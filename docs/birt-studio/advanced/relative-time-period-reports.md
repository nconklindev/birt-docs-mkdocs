---
title: Creating Relative Time Period Reports
description: How to utilize the "Relative Time Period" RDO feature and create a report using this RDO type
---

## What is a Relative Time Period Report?

The Relative Time Period feature allows you to view and compare data across multiple time periods within a single report. You can configure the relative time period options when creating the Report Data Object. This feature allows users to:

-   View data for a time period relative to any symbolic date or date range within a report (e.g., view data for the 7 days before "Today").
-   Compare data across multiple time periods within a single report (e.g., compare current forecast week sales with last year's sales).

## Creating the RDO

Creating a Relative Time Period RDO starts the same way as any other. Navigate to **Application Setup > Common Setup > Report Data Object Management** to start. Click the **Add** button and select your desired type.

On the **Create Report Data Objects** page, enter the following details:

-   _Report Data Object Key_
-   _Description_ (optional)

For the _Timeframe_ option, select _Relative Time Period_. Selecting this option will display additional fields for configuration.

## Configuring the RDO

After selecting the _Relative Time Period_ option, the following fields will be displayed for configuration:

-   _Relative Time Period Start Date Reference_: The reference date relative to the start date of the selected timeframe.
-   _Relative Time Period End Date Reference_: The reference date relative to the end date of the selected timeframe.

The following options are available for both reference fields:

-   _Week to Date Reference_
-   _Number of Days Before Selected Date_
-   _Number of Days After Selected Date_
-   _Number of Weeks Before Selected Date_
-   _Number of Weeks After Selected Date_

After selecting one of these options for the _Relative Time Period Start Date Reference_ and/or the _Relative Time Period End Date Reference_ fields, you can enter the number of days or weeks to reference.

Once you have configured the RDO and added your desired columns, click **Save** to save the RDO.

## Example

Let's say you want to create a report that shows employee hours for the last 7 days. You would configure the RDO as follows:

-   _Relative Time Period Start Date Reference_: Number of Days Before Selected Date = 7.

You would leave the _Relative Time Period End Date Reference_ blank, as you want to show the data for the last 7 days and in this case do not need to constrain the end date.
