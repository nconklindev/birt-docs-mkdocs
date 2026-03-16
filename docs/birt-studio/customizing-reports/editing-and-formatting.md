---
title: 'Editing and Formatting'
---

## Editing Column Labels

1. Double-click the column header label. A dark blue box appears around it to indicate it is selected.
2. Right-click and select _Edit Text_.
3. Edit the label and click outside the text box to save.

!!! info

    For CSV Reports, editing the column header label does not affect the underlying data binding. It is only a visual
    change. For more information on creating CSV reports, see the
    [Creating CSV Reports](../advanced/csv-reports.md) article.

## Formatting Data

To determine the type of data in a column, right-click any column and select _Data Fields_. The _Field Name_ column shows the column key and the _Type_ column shows the data type. If the type says "string", it is considered "text" for the purposes of this article.

To open the Format Data dialog:

1. Right-click the column header.
2. Select _Format > Format Data_.

The dialog will look different depending on the data type. Each type provides a **Custom** option with a text box for entering a custom format string — examples of allowed characters are shown when selected.

### Formatting Numbers

1. Select the column containing the data you want to format (e.g. **Actual Hours** from the **Timecard Transactions** entity).
2. Open the **Format Data** dialog following the steps above.
3. Choose from the available options:
    - Unformatted
    - General Number
    - Currency
    - Fixed (default for most)
    - Percent
    - Scientific
    - Custom

**Unformatted** and **General Number** drop trailing zeros after the decimal point. **Fixed** is the default for most numbers from Pro WFM and displays two decimal places. To increase decimal places, change the _Decimal Places_ dropdown (max: 10).

### Formatting Dates

Open the **Format Data** dialog and choose from:

- `mmm dd, yyyy` (e.g. Jan 1, 2023)
- `MMM dd, yyyy` (e.g. January 1, 2023)
- `mm/dd/yyyy` (e.g. 01/01/2023)
- Custom

### Formatting Date and Time

Open the **Format Data** dialog and choose from:

- Unformatted (default)
- `MMM dd, yyyy`
- `mm dd, yyyy`
- `mm/dd/yyyy`
- `hh:mm:ss a Z` (e.g. 12:00:00 PM UTC)
- `hh:mm:ss a` (e.g. 12:00:00 PM)
- `HH:mm` (e.g. 16:30)

The top option is equivalent to Unformatted since it matches the default display.

!!! info

    Dates and times are unaffected by the Locale Policy of the user running the report and the Tenant Default. They
    will always display in American English format. Use the Custom option to format dates and times to another locale.
    Any format is applied for _all_ users running the report and is not individual.

### Formatting Time

The time options are the same as the last three options for [Formatting Date and Time](#formatting-date-and-time).

### Formatting Text

Open the **Format Data** dialog and choose from:

- Unformatted
- Uppercase
- Lowercase
- Custom

### Formatting Currency

Formatting currency follows the same steps as [Formatting Numbers](#formatting-numbers) — select the **Currency** option from the dropdown. The available sub-options are:

- Symbol
- Symbol Position
- Decimal Places
- Use 1000s Separator
- Negative Numbers

### Formatting Booleans

Formatting a boolean only allows you to change the display text for the boolean value.

## Conditional Formatting

BIRT Studio allows you to format columns based on a specified condition.

1. Right-click the column you want to apply conditional formatting to.
2. Select _Format > Conditional Formatting_. The **Conditional Formatting** window opens. Its appearance varies by data type.
3. Click the _Format_ link at the top to set the format (Font, Font Size, Color, Background Color, etc.).
4. In the condition row, select the column to evaluate in the first field.
5. Select the condition in the second field (e.g. Equal To, Between, Greater Than). These are explained in [Applying Filters](./filtering.md#filter-conditions).
6. Enter the value to compare against in the text field.

!!! warning

    The column that is selected is the column that the formatting is being applied _to_. Make sure that the column you
    want to format is the correct one listed next to the _Selected Column_ label.

## Changing Font Properties

1. Right-click the column header.
2. Select _Format > Font_. The **Font** dialog opens.
3. Adjust the options to preference and click **OK**.

## Changing the Alignment of Text

1. Right-click the column header.
2. Select _Alignment_. The **Alignment** dialog opens.
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
2. Right-click any selected column and select _Column > Merge Columns_.

### How To Merge Column Headers

1. Double-click the column header cell in the bottom row of the merged column. A border appears around the header label.
2. Right-click and select _Cell > Merge Up_.
3. Repeat until one column header remains.

## Adding a New Column Header Row

When a new header row is inserted, it is added above the selected row and spans the full table width. Formatting and borders are copied from the row below.

### How To Add a New Column Header Row

1. Double-click inside the column header area to select it.
2. Right-click and select _Cell > Insert Row Above_ (or _Insert Row Below_ to add below the selected row).

### How To Merge Column Headers to Span Multiple Columns

1. Double-click the column header row you want to merge.
2. Right-click and select _Cell > Merge Right_.
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

1. In the menu bar, select _File > Page Setup..._.
2. Change **Orientation** from "Auto" to "Landscape" if needed.
3. Change **Page Layout** from "Fixed" to "Auto Expand Width" if needed.
4. Optionally change the paper **Size** (A4, US Legal, US Letter, or Custom) and adjust **Margins**.
5. Click **OK**.

## Changing the Report Title

1. Double-click the **Report Title** text in the report header. A cursor appears inside the text box.
2. Edit the title.
3. Click outside the text box to save.
