---
title: "List.FirstN | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2018"
ms.prod: "powerbi"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "mlang"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
ms.assetid: b44f7313-e546-4554-b1f1-aa923c2e0d30
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "kfile"
---
# List.FirstN

  
## About  
Returns the first set of items in the list by specifying how many items to return or a qualifying condition provided by **countOrCondition**.  
  
```  
List.FirstN(list as list, countOrCondition as any) as any  
```  
  
## Arguments  
  
|Argument|Description|  
|------------|---------------|  
|list|The List to check.|  
|countOrCondition|The number or condition to qualify against.|  
  
## <a name="__toc360789230"></a>Remarks  
  
-   If a number is specified, up to that many items are returned.  
  
-   If a condition is specified as a function, all items are returned that initially meet the condition.  
  
-   Once an item fails the condition, no further items are considered.  
  
## Examples  
  
```  
List.FirstN({3, 4, 5, -1, 7, 8, 2}, 2) equals {3, 4}  
```  
  
```  
List.FirstN({3, 4, 5, -1 ,7, 8, 2}, each_ > 2) equals {3, 4, 5}  
```  