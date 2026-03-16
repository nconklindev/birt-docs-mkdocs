---
title: 'Creating Summary Tables'
description: How to create summary tables using grouping and aggregations in BIRT Studio.
---

## Introduction

Summary tables are built like any other table you'd add to a report. Most of the time, you will even end up using the same Report Data Object that you used to build the report. The difference between a normal table and a summary table is that a summary table uses a combination of groupings, aggregations, and hiding of details to create a summary of the data. If you are unfamiliar with any of these concepts or need a refresher, please review [Grouping](../customizing-reports/grouping.md), [Aggregating](../customizing-reports/aggregating.md), and [Filtering](../customizing-reports/filtering.md).

## Creating a Summary Table

At a basic level, creating a summary table involves three steps: adding the columns you need, grouping by the column you want summarized, creating an aggregation on the metric column, and hiding the group details.

### Adding Columns

1. Click **Insert > Table > Table** from the menu bar. The **Table Builder** window opens.
2. Select the columns you want and move them over by clicking the right **Add** arrow button. Use <kbd>Ctrl</kbd>+<kbd>Click</kbd> to select multiple columns at once.
3. Click **OK** to add the table to the report design.

If there is an existing table, the new table will be added above it.

!!! info

    It is not required, but as a best practice, if the RDO is an employee-based RDO, at least one column from the
    _Employee Details_ entity should be included, such as _Employee Full Name_ or _Employee ID_. This will
    help with troubleshooting in the future if needed.

For more information on adding columns to a report design, please see [Getting Started](../introduction/getting-started.md#adding-columns-to-the-report).

### Grouping

1. Select the column you want to summarize (e.g., _Paycode Name_).
2. Click the **Add Group** icon.

For more information on creating groups and grouping data, please see [Grouping](../customizing-reports/grouping.md).

### Aggregating

1. Select the column to aggregate (e.g., _Hours_).
2. Click the **Aggregation (Σ)** icon. The **Aggregation Builder** window opens.
3. Select the aggregation type you want to use (e.g., _Sum_).
4. Set the aggregation to apply on the _Group_ and in the _header_.
5. Click **OK**.

For more information on creating aggregations, see the [Aggregating](../customizing-reports/aggregating.md) page.

### Hiding Details

The "detail" rows are the white rows (by default) that are not part of the group header. To hide them:

1. Right-click on the grouped column.
2. Select **Group > Hide Details** from the context menu.

Only the group header rows will now be visible.

Hiding Details is covered in the [Grouping](../customizing-reports/grouping.md#hiding-details) article.

## Other Considerations

Here are some other considerations for your next summary table:

-   The summary table can be expanded to include more groups and aggregated data.
-   Grouping by 1–2 columns is most readable in a summary table.
-   You can change the background color of the group header row to make it stand out from detail rows.
-   Try changing the font, font size, and font color.
-   When aggregating the data, don't forget that you can aggregate at the table level in the footer as well to get a total for everything.
