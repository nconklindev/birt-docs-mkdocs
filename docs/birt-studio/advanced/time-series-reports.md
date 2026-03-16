---
title: Creating Time Series Reports
description: How to create time series reports in BIRT Studio.
---

## What Are Time Series Reports?

Time Series reports allow managers to create reports that summarize Analytics data over a period of time. This can be
useful for tracking trends, identifying patterns, and making predictions based on historical data. Data can be
summarized by day, week, month, or quarter. Time Series reports are supported for both employee-based and business
structure-based reports.

!!! info

    The only entity that can be used to provide data for a Time Series report is the Analytics entity. It can be
    used with Employee Details and Employee Skill Assignment, but no other entities will appear when adding columns.

## Creating a Time Series Report

### Creating the Report Data Object

Creating a Time Series RDO starts the same way as any other. Navigate to **Application Setup > Common Setup > Report
Data Object Management** to start. Click the **Add** button and select your desired type, either _Employee - Time
Series_ or _Business Structure - Time Series_.

!!! warning

    Work Unit/HCA reports are beyond the scope of what is provided in this article. They are a little more
    complicated than an employee or business structure time series report. For more information on creating HCA
    reports, please see [Creating HCA Reports](./hca-reports.md).

The only difference in the newly opened page compared to a standard RDO is that a Time Series RDO contains two
additional dropdowns: _Time Increment_ and _Time Increment Format_. Both are required and default to _Calendar Day_
and _Day of Week_.

Each Time Increment has different available format options.

**Calendar Day**

- _Date_
- _Day of Week_
- _Day of Week + Date_ (e.g., Wednesday 12/04/2024)

**Calendar Month**

- _Date Range_
- _Month + Date Range_
- _Month Name_
- _Month Short Name_

**Calendar Quarter**

- _Date Range_
- _Quarter Number_
- _Quarter Number + Date Range_
- _Quarter Short Number_
- _Quarter Short Number + Date Range_

**Calendar Week**

- _Date Range_
- _Week Number_
- _Week Number + Date Range_

### Creating the Report

To create the report that uses the newly created Time Series RDO, the steps are the same as for other custom reports. If
you need those steps, please see the [Getting Started](../introduction/getting-started.md#creating-a-report-design) guide.
