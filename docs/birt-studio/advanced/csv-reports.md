---
title: 'Adding CSV Format to Reports'
description: How to add CSV format to reports in BIRT Studio
---

## CSV Format

Reports in BIRT Studio can be updated to run in CSV format. CSV stands for "Comma-Separated Values" and is a text file
format that uses commas to separate values. Configuring a report to run in CSV format is useful if the data inside the
report needs to be exported to another system or application that requires CSV format. Getting a BIRT Studio report to
run in CSV format is a simple process that requires a few steps in and out of the report.

!!! warning

    A report run in CSV format will only return the **raw** data from the report. This means that formatted data and
    modified column headers will return as they do from the database. For example, if you format a date in your
    report from January 1, 2024 to 1/1/2024, when the report is run in CSV format, the date will return however it
    is stored in the database — in this case, January 1, 2024. This is just an example and may not reflect how
    dates are returned in all cases.

## Configuring the Report Design

### Setting the Table Name

The first thing that needs to be done to set up the report design for CSV format is to set a table name on the table
that is going to be exported. Select the entire table by selecting a single column, then clicking the table bar above
the column headers. The entire table will be selected when a blue border appears around it. Click the **Properties**
icon to open the Table Properties. A drawer will open on the right side. Fill in the top text box labeled _Table Name_.
Click **OK** when done.

!!! warning

    If a report design contains multiple tables, only one can be used in CSV format.

### Setting the CSV_EXPORT_TABLE_NAME Parameter

After the table is set, the next step is to set the `CSV_EXPORT_TABLE_NAME` parameter. To do this, click on **Data >
Manage Parameters** and click the **Edit** icon next to the `CSV_EXPORT_TABLE_NAME` parameter. A window will appear in
the middle of the screen. In the _Default Value_ text box, enter the table name that was set in the previous step. Click
**OK** when done.

### Setting the CSV_EXPORT_COLUMN_NAMES_ORDER Parameter

To set the `CSV_EXPORT_COLUMN_NAMES_ORDER` parameter, you should take note of the column _binding_ names that are set in
the Report Data Object. These are whatever value is in the _Label_ field for each column. The steps below assume all
default label names. Click on **Data > Manage Parameters** and click the **Edit** icon next to the
`CSV_EXPORT_COLUMN_NAMES_ORDER` parameter. A window will appear in the middle of the screen. In the _Default Value_ text
box, enter the names of the column bindings in the order you'd like them to appear in the CSV report, separated by a
semicolon. An example output may look like:

```
Employee Full Name;Employee ID;Actual Total Hours (Include Corrections);Actual Total Apply Date;Paycode Name
```

This is just an example, but your parameter should be formatted similarly when complete.

!!! info

    Computed columns can be used in the parameter as well, but make sure that you use the computed column's binding
    name and not the label name.

When you are done editing the _Default Value_, click **OK**. After setting the two parameters described in the two
previous steps, the report design is complete. If the report is unpublished, it can be published following the steps
from the [Publishing a Report](../introduction/getting-started.md#publishing-a-report) section.

!!! danger

    Do not edit the "Required" checkbox for either of the CSV parameters. This will cause the report to fail when
    run. It is disabled by default and should not be enabled.

## Configuring the Report Options

### Setting the Available Formats

On the Report Options page (after clicking "Edit" on the Published Report), select CSV from the _Output formats_ list.
This will check off the format and make it available when the report is run. If this is all you wanted to do and you do
not want to change the default format, you can click **Save** and the report will be ready to run in CSV format.

### (Optional) Setting the Default Format

To set the default format to CSV, select it from the _Default Output Type_ dropdown. Click **Save** to save your
changes.
