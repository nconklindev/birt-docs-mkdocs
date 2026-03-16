---
title: 'Aggregating'
description: 'How to apply aggregations in custom reports.'
---

## Aggregating Data

In any good report, you may want to display summary, or aggregate, data. Aggregating data involves performing a calculation on a set of values and returning a single value. For example, you may want to calculate the total number of hours worked by all employees in a department. In this case, you would add up all the hours worked by each employee and return a single value.

In BIRT Studio, reports can be aggregated at the table and group level. For example, you could group by Employee Full Name and Paycode Name, then aggregate on each group, but also the table. This would provide you with the total hours worked by each employee, as well as the total hours worked by each employee for each paycode. And at the table level, it would give you the total hours worked by all employees.

## How To Aggregate Data

To open the **Aggregation** window:

1. Select the column to aggregate.
2. Click the **Aggregation (Σ)** icon in the table toolbar.

Alternatively, right-click the column and select **Aggregation**.

!!! info

    The following sections reference terms from the [User Interface](../introduction/user-interface.md) and
    [Terminology](../introduction/terminology.md) articles. If you are unfamiliar with these terms, please review
    those before continuing.

### Applying Aggregations by Group in Design View

Aggregating by group assumes that you have an existing group to aggregate on. If you do not know how to create a group, please see the [Grouping Data](./grouping.md) article.

To aggregate by group in design view:

1. Open the **Aggregation** window.
2. Check the _group_ option in the _Aggregate on_ section (enabled by default).
3. Select whether to place the aggregation in the _header_ or _footer_ of the group.
4. Select a function from the _Select Function_ dropdown.
5. Optionally, enter a _Label_ to prefix the aggregation value.
6. Click **OK** to save.

### Applying Aggregations by Group in Preview View

Aggregating by group in preview view has additional options not present in design view. However, there are some things to note when applying aggregations in preview view.

-   In order to edit in preview view, the report must be under 200 pages.
-   Changes applied in preview view must be saved in preview view, and the entire unpublished report reloaded to see the changes.
-   Aggregations in preview view are bolded by default (this can be changed in design view later).
-   The group aggregated on can be selected in preview view, whereas in design view the aggregation applies to every group and cannot be selected.
-   Aggregations at the group level in preview view apply their own "aggregation row" in either the header or footer of the group. **This behavior cannot be changed**.
-   Aggregations made in preview view cannot be removed from design view. They must be removed in preview view.

To aggregate by group in preview view:

1. Right-click the column header and select **Aggregation**, or click the three-dots menu and select **Aggregation**. The **Aggregation** window opens.
2. Select the group level from the dropdown. The dropdown lists the column key of every group in the report.
3. Select whether to place the aggregation in the _header_ or _footer_.
4. Optionally, enter a _Label_.
5. Click **OK** to save.

### By Table

Aggregating at the table level is the same in either design or preview view.

1. In the **Aggregation** window, check the _table level_ option (enabled by default).
2. Click **OK** to save.

## Adding Multiple Aggregations

To add multiple aggregations to the same column, click **Add Aggregation** at the bottom of the **Aggregation** window. Each aggregation can target a different group or the table level, and be placed in the header or footer. If adding multiple aggregations with different functions, add a _Label_ to each to differentiate them.

!!! warning

    Be aware of how many aggregations are being added to the report design. When processing the report, each
    aggregation will be calculated. If there are a large number of aggregations, this can slow down the report
    processing time.

## Removing Aggregations

To remove an aggregation, open the **Aggregation** window and click **Delete Aggregation**. If multiple aggregations are applied to the same column, only the selected one is removed.
