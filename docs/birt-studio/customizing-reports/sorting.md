---
title: 'Sorting'
description: How to sort data in a custom report in BIRT Studio.
---

## About Sorting Data

The data in a report can be sorted by any column and even multiple columns (up to 3). Read through this article for how to apply sorting to your report.

## Sorting on a Single Column

To sort on a single ungrouped column, select the column and either right-click and select _Sort > Sort Ascending_ or _Sort Descending_, or hover over the sort icon in the column header and select either _Sort Ascending_ or _Sort Descending_.

!!! info

    If there are no groups, only one column can be sorted at a time. See
    [Grouping Data](./grouping.md) for more information on how to create groups.

## Sorting on Multiple Columns

A lot of times, you will want to sort on multiple columns. To sort on multiple columns, you need to either:

-   Have a single or multiple grouped columns and at least one ungrouped column and apply the sort using the method
    described in [Sorting on a Single Column](#sorting-on-a-single-column)
-   Apply an Advanced Sort

Grouped columns are treated separately from ungrouped columns. This means that if you have a grouped column and an ungrouped column, you can sort on both of them. If you have multiple grouped columns, you can sort on all of them.

!!! info

    Multiple grouped columns can be sorted, but they will be sorted in the order that they were grouped. For example,
    if you have a Paycode Name and Employee Name group, and they appear in that order in the report, the sort applied
    to the Paycode Name takes precedence.

### Advanced Sort

An Advanced Sort allows you to sort on multiple columns, even if you have no grouped columns. To apply an Advanced Sort, right-click on a column and select _Sort > Advanced Sort_. This will open the Advanced Sort dialog.

!!! info

    The Advanced Sort dialog dropdown options will only show columns that are not grouped. If you have a grouped
    column, you will need to remove the grouping to sort on that column.

Start by selecting a _Sort By_ column and either _Ascending_ or _Descending_ order. To add multiple sorts, select one or more _Then By_ sorts.
