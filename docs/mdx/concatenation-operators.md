---
title: Verkettungsoperatoren | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a59ba79a2ba6cde723b79bb459734e7a8b5d752a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578432"
---
# <a name="concatenation-operators"></a>Operator für Verkettungen
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Der Operator für Verkettungen ist das Pluszeichen (+). Sie können zwei oder mehr Zeichenfolgen zu einer einzelnen Zeichenfolge kombinieren oder verketten. Sie können auch binäre Zeichenfolgen verketten.  
  
 Der folgende Code ist ein Beispiel für den Operator für Verkettungen, der hier den Produktnamen mit dem eindeutigen Namen des Produkts kombiniert.  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>Sprachbezogene Aspekte  
 Haben die beiden in einer Verkettung verwendeten Zeichenfolgen dieselbe Sortierung, hat die sich ergebende verkettete Zeichenfolge dieselbe Sortierung wie die Eingaben. Haben die in einer Verkettung verwendeten Zeichenfolgen unterschiedliche Sortierungen, wird die Sortierung der sich ergebenden verketteten Zeichenfolge durch die Regeln für die Sortierungsrangfolge bestimmt. Weitere Informationen finden Sie unter [Sprachen und Sortierungen &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatoren &#40;MDX-Syntax&#41;](../mdx/operators-mdx-syntax.md)  
  
  
