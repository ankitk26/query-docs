---
title: "FILTER Function (DAX) | Microsoft Docs"
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
  - "sql13.as.daxref.FILTER.f1"
helpviewer_keywords: 
  - "FILTER function"
  - "Filtering"
ms.assetid: f1f6bee4-547b-407c-b70b-9216b2f3d3fd
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "kfile"
---
# FILTER Function (DAX)
Returns a table that represents a subset of another table or expression.  
  
## Syntax  
  
```  
FILTER(<table>,<filter>)  
```  
  
#### Parameters  
  
|Term|Definition|  
|--------|--------------|  
|**table**|The table to be filtered. The table can also be an expression that results in a table.|  
|**filter**|A Boolean expression that is to be evaluated for each row of the table. For example, `[Amount] > 0` or `[Region] = "France"`|  
  
## Return Value  
A table containing only the filtered rows.  
  
## Remarks  
You can use FILTER to reduce the number of rows in the table that you are working with, and use only specific data in calculations. FILTER is not used independently, but as a function that is embedded in other functions that require a table as an argument.  
  
## Example  
The following example creates a report of Internet sales outside the United States by using a measure that filters out sales in the United States, and then slicing by calendar year and product categories. To create this measure, you filter the table, Internet Sales USD, by using Sales Territory, and then use the filtered table in a SUMX function.  
  
In this example, the expression `FILTER('InternetSales_USD', RELATED('SalesTerritory'[SalesTerritoryCountry])<>"United States")` returns a table that is a subset of Internet Sales minus all rows that belong to the United States sales territory. The RELATED function is what links the Territory key in the Internet Sales table to SalesTerritoryCountry in the SalesTerritory table.  
  
The following table demonstrates the proof of concept for the measure, NON USA Internet Sales, the formula for which is provided in the code section below. The table compares all Internet sales with non- USA Internet sales, to show that the filter expression works, by excluding United States sales from the computation.  
  
To re-create this table, add the field, SalesTerritoryCountry, to the **Row Labels** area of the PivotTable.  
  
### Table 1. Comparing total sales for U.S. vs. all other regions  
  
|Row Labels|Internet Sales|Non USA Internet Sales|  
|--------------|------------------|--------------------------|  
|Australia|$4,999,021.84|$4,999,021.84|  
|Canada|$1,343,109.10|$1,343,109.10|  
|France|$2,490,944.57|$2,490,944.57|  
|Germany|$2,775,195.60|$2,775,195.60|  
|United Kingdom|$5,057,076.55|$5,057,076.55|  
|United States|$9,389,479.79||  
|Grand Total|$26,054,827.45|$16,665,347.67|  
  
The final report table shows the results when you create a PivotTable by using the measure, NON USA Internet Sales. Add the field, CalendarYear, to the **Row Labels** area of the PivotTable and add the field, ProductCategoryName, to the **Column Labels** area.  
  
### Table 2. Comparing non- U.S. sales by product categories  
  
|Non USA Internet Sales|Column Labels||||  
|--------------------------|-----------------|----|----|----|  
|Row Labels|Accessories|Bikes|Clothing|Grand Total|  
|2005||$1,526,481.95||$1,526,481.95|  
|2006||$3,554,744.04||$3,554,744.04|  
|2007|$156,480.18|$5,640,106.05|$70,142.77|$5,866,729.00|  
|2008|$228,159.45|$5,386,558.19|$102,675.04|$5,717,392.68|  
|Grand Total|$384,639.63|$16,107,890.23|$172,817.81|$16,665,347.67|  
  
```  
SUMX(FILTER('InternetSales_USD', RELATED('SalesTerritory'[SalesTerritoryCountry])<>"United States")  
     ,'InternetSales_USD'[SalesAmount_USD])  
```  
  
## See Also  
[Filter Functions &#40;DAX&#41;](filter-functions-dax.md)  
[ALL Function &#40;DAX&#41;](all-function-dax.md)  
[ALLEXCEPT Function &#40;DAX&#41;](allexcept-function-dax.md)  
  