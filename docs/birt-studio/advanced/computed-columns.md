---
title: 'Creating Computed Columns'
description: How to create computed columns in BIRT Studio using the custom functions provided.
---

## What are Computed Columns?

Computed Columns in BIRT Studio are columns that are created using the custom functions provided in BIRT Studio.
The [functions](#birt-studio-functions) in BIRT Studio are somewhat similar to function calls in a modern programming
language such as Python or JavaScript, written as `functionName(arg1, arg2, ...)`. The function is written in a
dedicated text box within the Computed Column window.

## Creating a Computed Column

To create a computed column in BIRT Studio, right-click on a column header and select **Column > New Computed Column**.
This will open the _New Computed Column_ window.

In the _Column Label_ field, enter a label for the column. This will be the name that appears in the column header.
There is a _Category_ dropdown that will allow you to browse the existing function categories mentioned below. Changing
this dropdown changes the functions available in the _Select Function_ area.

To enter a custom expression, select "Advanced..." in any category. This shows a previously hidden _Enter Expression_
text area. Enter your custom expression here. Click the _Validate_ button to check if the expression is valid. If it is
valid, a dialog stating "The expression is valid" will appear. If it is invalid, BIRT Studio will alert you. Click **OK
** to close the dialog. Click **Cancel** to close the _New Computed Column_ window without saving. Click **OK** in the
_New Computed Column_ window to save the computed column.

!!! info

    If you are creating a computed column that is only being used in another computed column, a good practice is to
    set the label in camelCase so that it is easy to identify it from other computed columns and serves as a reminder
    that it is not being displayed in the final report.

!!! warning

    Column labels cannot be changed once the computed column has been saved. Make sure you are happy with the label
    before saving.

## BIRT Studio Functions

The functions in BIRT Studio are separated into several categories in the UI:

- Comparison
- Financial
- Text
- Math
- Date & Time
