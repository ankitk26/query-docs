---
title: "LASTDATE Function (DAX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/28/2017"
ms.prod: "powerbi"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "daxlang"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "sql13.as.daxref.LASTDATE.f1"
helpviewer_keywords: 
  - "LASTDATE function"
ms.assetid: 3e336a50-cd75-4543-9d2d-e1b0ff1db4f2
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "kfile"
---
# LASTDATE Function (DAX)
Returns the last date in the current context for the specified column of dates.  
  
## Syntax  
  
```  
LASTDATE(<dates>)  
```  
  
#### Parameters  
  
|Term|Definition|  
|--------|--------------|  
|**dates**|A column that contains dates.|  
  
## Return Value  
A table containing a single column and single row with a date value.  
  
## Remarks  
The **dates** argument can be any of the following:  
  
-   A reference to a date/time column,  
  
-   A table expression that returns a single column of date/time values,  
  
-   A Boolean expression that defines a single-column table of date/time values.  
  
> [!NOTE]  
> Constraints on Boolean expressions are described in the topic, [CALCULATE Function &#40;DAX&#41;](calculate-function-dax.md).  
  
When the current context is a single date, the date returned by the FIRSTDATE and LASTDATE functions will be equal.  
  
Technically, the return value is a table that contains a single column and single value. Therefore, this function can be used as an argument to any function that requires a table in its arguments. Also, the returned value can be used whenever a date value is required.  
  
This DAX function is not supported for use in DirectQuery mode. For more information about limitations in DirectQuery models, see  [http://go.microsoft.com/fwlink/?LinkId=219172](http://go.microsoft.com/fwlink/?LinkId=219172).  
  
## Example  
The following sample formula creates a measure that obtains the last date, for the current context, when a sale was made in the Internet sales channel.  
  
To see how this works, create a PivotTable and add the field CalendarYear to the **Row Labels** area of the PivotTable. Then add a measure, named **LastSaleDate**, using the formula defined in the code section, to the **Values** area of the PivotTable.  
  
```  
=LASTDATE('InternetSales_USD'[SaleDateKey])  
```  
  
## See Also  
[Date and Time Functions &#40;DAX&#41;](date-and-time-functions-dax.md)  
[Time Intelligence Functions &#40;DAX&#41;](time-intelligence-functions-dax.md)  
[FIRSTDATE Function &#40;DAX&#41;](firstdate-function-dax.md)  
[LASTNONBLANK Function &#40;DAX&#41;](lastnonblank-function-dax.md)  
[Get Sample Data](http://go.microsoft.com/fwlink/?LinkId=164474)  
  