---
title: "TOTALQTD Function (DAX) | Microsoft Docs"
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
  - "sql13.as.daxref.TOTALQTD.f1"
helpviewer_keywords: 
  - "TOTALQTD function"
ms.assetid: 8831561e-b92f-470c-a452-b4f213721668
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "kfile"
---
# TOTALQTD Function (DAX)
Evaluates the value of the **expression** for the dates in the quarter to date, in the current context.  
  
## Syntax  
  
```  
TOTALQTD(<expression>,<dates>[,<filter>])  
```  
  
#### Parameters  
  
|Parameter|Definition|  
|-------------|--------------|  
|**expression**|An expression that returns a scalar value.|  
|**dates**|A column that contains dates.|  
|**filter**|(optional) An expression that specifies a filter to apply to the current context.|  
  
## Return Value  
A scalar value that represents the **expression** evaluated for all dates in the current quarter to date, given the dates in **dates**.  
  
## Remarks  
The **dates** argument can be any of the following:  
  
-   A reference to a date/time column.  
  
-   A table expression that returns a single column of date/time values.  
  
-   A Boolean expression that defines a single-column table of date/time values.  
  
> [!NOTE]  
> Constraints on Boolean expressions are described in the topic, [CALCULATE Function &#40;DAX&#41;](calculate-function-dax.md).  
  
> [!NOTE]  
> The **filter** expression has restrictions described in the topic, [CALCULATE Function &#40;DAX&#41;](calculate-function-dax.md).  
>   
> This DAX function is not supported for use in DirectQuery mode. For more information about limitations in DirectQuery models, see  [http://go.microsoft.com/fwlink/?LinkId=219172](http://go.microsoft.com/fwlink/?LinkId=219172).  
  
## Example  
The following sample formula creates a measure that calculates the 'quarter running total' or 'quarter running sum' for the Internet sales.  
  
To see how this works, create a PivotTable and add the fields, CalendarYear, CalendarQuarter and MonthNumberOfYear, to the **Row Labels** area of the PivotTable. Then add a measure, named **Quarter-to-date Total**, using the formula defined in the code section, to the **Values** area of the PivotTable.  
  
## Code  
  
```  
=TOTALQTD(SUM(InternetSales_USD[SalesAmount_USD]),DateTime[DateKey])  
```  
  
## See Also  
[ALL Function &#40;DAX&#41;](all-function-dax.md)  
[CALCULATE Function &#40;DAX&#41;](calculate-function-dax.md)  
[TOTALYTD Function &#40;DAX&#41;](totalytd-function-dax.md)  
[TOTALMTD Function &#40;DAX&#41;](totalmtd-function-dax.md)  
[Get Sample Data](http://go.microsoft.com/fwlink/?LinkId=164474)  
  