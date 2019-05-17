---
title: "SELECTEDMEASURENAME function (DAX) | Microsoft Docs"
ms.service: powerbi 
ms.date: 04/25/2019
ms.reviewer: owend
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
---
# SELECTEDMEASURENAME

Used by expressions for calculation items to determine the measure that is in context by name.

> [!NOTE]
> This function currently applies only to [SQL Server 2019 Analysis Services CTP 2.3](https://docs.microsoft.com/sql/sql-server/what-s-new-in-sql-server-ver15?view=sqlallproducts-allversions#calc-ctp24) and later.
  
## Syntax  
  
```dax
SELECTEDMEASURENAME() 
```
  
#### Parameters  
  
None  
  
## Return value  

A string value holding the name of the measure that is currently in context when the calculation item is evaluated. 

## Remarks

Can only be referenced in the expression for a calculation item. 

This function is often used for debugging purposes when authoring calculation groups.


## Example  

The following calculation item expression checks if the current measure is Expense Ratio and conditionally applies calculation logic. Since the check is based on a string comparison, it is not subject to formula fixup and will not benefit from object renaming being automatically reflected. For a similar comparison that would benefit from formula fixup, please see the ISSLECTEDMEASURE function instead. 
  
```dax
IF (
    SELECTEDMEASURENAME = "Expense Ratio",
    SELECTEDMEASURE (),
    DIVIDE ( SELECTEDMEASURE (), COUNTROWS ( DimDate ) )
)
```
  
## See also  
[SELECTEDSMEASURE](selectedmeasure-function-dax.md)  
[ISSELECTEDSMEASURE](isselectedmeasure-function-dax.md)   
  