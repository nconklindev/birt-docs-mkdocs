---
title: Report Cookbook
description: Basic recipes for creating specific types of reports
---

## What Is This?

This page should be treated as a way to generate ideas for your next report. This page is not meant to be a
comprehensive walkthrough of how to create specific reports within BIRT Studio. Instead, it shows different patterns to
creating different kinds of reports and includes certain entities and columns that can be used together to achieve a
desired result.

The recipes provided here are only a getting started point and can, of course, be modified to whatever is needed. None
of
the recipes below will be for reports that require specific computed columns, complex filters, groups, or aggregations.
If you need help with a specific report, please open a case with Support.

## Hours by XXX

### Report Description

The "Hours by XXX" report is a very common reporting recipe. It can be made to report on hours by Paycode, Labor
Category, Cost Center, Location, etc.

### Report Type

Employee

### Report Data Object

**Entities**

- Employee Details
- Actual Total Hours (Include Corrections)
- Paycode
- Worked Job
- Labor Category

**Columns**

- Employee Full Name
- Employee ID
- Paycode Name
- Actual Total Hours
    - Assignment: Employee, Pay Code, Date
- Actual Total Wages
    - Assignment: Same as what is selected for "Hours"
- Location Name (Worked)
    - Assignment: As needed
- Labor Category Level x Entry Name
    - `x` is the desired level to return from **Labor Categories**
- Cost Center Name

## Custom Time Detail

### Report Description

The Standard Time Detail report can be duplicated and modified as needed, but the same columns used in this report can
also be used in a custom report of your own making. This type of report can vary in its design due to the number of
Transaction Types that can be returned.

### Report Type

Employee

### Report Data Object

**Entities**

- Employee Details
- Timecard Transactions
- Paycode
- Worked Job
- Labor Category

**Columns**

- Employee Full Name
- Employee ID
- Paycode Name
- Start Datetime
- End Datetime
- Transaction Type
    - Assignment: As needed
- Actual Hours
- Actual Wages
- Apply Date
- Location Name (Worked)
    - Assignment: As needed
- Job Name (Worked)
- Cost Center Name
- Labor Category Level x Entry Name
    - `x` is the desired level to return from **Labor Categories**

#### Note on Columns

There are two **Paycode Name** columns in the Data Dictionary. One is from the entity **Paycode** and the other is from
the entity **Timecard Transactions**. You will pick one of these, depending on the Transaction Type selected.

There are multiple Transaction Types that are
available. Each one returns something different.

## Timecard Audit

### Report Description

This type of report is similar to the **0-ST Time Audit** Dataview and can be used as a good basis for this report.
However, let's go over what you could include in this type of report.

!!! info

    Since an Audit report can include _a lot_ of columns, we only included the minimum columns that you need in order to
    understand all the data being returned. Review the columns from the Audit entity for more ideas on what else can be
    added.

### Report Type

Employee

### Report Data Object

**Entities**

- Audit
- Employee Details

**Columns**

- Employee Full Name
- Employee ID
- Audit ID
- Entity Type
- Revision Type
- Datasource
- Paycode Name
- Entity Event Date
- Revision Date
- Duration (Hours)
- Revision User

## Clock Audit

### Report Description

Similar to the Timecard Audit report, this Clock Audit report will provide an audit of all punches on UDM/clock devices.
We apply filters on the Entity Type, Revision Type, and Datasource columns.

### Report Type

Employee

### Report Data Object

**Entities**

- Audit
- Employee Details

**Columns**

- Employee Full Name
- Employee ID
- Audit ID
- Entity Type
- Revision Type
- Datasource
- Entity Event Date

**Filters**

- Entity Type _Equal To_ **Punch**
- Revision Type _Equal To_ **Add**
- Datasource _Starts With_ **UDM**