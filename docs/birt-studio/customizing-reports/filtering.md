---
title: 'Filtering'
description: 'How to apply filters to reports in BIRT Studio.'
---

## About Report Filtering

Sometimes the report you create needs only specific data to appear. This is where adding report filters comes in. In BIRT Studio, you have the ability to apply a filter to any column using a variety of conditions and even apply multiple conditions to a single column and multiple filters to a single report. For example, let's say you make a report that returns the hours worked by employee by paycode by date. It looks good but you'd like to only see a specific Pay Code or Pay Codes. That can easily be done by applying a filter to the Paycode column.

Applying filters to reports not only helps you get the data that you want but it also increases performance and can increase processing speed when run. Limiting the number of data rows that are returned to the report can help reduce the amount of time it takes to run the report.

## Filter Conditions

When applying a filter to a column, there are numerous conditions to choose from. The condition you apply will depend on what you are trying to do. The available conditions are listed in the table below.

| Condition | Description | Notes |
|-----------|-------------|-------|
| Between | Applies the filter to what is between two values | Typically used with numerical data but can be used for dates and times as well |
| Equal to | Applies the filter that is equal to what is set | |
| Greater than | Applies the filter that is greater than the specified value | |
| Greater than or Equal | Applies the filter that is greater than or equal to the specified value | |
| In | Applies the filter that is in the specified list | Enter values in the _Enter value(s)_ field and click _Add Value(s)_ when done |
| Is Not Null | Applies the filter that is not null | |
| Is Null | Applies the filter that is null | |
| Less than | Applies the filter that is less than the specified value | |
| Less than or Equal | Applies the filter that is less than or equal to the specified value | |
| Like | Applies the filter that is like the specified value | Use the wildcard character `%` |
| Match | Applies the filter that matches the value | |
| Not Between | Applies the filter that is not between the specified values | Typically used with numerical data but can be used for dates and times as well |
| Not Equal to | Applies the filter that is not equal to the specified value | |
| Not In | Applies the filter that is not in the specified list | Enter values in the _Enter value(s)_ field and click _Add Value(s)_ when done |
| Not Like | Applies the filter that is not like the specified value | Use the wildcard character `%` |
| Not Match | Applies the filter that does not match the specified value | |
| Is False | Applies the filter for when the value is false | |
| Is True | Applies the filter for when the value is true | |
| Top Percent | Applies the filter for the specified top percent | Can be filtered on the entire table, or a specific group |
| Top n | Applies the filter for the top number of items specified (n) | Can be filtered on the entire table, or a specific group |
| Bottom Percent | Applies the filter for the specified bottom percent | Can be filtered on the entire table, or a specific group |
| Bottom n | Applies the filter for the bottom number of items specified (n) | Can be filtered on the entire table, or a specific group |

When applying any of the above conditions, there are three options to pick from:

-   Specify literal value
-   Use value from data field
-   Link to parameter

The _Link to parameter_ option is covered in a different article. See [Custom Report Parameters](../advanced/custom-report-parameters.md) for more information.

**Specify literal value** — This option allows you to specify a value that will be used in the filter. For example, if you want to filter the Pay Code column to only show the value of **REG**, you would select this option and then type **REG** in the text box.

**Use value from data field** — This option allows you to compare the data from each row with the value from a specified data field.

!!! warning

    The _Use value from data field_ option may not work for all conditions or columns. If an error is encountered
    after trying to apply a filter using this option, try using the _Specify literal value_ option instead.

## Adding Filters to a Report

To add a filter to a report, start by clicking a column header to select it. You will know it is selected when the column has a dark blue border around the entire column. Once selected, the **Filter** icon will appear in the table toolbar above the report. Click it to begin adding a filter and open the **Filter** window.

Click the **Advanced Filter** link to be taken to the **Advanced Filter** window. This window allows you to apply multiple filters to a single column. See [Multiple Filters](#multiple-filters) for more information.

### Single Filter

To add a single filter to the report, select your _Filter By_ column in the **Advanced Filter** window and your desired _Condition_ from above. If using _Specify literal value_, enter the condition into the _Default value_ field. If using _Use value from data field_, select the data field from the _Data field_ dropdown. Click the _Add Condition_ link to add the condition, then the _Add Filter_ link to add the filter to the report. Click **OK** when done making changes to add the filter.

!!! warning

    After saving changes to your filter, the report may update and display no data with a dialog box that states "The
    sample data does not meet the filter conditions. To design the report, increase max rows setting or remove the
    filters. Then recreate filters or move filters on data set before publishing the report design". If the filter you
    applied is correct, then this can be ignored. The default timeframe when designing a report is Today–Today with a
    Hyperfind of All Home Locations. If you are sure that there should be data showing in view, then preview the
    report by clicking the **Preview** icon in the navigation menu at the top of the window.

!!! info

    When using _Use value from data field_, depending on the condition you select, you may have additional options to
    choose from. For example, if you select _Between_, you will have two additional fields to enter values into.

### Multiple Filters

Multiple filters on one column can also be applied through one condition. To apply two or more filters as a condition, perform the steps to apply the first filter and click the _Add Condition_ link.

Before clicking _Add Filter_, select the same or another column from the _Filter By_ dropdown and select a _Condition_ from the dropdown. Enter the literal value or use values from data fields and click _Add Condition_.

By default, the _Conditions_ text area will display the two conditions together, joined with an **AND**. This follows standard computer logic where _both_ conditions must be met for the filter to be applied. If you want to change the logic to an **OR**, click the **OR** button on the right side. Click _Add Filter_ and **OK** to finalize the changes.

For example, using `1` as `true` and `0` as `false`:

`1 && 1 = true`

`1 && 0 = false`
