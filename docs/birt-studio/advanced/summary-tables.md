---
title: 'Creating Summary Tables'
description: How to create summary tables using grouping and aggregations in BIRT Studio.
---

## Introduction

Summary tables are built like any other table you'd add to a report. Most of the time, you will even end up using the same Report Data Object that you used to build the report. The difference between a normal table and a summary table is that a summary table uses a combination of groupings, aggregations, and hiding of details to create a summary of the data. If you are unfamiliar with any of these concepts or need a refresher, please review [Grouping](../customizing-reports/grouping.md), [Aggregating](../customizing-reports/aggregating.md), and [Filtering](../customizing-reports/filtering.md).

## Creating a Summary Table

At a basic level, creating a summary table involves three steps. You'll start by adding the columns you need to a new table. Then you'll group by the desired column you want summarized. For example, if you want to summarize the hours for all Paycodes, you would group by Paycode Name. Next, you need to create an aggregation on the column that you want to act as the metric. Finally, you hide the group details. Your data could end up looking like the below example.

### Adding Columns

To begin creating the summary table, you need to create a new table in the report design. To do this, click **Insert > Table > Table** from the menu bar. This will open the **Table Builder** window. In this window, select the columns you want and move them over by clicking the right **Add** arrow button. You can <kbd>Ctrl</kbd>+<kbd>Click</kbd> to select multiple columns at once. Once you have all the columns you want, click **OK** to add the table to the report design. If there is an existing table, the new table will be added above it.

!!! info

    It is not required, but as a best practice, if the RDO is an employee-based RDO, at least one column from the
    _Employee Details_ entity should be included, such as _Employee Full Name_ or _Employee ID_. This will
    help with troubleshooting in the future if needed.

For more information on adding columns to a report design, please see [Getting Started](../introduction/getting-started.md#adding-columns-to-the-report).

### Grouping

After adding the columns for the new table, group by the column you want to summarize. For example, if you want to summarize the total hours for Paycodes, group by the _Paycode Name_ column. Select the column and click the **Add Group** icon.

For more information on creating groups and grouping data, please see [Grouping](../customizing-reports/grouping.md).

### Aggregating

Once the group is applied, apply aggregations on the columns you want to summarize. In our example, we want to summarize the total hours for each Paycode. To do this, add an aggregation on the _Hours_ column. Select the column and click the **Aggregation (Σ)** icon. This will open the **Aggregation Builder** window. Select the aggregation type you want to use — in our example, use _Sum_. Set it to aggregate on the _Group_ and in the _header_. Click **OK** to add the aggregation to the column.

For more information on creating aggregations, see the [Aggregating](../customizing-reports/aggregating.md) page.

### Hiding Details

The final step in creating our summary table is to hide the details of the group. The "detail" rows are the rows that are in white (by default) and are not in the group header row. The only data we would have in our group header row at this point should be the Paycode Name and the aggregated hours. To hide the details, right-click on the grouped column and select **Group > Hide Details** from the context menu. This will hide the detail rows and only show the group header rows.

Hiding Details is covered in the [Grouping](../customizing-reports/grouping.md#hiding-details) article.

## Other Considerations

Here are some other considerations for your next summary table:

-   The summary table can be expanded to include more groups and aggregated data.
-   Grouping by 1–2 columns is most readable in a summary table.
-   You can change the background color of the group header row to make it stand out from detail rows.
-   Try changing the font, font size, and font color.
-   When aggregating the data, don't forget that you can aggregate at the table level in the footer as well to get a total for everything.
