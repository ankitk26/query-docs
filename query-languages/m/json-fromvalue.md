---
title: "Json.FromValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2018"
ms.prod: "powerbi"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
ms.assetid: 5b6e9ee5-9ce4-4b9a-86be-eee58f67191f
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "kfile"
---
# Json.FromValue
Json.FromValue(value as any, optional encoding as nullable number) as binary  
  
## About  
Produces a JSON representation of a given value value with a text encoding specified by encoding. If encoding is omitted, UTF8 is used. Values are represented as follows:  
  
|Value|  
|---------|  
|Null, text and logical values are represented as the corresponding JSON types.|  
|Numbers are represented as numbers in JSON, except that #infinity, -#infinity and #nan are converted to null.|  
|Lists are represented as JSON arrays.|  
|Records are represented as JSON objects.|  
|Tables are represented as an array of objects.|  
|Dates, times, datetimes, datetimezones and durations are represented as ISO-8601 text.|  
|Binary values are represented as base-64 encoded text.|  
|Types and functions produce an error.|  
  
### Example 1  
Convert a complex value to JSON.  
  
```  
Text.FromBinary(Json.FromValue([A={1, true, "3"}, B=#date(2012, 3, 25)]))  
```  
  
```  
Equals: "{""A"":[1,true,""3""],""B"":""2012-03-25""}"  
```  