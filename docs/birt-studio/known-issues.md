---
title: 'Known Issues'
editUrl: false
---

This is only meant to serve as the known issues with BIRT Studio and not as a comprehensive list of all issues. If you
are experiencing an issue that is not listed here, please contact support.

## Computed Column Expression Does Not Update in the UI

When creating a computed column expression, there is a known issue where the expression may not update in the UI after
it has been saved. This is a visual issue and does not affect the functionality of the expression. If you are having
trouble knowing what expression is currently being executed, please open a case with Support who can look into the
design for you and help troubleshoot.

## Drag & Drop Functionality Does Not Work as Expected

There is a known issue where the drag & drop functionality may not work as expected. This includes dragging column
objects from the **BaseDataSet** into the design and dragging columns added to the design to re-order them in the
layout. This issue is intermittent. Support has not been able to determine when this will work and when it will not.

## Custom Report Parameter Disappears After Creation

When running a custom report that has a [custom report parameter](/docs/birt-studio/advanced/custom-report-parameters),
the parameter may not appear in the Report Library when attempting to run the report. The Parameter toggles itself to
invisible sometimes after creation. Navigate to Application Setup > Common Setup > Published Reports and edit your
published report (not edit design). Select the custom report parameter and click "Edit" and select the "Visible" option.