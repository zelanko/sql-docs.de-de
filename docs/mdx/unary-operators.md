---
description: Unäre Operatoren
title: Unäre Operatoren | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 391b39dd92011ce43b146d740b232d0c4fca6669
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193480"
---
# <a name="unary-operators"></a>Unäre Operatoren


  In MDX (Multidimensional Expressions) führt ein unärer Operator einen Vorgang für einen einzelnen Operanden aus, z. B. das Zurückgeben eines negativen oder positiven Wertes eines numerischen Ausdrucks.  
  
 MDX unterstützt die unären Operatoren, die in der folgenden Tabelle aufgelistet sind.  
  
|Operator|Beschreibung|  
|--------------|-----------------|  
|[- (Negativ)](../mdx/negative-mdx.md)|Gibt den negativen Wert eines numerischen Ausdrucks zurück.|  
|[+ (Positive) (+ (Positiv))](../mdx/positive-mdx.md)|Gibt den positiven Wert eines numerischen Ausdrucks zurück.|  
  
 Im folgenden Beispiel wird gezeigt, wie ein unärer Operator verwendet wird, um den negativen Wert eines Measures zurückzugeben.  
  
```  
WITH   
   MEMBER [Measures].[NegDiscountAmount] AS  
   -[Measures].[Discount Amount]  
SELECT   
   {[Measures].[Discount Amount],[Measures].[NegDiscountAmount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 Außerdem verwendet MDX spezielle unäre Operatoren, um den Aggregations Vorgang zu bestimmen, der von der [RollupChildren](../mdx/rollupchildren-mdx.md) -Funktion ausgeführt wird. Weitere Informationen zu diesen besonderen unären Operatoren finden [Sie unter Hinzufügen einer benutzerdefinierten Aggregation zu einer Dimension](/analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatoren &#40;MDX-Syntax&#41;](../mdx/operators-mdx-syntax.md)  
  
