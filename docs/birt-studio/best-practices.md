---
title: Best Practices
description:
    'A list of best practices that have been developed by report SMEs within Support and will help when building custom
    reports.'
---

# Best Practices

These are a list of best practices that have been developed by report SMEs within Support and will help when building custom reports.

!!! info

    None of these are a must and should not be taken as absolute rules, but not following some of them has been known
    to cause issues with reports or add to report development time due to confusion, unclear names, or other reasons.

## Naming Conventions

When naming your report, it is best to follow a standard naming convention. Typically we recommend naming reports in **PascalCase** or **camelCase**. This will help you and others understand what the report is for and what it does. Here are some examples of what would be considered good naming conventions:

-   EmployeeHoursByJob
-   EmployeeHoursByJobAndDate
-   PunchDetailReport
-   TimecardAudit
-   EmployeeActivityHours

## Each Report Data Object Has a Purpose

A Report Data Object (RDO) should be used in at most one report. The idea is that an RDO should contain _only_ the exact number of columns that a single report needs. This helps prevent any future issues or conflicts that may come up if the RDO was used in multiple reports. It also helps keep runtimes down in reports that do not make use of all the columns. This is because even when a column is added to an RDO but not used in the report design, the data is still requested when the report is run, which can increase the runtime of the report.

!!! note

    This rule can be broken in cases where multiple reports make use of all (or most) of the columns in the RDO, but
    we don't suggest using the RDO in reports where this is not the case.

## Think of the Employees!

When creating an employee-based RDO, it is best practice to add _at least_ one column from the **Employee Details** entity first. This will set the relationship rules so that only those entities that relate to **Employee Details** can be added. This keeps the RDO conforming to column relationship rules and ensures your report will not have any issues due to the configuration of the RDO.

## Leave Column Relationship Rules On

When building an RDO or Dataview, the Column Relationship Rules checkbox is enabled by default and the control is hidden behind a Feature Switch. The Feature Switch is called "Ability to disable column relationship rules". Enabling this setting will make the checkbox visible again. While this Feature Switch can be enabled to show the checkbox again, we **do not recommend disabling column relationship rules**.

!!! danger

    By disabling column relationship rules, you are opening your RDO/Dataview up for potential issues. When unrelated
    entities are used together in an RDO, the report may display unexpected behaviors. Some indications that unrelated
    entities are being used are:

    -   Duplicate rows with seemingly the same data
    -   Blank rows
    -   "Duplicate" rows where one row shows data in some columns and not others and the subsequent rows showing data
        in the other columns
    -   No data
    -   Errors

    If a Support case is entered and the issue is with a report or Dataview that has Column Relationship Rules
    disabled, Support will not be able to assist until a new RDO or Dataview is created with Column Relationship
    Rules enabled.

## Each Report Has a Purpose

Just like [above](#each-report-data-object-has-a-purpose), each report should have a purpose too. It is easy to get carried away with creating dozens of computed columns, aggregating unnecessarily, applying too much formatting, etc. — and before you know it, BIRT can no longer load your report, it loads much slower, it starts to fail, or things stop working while editing. These are all symptoms and indications that a report might be trying to do _too_ much.

The best recommendation is to start with a single idea and a single desired goal of what the report should tell an end-user. Here are some tips to help you focus your ideas:

**Be as specific as possible**<br>
Want to create a report of Paycode totals? Great — which ones? Do the Paycodes have something in common that would help you further identify your goal (e.g., are they all Overtime Paycodes, are they all related to Exceptions, Leave, or Absences)? Being specific in your goal and desired output will help prevent scope creep and any potential issues down the road.

**Computed columns for the sake of computed columns**<br>
Don't create computed columns just for the sake of it. If a computed column is made, don't leave it unused somewhere in your report. Remember, every computed column adds to what needs to be loaded when editing a report design and running a report.

!!! info

    Most computed column expressions are "free" in that they shouldn't cause too much overhead. The issue starts
    when one computed column is trying to do too much or there are too many computed columns all doing the same thing
    (such as computing out hours for a Paycode and returning those hours in a column instead of a row).

**Follow these best practices**<br>
The best practices presented here and in our articles on this site are meant to guide you to creating the best report possible with zero issues in the final report.

If you feel your report is following these suggestions and you are still having issues with your report failing to open, failing to run, or returning errors, please open a case with Support.

!!! warning

    Troubleshooting issues where these best practices are not followed can be difficult, and a first step may be to
    go back and rework the RDO or design.
