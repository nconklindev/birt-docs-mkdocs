---
title: Getting Started
---

# Getting Started

## About BIRT Studio

BIRT Studio is a web-based report designer built into Pro WFM. It lets you create professional reports without deep knowledge of database architecture or report design — all you need is a basic understanding of the available data and the ability to drag and drop fields onto a canvas.

## Who This Guide is For

This guide introduces the basic concepts and steps for creating a custom report in BIRT Studio. It is not a comprehensive reference for every feature. For more advanced topics, see the other articles in the sidebar.

## When to Use Reports

Reports are a great way to get data out of Pro WFM. They are straightforward to create, and most dataviews can be turned into reports. Reports also have capabilities that dataviews do not:

- Can be scheduled to run automatically
- Can be exported to PDF or Excel
- Support custom parameters and filters

While reports take a few more steps to set up, they can be significantly more powerful than dataviews.

## Creating a Report Data Object

Before building a report in BIRT Studio, you need to create a **Report Data Object (RDO)**. The RDO defines which entities and columns will be available in your report design.

1. From the home screen, open the navigation menu and go to **Application Setup > Common Setup > Report Data Object Management**.
2. Click **Add**. A dropdown appears with the following RDO types:
    - **Employee**
    - **Business Structure View**
    - **Employee - Time Series**
    - **Business Structure - Time Series**
    - **Work Unit View** and **Work Unit - Time Series** (available if Healthcare Analytics is enabled)

!!! tip
    Most reports use **Employee** or **Business Structure View**.

3. Enter a **Report Data Object Key**. This is the identifier used when adding the RDO to a report design.
4. Optionally enter a **Description**.
5. Set the **TimeFrame**. The default of _Selected Time Period_ is appropriate for most reports.
6. Click **Save**.

!!! tip

    Use the same name for the RDO as the report you are creating. Standard naming conventions include **ReportName_DO** or **ReportName_version** where *version* is the iteration number.

!!! info

    The **Column Relationship Rules** checkbox may not be visible in your environment. If it is not, enable it via a Feature Switch under **Application Setup > System Configuration > Feature Switch**. The switch is called *Ability to Disable Column Relationship Rules*.

### Adding Columns to an RDO

1. Click **Add**. The **Select Column** screen opens.
2. Select the columns you want to add and click **Add Column**.
3. Optionally change the default _Label_ for each column.
4. Click **Save** when done.

## Creating a Report Design

Once your RDO is ready, you can create the report design in BIRT Studio.

1. Open the navigation menu and go to **Application Setup > Common Setup > Unpublished Reports**.
2. Click **Create**. This opens BIRT Studio. If the button reads **Create Design**, click it and select **Common Report** from the dropdown.

### Adding an RDO to the Report Design

1. In BIRT Studio, select **Data > Manage Data** from the top menu. The **Manage Data** window opens.
2. In the _Available Data_ area, select your RDO.
3. Click the arrow icon between the two areas to move it to the _Selected Data_ area.
4. Click **OK**.

!!! warning

    Do not delete the **Hyperfind_DO** during this step. It provides the Hyperfind selector when previewing the report. If deleted, there will be no Hyperfind dropdown and you will need to know the Hyperfind ID to run the report.

!!! info

    Only Custom RDOs appear in this window — Standard and Read-Only RDOs do not. To use a Standard RDO, you must first duplicate the standard report and its RDO.

After adding the RDO, the **Save** button becomes active. If you save now, a dialog will prompt you to enter a _File Name_ — use the same name as the RDO as a best practice.

After saving (or skipping it), the left sidebar will appear empty. **This is normal.** Click anywhere inside the bordered box in the center to populate it with two folders: one for your RDO's data and one for the _Hyperfind_DO_.

## Adding Columns to the Report

1. In the left sidebar, expand the _BaseDataSet_ for your RDO. The columns appear listed by their labels.
2. Drag a column from the sidebar onto the report canvas. To add multiple columns at once in order, click the first column, then **Ctrl + click** each additional column, then drag them all onto the canvas.
3. Click **Save**. If this is your first save, a dialog will prompt you to enter a _File Name_.

!!! info

    If the table is not generating, try dragging the columns into the bordered text box at the top of the canvas, below the header.

## Publishing a Report

1. Open the navigation menu and go to **Application Setup > Common Setup > Unpublished Reports**.
2. Select the report and click **Publish**. The **Unpublished Reports - Create Published Report** page opens.
3. Fill in the fields:
    - **Report Name** *(required)* — The name that will appear in the application.
    - **Report Description** *(optional)*
    - **Default Output Type** *(required)* — PDF, Excel, Interactive, or CSV.
    - **Output Formats** *(required)* — One or more formats available when running the report.
    - **Currency Display As** *(optional)* — _Logged-in User_ or _Employee Assigned_.
    - **Category** *(optional)* — The category the report appears under in the Report Library.
4. Review the **Report Parameters** table. The default parameters for a custom report are:
    - _TimeFrame_ — Provides the timeframe selector when running the report.
    - _HyperFindSelector_ — Provides the Hyperfind selector when running the report.
    - _ShowChart_ — Provides the "Show Chart" radio buttons. Set _Display_ to false to hide it.
5. Click **Save**.

!!! warning

    Setting _TimeFrame_ or _HyperFindSelector_ to _Display_ = false hides those parameters and defaults them to Today and All Home. Setting either to _Required_ = false will cause the report to fail — these parameters are required.

Congratulations on publishing your first custom report!

## Testing Your Report

1. From the home screen, open the navigation menu and go to **Dataviews & Reports > Report Library**.
2. Click **Run Report**. A **Select Report** drawer slides open from the right.
3. Expand the category the report was published under, select the report, and click **Select**.
4. Set the desired parameters — Today for All Home is a good baseline test — and click **Run Report**.

The report appears under **In Progress** while running, then moves to **Completed** when done. Clicking the tile prompts you to download the file for any output type other than _Interactive_.

## What's Next

- [Applying Filters](../customizing-reports/filtering.md)
- [Editing and Formatting](../customizing-reports/editing-and-formatting.md)
