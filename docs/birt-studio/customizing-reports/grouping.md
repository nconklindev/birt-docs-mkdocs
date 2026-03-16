---
title: 'Grouping'
description: 'How to apply grouping and add sections to reports in BIRT Studio.'
---

## Benefits of Grouping Data

Sorting data is only one way to organize data in a report. But, in report development, it is common to present data that
is organized into meaningful groups, especially reports with a large number of columns. With groups, you can:

- Add [Aggregations](./aggregating.md) to summarize data within each group.
- Insert page breaks before or after each group to start each group of data on a new page.
- Hide the details of each group to view a summary report — see
  [Creating Summary Tables](../advanced/summary-tables.md).

Upon creating a group, BIRT Studio performs the following:

- Removes duplicate values
- Sorts the values of each group (though this can be changed — see [Sorting Data](./sorting.md))

## How to Create a Group

To create a group:

1. Select a column.
2. Click the **Add Group** icon in the table toolbar, or right-click the column and select **Group > Add Group**.

Repeat for any additional columns to group on.

To remove a group:

1. Select the grouped column.
2. Click the **Delete Group** icon in the table toolbar (same position as **Add Group**, with an "X" in the bottom right corner), or right-click the group header and select **Group > Delete Group**.

!!! warning

    The first two groups created will have a light grey background color applied to the entire group row. After the
    second group, this formatting stops being applied and the group row is harder to distinguish from the other data
    rows. This is normal and cannot be changed. It is generally recommended to keep the number of groups at two, or
    use manual formatting for anything beyond two.

### Grouping on Date and Time Columns

When grouping on date and time columns, BIRT Studio will present two options:

- Group using individual values
- Group every X time units

Grouping using individual values will group the data by the individual values in the column. For example, if you have a
datetime column that has the value Dec 22, 2023 7:30 AM, then the group will be Dec 22, 2023 7:30 AM. This is not
usually the most useful, and you will more often than not want to group using the second option.

Grouping every X time units will group the data by the time unit you select. For example, using the same values as
above, then the group will be Dec 22, 2023. This is much more useful in most cases.

The values that are available for the time units are:

- Years
- Quarters
- Months
- Weeks
- Days
- Hours
- Minutes
- Seconds

## Changing the Order of Groups

To reorder groups:

1. Select the table or any column, right-click, and select **Column > Reorder Columns**.
2. In the _Grouped Columns_ section, use the up and down arrows to reorder.

!!! info

    This window also allows you to reorder the columns in the table. This is useful if you want to change the order of
    the columns in the table but don't want to delete and re-add them. Reordering columns is also discussed in
    [Editing and Formatting](./editing-and-formatting.md#changing-the-order-of-columns).

## Creating Sections

A section is functionally equivalent to a group. When you create a section, you are also grouping data. Similar to
groups, you can create multiple sections, calculate aggregate data for each section, start each section on a new page,
and hide the details of each section.

However, one of the differences between a section and a group is how the information is arranged. See the below images
for an example of a group and a section.

!!! info

    For other examples of how sections can be used, review some of the existing Timekeeping reports in the Report
    Library such as the **Time Detail** report and the **Condensed Employee Time Detail** report. Other reports in the
    Report Library also use sections, but these are good examples of the types of data that work well with sections
    since these two reports were created by UKG.

To create a section:

1. Select the columns to add as a section by clicking the first column and <kbd>Ctrl</kbd>-clicking any others.
2. Right-click and select **Group > Add Section**.

!!! info

    For most report designs built using BIRT Studio, sections are not typically needed. You can create very nice and
    simple reports without sections by using groups instead.

## Hiding Details

Hiding details is useful to create things like [summary tables](../advanced/summary-tables.md).

!!! info

    Hiding details requires at least one group to be present before the option is visible.

To hide details:

1. Select the grouped column.
2. Right-click and select **Group > Hide Detail**.

### Showing Details

To show previously hidden details:

1. Select the grouped column.
2. Right-click and select **Group > Show Detail**.

If there are multiple groupings applied, the details must be shown from the deepest group first.
