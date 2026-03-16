---
title: CSV Format
description: How to troubleshoot common issues that go wrong with creating and running CSV reports.
---

## CSV Format Fails

If a CSV report is failing, it can happen for a few reasons:

-   The value for the `CSV_EXPORT_TABLE_NAME` or `CSV_EXPORT_COLUMN_NAMES_ORDER` parameter is incorrect.
-   There is a misspelling or incorrect column binding name entered into the `CSV_EXPORT_COLUMN_NAMES_ORDER` parameter.

In either case, go back into the report design and make sure that the values for the parameters are correct. For the table name, make sure it matches what is set in the **Properties** of the table. For the column names, make sure that nothing is misspelled and that the column binding names are correct. Remember that the column binding names are whatever is set in the _Label_ field for each column in the Report Data Object.

!!! warning

    If the report completes successfully in CSV format but there is an issue with the data, then the problem is not
    with the CSV parameters or the CSV format itself. The issue could be in the report design or with the data. If
    you are unsure of where the issue is coming from, open a case with Support.

## Provided Columns Are Not Exporting

If a CSV report is running but is not exporting the columns that you have configured in the `CSV_EXPORT_COLUMN_NAMES_ORDER` parameter, try the following steps:

1. Verify that the column names are typed correctly.
    - For standard columns from the Report Data Object (RDO), this is the column _Label_ configured for the column in the RDO.
    - For computed columns, this is the name that was set when the column was created.
2. Edit the Report Options and remove CSV as an available format, then save.
3. Run a test report for any format with a short timeframe and a small Hyperfind that has data (this should complete successfully).
4. Edit the report design again and verify all columns are in the `CSV_EXPORT_COLUMN_NAMES_ORDER` parameter.
5. If everything looks correct, save any changes, then edit the Report Options, add CSV as an available format again, and save.
6. Test the report in CSV format.
