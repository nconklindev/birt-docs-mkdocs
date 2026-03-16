---
title: Report Failures and Performance
description: How to troubleshoot common report failures and performance issues using Splash.
---

This article covers how to diagnose and investigate report failures and performance issues using [Splash](./using-splash.md). Before proceeding, generate a Splash dashboard from your report execution data.

## Failures

### Where to Start

The **Error Analysis** section of the dashboard is the starting point for all failure investigations.

1. Check the **Failure Rate** KPI card.
    - A rate above ~5% warrants investigation.
    - A rate above 20% indicates a significant problem.
2. Review **Failures by Engine** — is the failure rate disproportionately high on one engine? ADHOC failures are the most common case.
3. Review **Failures by Hour** — is there a time-based pattern? Overnight batches spiking or failures concentrated at a specific hour suggest resource or scheduler issues.
4. Review the **Error Code Distribution** — a single dominant error code points to a specific cause; mixed codes suggest multiple unrelated root causes.
5. Review **Most Failing Reports** — sort by failure _rate_, not failure _count_. A rate reveals true severity better than raw volume.
6. Check **Concurrent Load at Failure Time** — high concurrency at the time of failure is a key indicator of resource contention.

### ADHOC Timeouts

ADHOC timeouts are the most common cause of report failures. The ADHOC engine has a hard execution limit of approximately 15 minutes. Any report that exceeds this limit will be terminated.

**How to identify:**

- Failures are concentrated on the ADHOC engine.
- Run durations are near 15 minutes.
- Splash automatically applies a **TIMEOUT** badge (≥ 15 min) or **POSSIBLE TIMEOUT** badge (13–15 min) in the execution log.

**Root causes:**

- The report requests too much data to complete within the ADHOC limit.
- The Hyperfind pulls too many employees.
- The selected timeframe is too wide.

**How to investigate:**

1. Navigate to the failing report's detail view.
2. Read the **Observations** — Splash will often identify an ADHOC timeout pattern directly.
3. Open a failed execution in the **Execution Detail Panel** and check:
    - _Timeframe_ start and end dates.
    - _People IDs_ count (the size of the Hyperfind population).
    - The full error message for keywords like "SOAP" or "timeout".
4. If confirmed, the fix is to move the report to a scheduled engine (MEDIUM or LARGE) or reduce the data scope by narrowing the Hyperfind or timeframe.

### Drilling Into a Failing Report

1. Navigate to the report in the dashboard using the tenant → report selector.
2. Read the **Observations** section first.
3. In the **Execution Log**, filter to _Failures only_.
4. Click a failed execution to open the **Execution Detail Panel**, which shows:
    - Queue time and duration side-by-side.
    - Which engine was assigned and whether it matched the expected engine.
    - The full error message.
    - Whether a **TIMEOUT** badge applies.
    - Every other report running on the same engine at the same time across all tenants.

If the error code and message are the same across all failures, the cause is likely deterministic (a configuration problem or a report that is structurally too large). If the error varies, the cause is likely environmental (contention or an infrastructure event).

### Engine Mismatch Failures

A scheduled report that lands on the ADHOC engine will eventually hit the 15-minute hard limit.

1. Navigate to the **Engine Routing** section.
2. Check the **Mismatch Rate** — what percentage of runs landed on a different engine than expected?
3. For a suspected report, open its detail view and sort the **Execution Log** by the _Engine_ column to see whether the actual engine varies or is consistently wrong.

### Failure Clusters

A failure cluster is two or more failures that started within a configurable time window (default: 15 minutes). Use the **Failure Clusters** table in Error Analysis to identify systemic outage events.

**Interpreting a cluster:**

| Pattern | Likely Cause |
|---------|--------------|
| Many reports, many engines | System-wide event (infrastructure issue, batch scheduler firing simultaneously) |
| Many reports, one engine | That engine tier was saturated or unhealthy |
| 2–3 reports, same engine, same time | Resource contention between those specific reports |

To tighten the detection window, regenerate the dashboard with `--cluster-window 5`.

Cross-reference cluster timestamps against the **Failures by Hour** and **Avg Queue Time by Hour** charts to confirm whether system-wide pressure contributed.

### Failures on Specific Parameter Sets

If a report fails only for some parameter combinations but not others:

1. Open the report's detail view and scroll to the **Parameter Set Breakdown** table (requires `report_runtime_stat_id` or sufficient parameter data).
2. Look at the _Failure Rate_ column. A high rate for one parameter set but not others indicates the parameters are the issue.
3. Open the **Execution Detail Panel** for a failed run from that parameter set and check:
    - Is the error message consistent? (Same message = deterministic cause.)
    - Is the duration near 15 minutes on ADHOC? (Timeout from too much data.)
    - Is the Hyperfind larger or the timeframe wider than other parameter sets?

The **Repeatedly Failing Parameter Sets** table in the **Engine Routing** section surfaces the worst offenders across all reports without requiring individual drill-down.

---

## Performance

!!! warning

    Performance investigation is complex. Many factors influence report runtime and queue time, and analyses are
    only as good as the data provided. If you cannot draw clear conclusions from the dashboard, the contributing
    factor may be infrastructure-level and invisible in this data.

### Queue Time vs. Duration

Before investigating, always establish which problem you are looking at:

| Queue Time | Duration | Interpretation |
|------------|----------|----------------|
| Low | Low | Healthy run |
| Low | High | The report itself is expensive (data volume, complexity) |
| High | Low | Engine pool was saturated; the report ran fine once it got an engine |
| High | High | Both: system was busy and the report is expensive |

These are different problems with different solutions. Conflating them leads to incorrect diagnoses.

### Identifying Saturation Periods

The **Avg Queue Time by Hour** chart in the **Performance** section is the best starting point for understanding engine pool pressure.

Color coding:

- **Green** (< 1 min avg) — normal, reports picking up engines quickly
- **Orange** (1–5 min avg) — moderate pressure, pool is busy but not overwhelmed
- **Red** (> 5 min avg) — saturation, many reports are waiting significantly

1. Identify red or orange bars. Note the hours they correspond to.
2. Cross-reference those hours with the **Failures by Hour** chart in Error Analysis — elevated failures in the same window confirm resource pressure.
3. If elevated hours align with business hours (e.g., 8–10 AM), this is expected. If they align with overnight scheduled batches, investigate the batch scheduling configuration.

To confirm saturation is affecting a specific report, check the **Concurrent Load** chart in its detail view. Tall bars confirm the engine was busy during that report's execution window.

### Investigating a Slow Report

1. Navigate to the report's detail view.
2. Read the **Observations** section — Splash may already identify the pattern.
3. Review the **Duration Trend** chart:
    - Is this an isolated slow run or a recurring pattern?
    - Are slow runs also failures?
4. Review the **Queue Trend** chart:
    - Is queue time growing over time? Growing queue = increasing system load, not a change in the report itself.
5. Click the slowest execution in the **Execution Log** to open the **Execution Detail Panel** and check:
    - Queue time vs. duration side-by-side.
    - _Timeframe_ and _People IDs_ count.
    - Concurrent load on the same engine during that run.

For a report with a very long duration and a near-zero queue time, the report received an engine immediately — the slowness is intrinsic to the report's data volume or complexity, not contention from other reports.

### Slowest Reports Table

The **Slowest Reports** table shows the longest-running individual executions across all reports. For each entry:

- **Long duration + short queue** → the report itself is the bottleneck.
- **Long duration + long queue** → the report was delayed before starting and then ran slowly.
- **Short duration + long queue** → the report ran fine once it got an engine; the problem is congestion, not the report.

### Anomaly Detection

The **Anomalous Runs** table flags executions that are statistically slow relative to that report's own history (modified Z-score > 3.5, minimum 5 runs). Anomalies appear with a **SLOW** badge in the execution log.

!!! info

    Anomaly detection is scoped to the export window. A flagged run might look normal over a longer baseline.
    Use anomalies as starting points for investigation, not as verdicts.

For reports with anomalous runs, check:

1. Do slow runs cluster at a specific hour? (Check the **Hourly Run Pattern** chart.)
2. Do they correlate with a specific engine?
3. Does the **Concurrent Load** chart show elevated load during those slow runs?
4. Are slow runs associated with a larger Hyperfind population? (Check _People IDs_ in the execution detail panel.)

### Parameter Set Analysis

The **Parameter Set Breakdown** table in a report's detail view answers whether the report is consistently slow or only slow for specific parameter combinations. It is available when `report_runtime_stat_id` is present in the data.

**Reading the table:**

| Column | What to Look For |
|--------|-----------------|
| _Failure Rate_ | High for one set but not others → parameters are the issue |
| _CV%_ | Amber (≥ 25%) or red (≥ 50%) indicates unpredictable runtimes for that parameter set |
| _Trend_ | Amber (positive) = this parameter set is getting slower over time |
| _Avg / Min / Max_ | A wide spread between min and max indicates external factors (contention, resource availability) |
| _Hyperfind / Timeframe_ | Cross-reference: is this the largest population or widest timeframe? |

**Common patterns and their meaning:**

- **High CV% for one set, low for others** — an external factor (contention, engine availability) is hitting this combination specifically. Cross-reference with the **Avg Queue Time by Hour** chart for the hours this set runs.
- **High CV% across all sets** — the report is generally sensitive to engine load. Check the tenant-level queue-by-hour chart.
- **Positive trend (getting slower)** — the runtime for this parameter set is increasing over time. Possible causes: the Hyperfind is growing (more employees), the historical data window is expanding, or there was a recent environment change.

The **High-Variance Parameter Sets** and **Repeatedly Failing Parameter Sets** tables in the **Engine Routing** section surface the worst offenders across all reports without requiring individual drill-down — use these as a triage tool.

### Duration Trend Over Time

The **Duration Trend Over Time** chart shows per-day median and 95th-percentile (p95) duration for the top 5 most frequently run reports.

- **Median drifting upward** — the report is getting progressively slower (growing Hyperfind, expanding historical data, infrastructure degradation).
- **p95 spiking while median is flat** — most runs are fine, but occasional runs are much slower. Check concurrent load or parameter variation for those runs.
- **Sudden step change on a specific date** — a report configuration change or environment change occurred around that date.

### Long-Queued Completions

The **Long-Queued Completions** table shows reports with the highest queue time that ultimately completed successfully. These are useful because they show engine pool pressure without the noise of failures — pure wait time. A cluster of long-queued completions at a specific hour confirms saturation even when there are no failures.

### Engine Saturation Windows

If the dashboard was generated with `--engine-slots`, the **Engine Saturation Windows** table identifies specific hours where the engine pool reached or exceeded capacity.

```bash
splash data.csv --engine-slots ADHOC=10,MEDIUM=5,LARGE=3 -o report.html
```

Cross-reference saturated engine hours with the **Avg Queue Time by Hour** and **Failures by Hour** charts to confirm the impact on report execution.

### Possibly Hung Running Jobs

The **Possibly Hung Running Jobs** table lists executions in RUNNING status where the elapsed time exceeds 2× the report's median completed duration. These reports should have finished based on their history and are likely stuck. This is the only place in the dashboard where RUNNING rows appear — they are excluded from all other duration statistics.
