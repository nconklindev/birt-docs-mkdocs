---
title: "Changing the Default Hyperfind Parameter"
---

## BIRT Studio Default Parameters

By default, BIRT Studio attempts to load the data from the Report Data Object (RDO) for today and *All Home*. For some
tenants, this can result in performance issues when trying to edit the design of
the report. It is a common problem with large tenants and *Audit*-based Report Data Objects. However, it is not
necessarily isolated to the Audit entity alone.

In these circumstances, the default parameters can be changed to load the data from a different entity.

!!! warning

    It is recommended to only change the default parameters if there is a performance issue when trying to edit a published or unpublished report in BIRT Studio.

BIRT Studio comes with a set of default parameters that can be changed. These parameters are:

1. `TimeFrame_startDate`
2. `TimeFrame_endDate`
3. `HyperFindSelector_Id`

!!! danger

    Out of the three parameters, only the `HyperFindSelector_Id` parameter should be changed. Changing `TimeFrame_startDate` or `TimeFrame_endDate` may cause report errors.

## Changing the Default Parameters

!!! warning

    If there is an existing report that will not load with the default parameters, it must be re-created from scratch. Update the parameters before adding the Report Data Object to prevent performance issues during report design.

### Finding the Hyperfind ID

Before changing the default parameters, find the Hyperfind ID you want to use.

1. Under the **File** menu, click **Preview**
2. In the list of Hyperfinds, find the one you want to use as the default and note its ID. Each Hyperfind in the
   list is displayed in the format `Name|ID`.

### Setting the New Hyperfind ID

1. Create a new report
2. From the **File** menu, select **Data > Manage Parameters**
3. Click the **pencil icon** next to the `HyperFindSelector_Id` parameter to edit it
4. In the *Default Value* field, delete `-5001` and enter the ID found in the previous step
5. Click **Save Parameter** to save the changes
