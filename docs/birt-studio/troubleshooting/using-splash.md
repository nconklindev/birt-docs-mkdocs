---
title: Using Splash
description: How to install and use Splash to analyze BIRT report execution data.
---

Splash is a Python CLI tool that transforms CSV exports of BIRT report execution data into a self-contained, interactive HTML dashboard. It is the primary tool used to diagnose why reports are failing, running slowly, or experiencing resource contention.

No server, login, or runtime dependency is needed to view the output — Splash generates a single HTML file you can open in any browser.

## Installing Splash

**Recommended (via uv):**

```bash
uv tool install git+https://github.com/nconklindev/splash
```

**Via pip (from a cloned repo):**

```bash
git clone https://github.com/nconklindev/splash
pip install .
```

**Via wheel (from a GitHub release):**

```bash
pip install splash-<VERSION>.whl
```

## Getting the Data

Splash requires a CSV export of BIRT report execution history from Splunk or PostgreSQL. Each row in the CSV represents one report execution.

**Required columns:**

| Column | Description |
|--------|-------------|
| `report_name` | Name of the report |
| `report_execution_status_id` | Execution status (1=Running, 2=Completed, 3=Failed, 5=Suspended) |

**Recommended columns** (the dashboard adapts to what is present):

| Column | Description |
|--------|-------------|
| `id` | Unique execution ID — enables deduplication when combining multiple CSV files |
| `schema_name` | Tenant identifier — enables multi-tenant drill-down |
| `start_datetime` / `end_datetime` | Execution timestamps — required for timing and queue analysis |
| `birt_report_starttime` / `birt_report_endtime` | BIRT engine start/end — required to compute queue time |
| `actual_engine` / `expected_engine` | Engine assignment — required for routing and mismatch analysis |
| `error_code` / `error_message` / `error_stack` | Error details — required for failure analysis |
| `parameters` | JSON string of run parameters — enables hyperfind/timeframe extraction |
| `report_runtime_stat_id` | Groups executions by parameter set — enables Parameter Set Analysis |
| `output_file_size` / `report_object_count` | Output size metrics — used in performance correlation analysis |

## Basic Usage

```bash
# Generate a dashboard from a single file and open it immediately
splash report_history.csv -o dashboard.html --open

# Combine multiple exports
splash jan.csv feb.csv mar.csv --title "Q1 Analysis" -o q1.html
```

## Common Options

| Option | Description |
|--------|-------------|
| `-o, --output PATH` | Output file name (default: `splash_report.html`) |
| `--title TEXT` | Dashboard title |
| `--start-date YYYY-MM-DD` | Include only rows on or after this date |
| `--end-date YYYY-MM-DD` | Include only rows on or before this date |
| `--open` | Open the dashboard in a browser after generation |
| `--threshold SECONDS` | Flag any report that ran longer than this duration |
| `--engine-slots ENGINE=N[,...]` | Define engine pool sizes for saturation detection (e.g., `ADHOC=10,MEDIUM=5`) |
| `--cluster-window N` | Minutes window for failure cluster detection (default: 15) |
| `--compare FILE` | Add a second period's CSV for side-by-side comparison |
| `--compare-title-a TEXT` | Label for the baseline period (default: "Period A") |
| `--compare-title-b TEXT` | Label for the comparison period (default: "Period B") |
| `-q, --quiet` | Suppress informational output |

## Dashboard Overview

The dashboard is organized into the following sections:

- **Report Inventory** — unique reports, frequency, scheduling regularity, parameter variations
- **Timing & Scheduling** — duration distribution, hourly/weekly run patterns, overlapping runs
- **Error Analysis** — failure rates, failure clusters, error codes, concurrent load at failure time
- **Engine Routing** — load distribution, engine mismatches, saturation windows
- **Performance** — slowest reports, queue time by hour and engine, anomaly detection, duration trends
- **Comparison** (when `--compare` is used) — side-by-side KPI comparison and per-report delta table

### Navigation Pattern

The recommended drill-down path is:

**Stack view** (all tenants) → **Tenant view** (one tenant) → **Report view** (one report) → **Execution detail panel** (one run)

The **Report view** is the most valuable level for diagnosis. It includes pre-written **Observations** that Splash computes automatically — always read these first before diving into charts.

## Key Concepts

**Queue time vs. duration**
Queue time is how long the report waited before a BIRT engine picked it up (`birt_report_starttime - start_datetime`). Duration is the total execution time (`end_datetime - start_datetime`). These represent different problems with different causes — always check both separately.

**ADHOC engine timeout**
ADHOC is the on-demand engine with a hard ~15-minute execution limit. Splash automatically badges runs that hit this limit:

- **TIMEOUT** — duration ≥ 15 minutes on ADHOC (almost certainly timed out)
- **POSSIBLE TIMEOUT** — duration 13–15 minutes on ADHOC (worth investigating)

**Failure clusters**
Two or more failures starting within a configurable time window (default: 15 minutes). A cluster of 5+ failures is almost never coincidental — it typically indicates a systemic event such as an infrastructure outage or engine saturation.

**Anomaly detection**
Splash flags runs that are statistically slow relative to that report's own history using a modified Z-score (threshold: 3.5, minimum 5 runs required). Anomalies are relative to the export window, not long-term history.

**CV% (Coefficient of Variation)**
A measure of consistency. Lower is more predictable. Thresholds: amber ≥ 25%, red ≥ 50%.

**Parameter sets**
Groups of executions sharing the same parameters. Scheduled reports are grouped by `report_runtime_stat_id`. ADHOC runs are grouped by matching employee/org ID lists and timeframe. Parameter Set Analysis answers: is the report inconsistent overall, or only for specific parameter combinations?
