---
title: 'Editing and Formatting'
---

## Editing Column Labels

1. Double-click the column header label. A dark blue box appears around it to indicate it is selected.
2. Right-click and select **Edit Text**.
3. Edit the label and click outside the text box to save.

!!! info

    For CSV Reports, editing the column header label does not affect the underlying data binding. It is only a visual
    change. For more information on creating CSV reports, see the
    [Creating CSV Reports](../advanced/csv-reports.md) article.

## Formatting Data

To determine the type of data in a column, right-click any column and select **Data Fields**. The _Field Name_ column shows the column key and the _Type_ column shows the data type. If the type says "string", it is considered "text" for the purposes of this article.

To open the Format Data dialog:

1. Right-click the column header.
2. Select **Format > Format Data**.

The dialog will look different depending on the data type. Each type provides a _Custom_ option with a text box for entering a custom format string — examples of allowed characters are shown when selected.

### Formatting Numbers

1. Select the column containing the data you want to format (e.g. _Actual Hours_ from the _Timecard Transactions_ entity).
2. Open the **Format Data** dialog following the steps above.
3. Choose from the available options:
    - _Unformatted_
    - _General Number_
    - _Currency_
    - _Fixed_ (default for most)
    - _Percent_
    - _Scientific_
    - _Custom_

_Unformatted_ and _General Number_ drop trailing zeros after the decimal point. _Fixed_ is the default for most numbers from Pro WFM and displays two decimal places. To increase decimal places, change the _Decimal Places_ dropdown (max: 10).

### Formatting Dates

Open the **Format Data** dialog and choose from:

- `mmm dd, yyyy` (e.g. Jan 1, 2023)
- `MMM dd, yyyy` (e.g. January 1, 2023)
- `mm/dd/yyyy` (e.g. 01/01/2023)
- _Custom_

### Formatting Date and Time

Open the **Format Data** dialog and choose from:

- _Unformatted_ (default)
- `MMM dd, yyyy`
- `mm dd, yyyy`
- `mm/dd/yyyy`
- `hh:mm:ss a Z` (e.g. 12:00:00 PM UTC)
- `hh:mm:ss a` (e.g. 12:00:00 PM)
- `HH:mm` (e.g. 16:30)

The top option is equivalent to _Unformatted_ since it matches the default display.

!!! info

    Dates and times are unaffected by the Locale Policy of the user running the report and the Tenant Default. They
    will always display in American English format. Use the Custom option to format dates and times to another locale.
    Any format is applied for _all_ users running the report and is not individual.

### Formatting Time

The time options are the same as the last three options for [Formatting Date and Time](#formatting-date-and-time).

### Formatting Text

Open the **Format Data** dialog and choose from:

- _Unformatted_
- _Uppercase_
- _Lowercase_
- _Custom_

### Formatting Currency

Formatting currency follows the same steps as [Formatting Numbers](#formatting-numbers) — select the _Currency_ option from the dropdown. The available sub-options are:

- _Symbol_
- _Symbol Position_
- _Decimal Places_
- _Use 1000s Separator_
- _Negative Numbers_

### Formatting Booleans

Formatting a boolean only allows you to change the display text for the boolean value.

## Conditional Formatting

BIRT Studio allows you to format columns based on a specified condition.

1. Right-click the column you want to apply conditional formatting to.
2. Select **Format > Conditional Formatting**. The **Conditional Formatting** window opens. Its appearance varies by data type.
3. Click the **Format** link at the top to set the format (_Font_, _Font Size_, _Color_, _Background Color_, etc.).
4. In the condition row, select the column to evaluate in the first field.
5. Select the condition in the second field (e.g. Equal To, Between, Greater Than). These are explained in [Applying Filters](./filtering.md#filter-conditions).
6. Enter the value to compare against in the text field.

!!! warning

    The column that is selected is the column that the formatting is being applied _to_. Make sure that the column you
    want to format is the correct one listed next to the _Selected Column_ label.

## Changing Font Properties

1. Right-click the column header.
2. Select **Format > Font**. The **Font** dialog opens.
3. Adjust the options to preference and click **OK**.

## Changing the Alignment of Text

1. Right-click the column header.
2. Select **Alignment**. The **Alignment** dialog opens.
3. Choose **Align Left**, **Align Center**, or **Align Right**.
4. Click **OK**.

## Changing the Order of Columns

There are three ways to reorder columns:

**Drag and drop in the design view:**

1. Click anywhere inside the column to select it. A dark blue border appears around it.
2. Click and hold, then drag the column to the desired position. A blue line indicates where it will be placed.

**Using the Table Builder:**

1. Select a column, then click the table handle above the column headers.
2. Click the **Edit** icon to open the **Table Builder** window.
3. Under _Current Column Selections_, select a column and use the up/down arrows to reposition it.
4. Click **OK**.

**Drag and drop in preview mode:**

1. Preview the report.
2. Drag columns to the desired position.
3. Save the report after making changes.

!!! warning

    If there are computed columns in the report design, they will not appear in the Table Builder list.

!!! danger

    As of 09.08.00 (2024.R1), drag and drop in the design view is not working as expected — the column will not be
    placed where the blue line indicates. Use the Table Builder or preview mode instead.

## Merging Data into One Column

Merging data from two or more columns causes the data to display on multiple lines within a single column. This is useful for fitting more columns within the page width.

1. Hold <kbd>Ctrl</kbd> and click each column header to select the columns to merge.
2. Right-click any selected column and select **Column > Merge Columns**.

### How To Merge Column Headers

1. Double-click the column header cell in the bottom row of the merged column. A border appears around the header label.
2. Right-click and select **Cell > Merge Up**.
3. Repeat until one column header remains.

## Adding a New Column Header Row

When a new header row is inserted, it is added above the selected row and spans the full table width. Formatting and borders are copied from the row below.

### How To Add a New Column Header Row

1. Double-click inside the column header area to select it.
2. Right-click and select **Cell > Insert Row Above** (or **Cell > Insert Row Below** to add below the selected row).

### How To Merge Column Headers to Span Multiple Columns

1. Double-click the column header row you want to merge.
2. Right-click and select **Cell > Merge Right**.
3. Repeat across the entire row until all columns in the row are merged.

## Changing Column Width

1. Select the column.
2. Hover over the right edge of the column header until the resize cursor appears.
3. Click and drag to the desired width.

!!! info

    Resizing column width does not behave like Excel — there appears to be a maximum width depending on the number of
    columns in the table, and resizing one column may shrink adjacent ones. If columns are too narrow, consider switching
    the page orientation to landscape or setting the Page Layout to Auto Expand Width. See
    [Changing the Page Layout](#changing-page-layout) for more information.

## Changing Page Layout

1. In the menu bar, select **File > Page Setup...**.
2. Change _Orientation_ from _Auto_ to _Landscape_ if needed.
3. Change _Page Layout_ from _Fixed_ to _Auto Expand Width_ if needed.
4. Optionally change the paper _Size_ (_A4_, _US Legal_, _US Letter_, or _Custom_) and adjust _Margins_.
5. Click **OK**.

## Changing the Report Title

1. Double-click the **Report Title** text in the report header. A cursor appears inside the text box.
2. Edit the title.
3. Click outside the text box to save.
