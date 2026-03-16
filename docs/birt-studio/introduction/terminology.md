---
title: 'BIRT Studio Terminology'
description: 'A glossary of terms used in BIRT Studio'
---

# BIRT Studio Terminology

A list of terms that can be used to help you understand BIRT Studio.

!!! info

    The terms presented in this article are a combination of terms found in the BIRT Studio documentation, terms commonly
    found in the data analytics sphere, or terms that are used within UKG Support to describe BIRT Studio functionality.

## A

### Adhoc

Typically refers to the way a report is run. When run from the **Report Library**, the execution of that report is said
to be "Adhoc".

### Aggregation

A function that is applied at the group level that provides some form of calculation to data within a column.

### Auto expand width

A report page property that causes all columns to take up equal width, and expand to the full width of the configured
paper type and width (i.e. portrait vs landscape).

### Analytics Studio

The page title that appears in the browser window or tab when working within BIRT Studio. Alias for **BIRT Analytics
Studio**.

## B

### BaseDataSet

The object that is created to include the columns from the Report Data Object. Appears as a collapsible category in the
left sidebar of BIRT Studio.

### BIRT Designer/Desktop

The software that is used by Professional Services to build custom reports. Includes more advanced functionality than
what is within BIRT Studio. Requires a Service Request for a custom report to be made. Not available for customer use.

### BIRT Studio

The software available in Pro WFM for any manager with the necessary access to build custom reports. See term
[analytics studio](#analytics-studio).

## C

### Column

The item that is selected in the [Report Data Object](#report-data-object) to be returned in the report design, or can
be computed from existing data in a report. A vertical series of objects within a table or chart. Used with a capital
*C*olumn when differentiating between Crosstab Columns and RDO columns (when used in the same context).

### Column header

The text that is displayed for a single column in a report design. This may be the same as the [label](#label), but does
not have to be and can be changed independently of the label.

### Concatenation

A non-BIRT term that means "a series of interconnected things or events". Typically refers to piecing together String
type columns using a computed column in BIRT Studio.

### Crosstab

A type of report table that can be included in a report design. A crosstab displays data in a row-and-column matrix that
has a spreadsheet like appearance. Ideal for summarizing data in a compact and concise format.

### Custom report

A report type that designates a report that was built within BIRT Studio.

### Custom Read-Only

A report type that designates a report that was built by Professional Services or Partner using
[BIRT Designer](#birt-designerdesktop). These reports cannot be edited in BIRT Studio.

## D

### Data type

Refers to the type of data that a selected column returns in a Report Data Object. Data Types include:

-   String (text)
-   Boolean (true or false)
-   Number (used as a catch-all term to include Float and Integer types)
-   Date (e.g. 2024-01-08)
-   DateTime (e.g. 2024-01-08 14:00:00.000)
-   [Enum](#enum) (e.g. a set of predefined named values)

### Design view

A non-standard BIRT Studio term that refers to the standard and default view that all BIRT Studio reports open up into.

### Detail row

Identifies the row(s) of data that appears underneath a [group](#groups). See
[Grouping Data](../customizing-reports/grouping.md). Detail rows do not exist without at least one
level of grouping.

### Dynamic Filter

An option that is available when creating a report filter.

!!! warning

    Dynamic filters do not work in the Pro WFM implementation of BIRT Studio

## E

### EasyScript

The custom scripting language that is specific to BIRT and BIRT Studio. It is used in the creation of
[computed columns](../advanced/computed-columns.md).

### Entity

The group of related data that a report column belongs to.

### Enum

Short for "enumerated type". A data type that consists of a set of named values that act as constants. Used to define a
variable that can only be equal to one of the predefined values.

## F

### Float

A data type that represents a fractional number, written as a decimal.

### Filter

A condition or conditions applied to a column to include or exclude specific data.

### Fixed width

A report page property that causes all columns to be the same width, allowing individual columns to be manually resized.

## G

### Groups

A set of related rows to make it easier to compare and analyze information.
[Groups](../customizing-reports/grouping.md) can be manually applied in BIRT Studio.

### Grand Total

Totals that are applied to a Crosstab report that provide Row or Column totals.

## I

### Information Access (IA)

The intermediary service that lies between Pro WFM and the data. Responsible for querying UKG infrastructure to obtain
the necessary data for the report.

### Integer

A data type that represents a number that is not a fraction. A whole number.

### Interactive mode

A report output format that all reports can be run as. It is selected when publishing a new custom report or selected in
the **Report Options** for any report. This is the mode that is rendered when previewing reports while working in BIRT
Studio. Provides an interactive table that can be manipulated in its own window or tab.

!!! warning

    Tables can only be manipulated while under 200 pages.

## L

### Label

The text that is configured on a column added within a Report Data Object. When working with reports, this term will
always reference the RDO column label and not the column header text.

## M

### Measure

A numerical value within a Crosstab report that is selected from the numerical type columns included in the Report Data
Object.

## N

### null

A Computer Science term to indicate a value that points, generally intentionally, to a nonexistent or invalid object or
address<sup>[1](https://developer.mozilla.org/en-US/docs/Glossary/Null)</sup>. In BIRT reporting, cells that have no
data in them would be considered having a null value. The value of zero (0) is considered numerical and would not be
considered null.

## O

### Operators

Indicates the type of operation that is applied to an individual item. Can be applied to filters and in expressions.

## P

### Parameter

A customizable option that allows a user to customize a report execution to their liking. Examples include:

-   Timeframe
-   Hyperfind
-   Pay Codes
-   Output

[Custom report parameters](../advanced/custom-report-parameters.md) can be created within BIRT Studio.

### Preview mode/view

A non-standard BIRT term to refer to the [interactive viewer](#interactive-mode) that is opened after pressing the
"Preview" button inside BIRT Studio.

## R

### Report Data Object

Created before working on a report in Application Setup. Contains all of the entities and columns that the report design
will be using.

### Report Job

An event that indicates a scheduled or adhoc report request.

### Row

The data that is returned in a report table after it has been fetched from the server. Used with a capital *R*ow when
differentiating between Crosstab Columns and RDO columns (when used in the same context).

## S

### Section

An organization feature that is functionally equivalent to a group. Also groups data.

### Standard Read-Only

A type of report that is included with Pro WFM. They are built in [BIRT Designer](#birt-designerdesktop) by Engineering
and cannot be modified.

## T

### Table Handle

A non-standard BIRT term to indicate the bar that appears above a report table when the entire table is selected.
Includes icons such as "Delete", "Insert Chart", "Filter", "Edit" and "Properties".

## U

### Unrelated entities

Describes a Report Data Object that contains entities that do not relate to one another per the selected entity's
related entities.

## W

### WFM-COMMON-1234

A common error that may appear when working on or running a report. The error is typically due to access issues. See
[WFM-COMMON-1234](../faq.md#my-report-displays-a-red-error-showing-code-wfm-common-1234-what-is-this-and-how-do-i-fix-it).

## References

1: https://developer.mozilla.org/en-US/docs/Glossary/Null