---
title: Creating Relative Time Period Reports
description: How to utilize the "Relative Time Period" RDO feature and create a report using this RDO type
---

## What is a Relative Time Period Report?

The Relative Time Period feature allows you to view and compare data across multiple time periods within a single report. You can configure the relative time period options when creating the Report Data Object. This feature allows users to:

-   View data for a time period relative to any symbolic date or date range within a report (e.g., view data for the 7 days before "Today").
-   Compare data across multiple time periods within a single report (e.g., compare current forecast week sales with last year's sales).

## Creating the RDO

1. Navigate to **Application Setup > Common Setup > Report Data Object Management**.
2. Click **Add** and select your desired type.
3. On the **Create Report Data Objects** page, enter the following:
    -   _Report Data Object Key_
    -   _Description_ (optional)
4. For the _Timeframe_ option, select _Relative Time Period_. Additional configuration fields will appear.

## Configuring the RDO

After selecting _Relative Time Period_, two new fields appear:

-   _Relative Time Period Start Date Reference_: The reference date relative to the start date of the selected timeframe.
-   _Relative Time Period End Date Reference_: The reference date relative to the end date of the selected timeframe.

1. For _Relative Time Period Start Date Reference_, select one of the following options:
    -   _Week to Date Reference_
    -   _Number of Days Before Selected Date_
    -   _Number of Days After Selected Date_
    -   _Number of Weeks Before Selected Date_
    -   _Number of Weeks After Selected Date_
2. Optionally, configure _Relative Time Period End Date Reference_ using the same options.
3. Enter the number of days or weeks to reference for each field you configured.
4. Add your desired columns to the RDO.
5. Click **Save**.

## Example

To create a report that shows employee hours for the last 7 days, configure the RDO as follows:

-   _Relative Time Period Start Date Reference_: _Number of Days Before Selected Date_ = 7.

Leave _Relative Time Period End Date Reference_ blank, as no end date constraint is needed.
