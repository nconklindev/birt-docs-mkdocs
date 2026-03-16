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

!!! warning

    If a report design contains multiple tables, only one can be used in CSV format.

1. Select a single column in the table, then click the table bar above the column headers to select the entire table. A blue border will appear around the table when it is selected.
2. Click the **Properties** icon to open the Table Properties. A drawer will open on the right side.
3. Fill in the _Table Name_ field at the top of the drawer.
4. Click **OK**.

### Setting the CSV_EXPORT_TABLE_NAME Parameter

1. Click **Data > Manage Parameters**.
2. Click the **Edit** icon next to the `CSV_EXPORT_TABLE_NAME` parameter.
3. In the _Default Value_ text box, enter the table name set in the previous step.
4. Click **OK**.

### Setting the CSV_EXPORT_COLUMN_NAMES_ORDER Parameter

Before setting this parameter, note the column binding names from your Report Data Object. These are the values in the _Label_ field for each column.

1. Click **Data > Manage Parameters**.
2. Click the **Edit** icon next to the `CSV_EXPORT_COLUMN_NAMES_ORDER` parameter.
3. In the _Default Value_ text box, enter the column binding names in the desired display order, separated by semicolons. For example:

    ```
    Employee Full Name;Employee ID;Actual Total Hours (Include Corrections);Actual Total Apply Date;Paycode Name
    ```

4. Click **OK**.

!!! info

    Computed columns can be used in the parameter as well, but make sure that you use the computed column's binding
    name and not the label name.

After setting both parameters, the report design is complete. If the report is unpublished, publish it following the steps in the [Publishing a Report](../introduction/getting-started.md#publishing-a-report) section.

!!! danger

    Do not edit the "Required" checkbox for either of the CSV parameters. This will cause the report to fail when
    run. It is disabled by default and should not be enabled.

## Configuring the Report Options

### Setting the Available Formats

1. Click **Edit** on the Published Report to open the **Report Options** page.
2. Select _CSV_ from the _Output formats_ list to enable it.
3. Click **Save**.

### (Optional) Setting the Default Format

1. From the _Default Output Type_ dropdown, select _CSV_.
2. Click **Save**.
