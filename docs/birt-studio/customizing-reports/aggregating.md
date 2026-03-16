---
title: 'Aggregating'
description: 'How to apply aggregations in custom reports.'
---

## Aggregating Data

In any good report, you may want to display summary, or aggregate, data. Aggregating data involves performing a calculation on a set of values and returning a single value. For example, you may want to calculate the total number of hours worked by all employees in a department. In this case, you would add up all the hours worked by each employee and return a single value.

In BIRT Studio, reports can be aggregated at the table and group level. For example, you could group by Employee Full Name and Paycode Name, then aggregate on each group, but also the table. This would provide you with the total hours worked by each employee, as well as the total hours worked by each employee for each paycode. And at the table level, it would give you the total hours worked by all employees.

## How To Aggregate Data

To aggregate data in a report, first select the desired column that will be aggregated. In the table bar, click the **Aggregation (Σ)** icon. This will open the Aggregation Editor. Alternatively, you can right-click the column and select _Aggregation_.

The following sections review terms discussed in the [User Interface](../introduction/user-interface.md) and [Terminology](../introduction/terminology.md) articles. If you are unfamiliar with these terms, please review those before continuing.

### Applying Aggregations by Group in Design View

Aggregating by group assumes that you have an existing group to aggregate on. If you do not know how to create a group, please see the [Grouping Data](./grouping.md) article.

To aggregate by group, while in design view and with the Aggregation Window open, check the _group_ option in the _Aggregate on_ section (enabled by default). Then select whether you want to place the aggregation in the header or footer of the group. Select a function to use for the aggregation in the _Select Function_ dropdown. An optional _Label_ can be entered that will prefix the aggregation. Click **OK** when done to save the aggregation.

### Applying Aggregations by Group in Preview View

Aggregating by group in preview view has additional options not present in design view. However, there are some things to note when applying aggregations in preview view.

-   In order to edit in preview view, the report must be under 200 pages.
-   Changes applied in preview view must be saved in preview view, and the entire unpublished report reloaded to see the changes.
-   Aggregations in preview view are bolded by default (this can be changed in design view later).
-   The group aggregated on can be selected in preview view, whereas in design view the aggregation applies to every group and cannot be selected.
-   Aggregations at the group level in preview view apply their own "aggregation row" in either the header or footer of the group. **This behavior cannot be changed**.
-   Aggregations made in preview view cannot be removed from design view. They must be removed in preview view.

To aggregate by group while in preview view, right-click on the column header and select _Aggregation_. Alternatively, with a column selected, you can click the three-dots menu and select _Aggregation_. Either will open the Aggregation Window, which will look slightly different than in design view.

You'll notice that this window allows you to select the group level with a dropdown. The dropdown provides the column key of every group in the report.

From this dropdown, select the group you want to aggregate on and whether you would like the aggregation to appear in the header or footer. As mentioned above, aggregations in preview view will add their own row to the report. If header is selected, the aggregation will appear just under the group header. If footer is selected, the aggregation will appear just before the next group header. An optional _Label_ can be entered. Click **OK** when done to save the aggregation.

### By Table

Aggregating at the table level is the same in either design or preview view. From the aggregation window, check the _table level_ option (enabled by default). Click **OK** when done to save the aggregation.

## Adding Multiple Aggregations

To add multiple aggregations, click the _Add Aggregation_ link at the bottom of the Aggregation window. This will add another aggregation on the same selected column. You can add as many aggregations as you want. Each aggregation can be applied to a different group or the table. Each aggregation can also be placed in the header or footer of the group. If adding multiple aggregations with different functions, it may be a good idea to add a label to differentiate what each aggregation represents.

!!! warning

    Be aware of how many aggregations are being added to the report design. When processing the report, each
    aggregation will be calculated. If there are a large number of aggregations, this can slow down the report
    processing time.

## Removing Aggregations

If you need to remove an existing aggregation, open the Aggregation window and click the _Delete Aggregation_ link. This will remove that specific aggregation from the report. If multiple aggregations on the same column are applied, the others will not be removed.
