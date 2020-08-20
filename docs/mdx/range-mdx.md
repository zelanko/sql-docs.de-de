---
description: ': (Bereich) (MDX)'
title: ': (Bereich) (MDX) | Microsoft-Dokumentation'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d52a78a1fcdefa4ee7bf09fa4125b488165e09c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500463"
---
# <a name="-range-mdx"></a>: (Bereich) (MDX)


  Führt eine Mengenoperation aus, die eine natürlich geordnete Menge zurückgibt, wobei die beiden angegebenen Elemente als Endpunkte dienen und alle Elemente zwischen den beiden angegebenen Elementen als Elemente der Menge eingeschlossen werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>Parameter  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Menge, die die angegebenen Elemente und alle Elemente zwischen diesen enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Beide Parameter müssen Elemente in derselben Ebene und Hierarchie einer bestimmten Dimension angeben. Wenn beide Parameter denselben Member angeben, gibt der Operator " **: (Range)** " eine Menge zurück, die nur den angegebenen Member enthält. Wenn der erste Parameter NULL ist, enthält die Menge alle Elemente vom Anfang der Ebene des Elements, das im zweiten Parameter angegeben ist, bis einschließlich jenes Elements. Wenn der zweite Parameter NULL ist, enthält die Menge alle Elemente vom Element, das im ersten Parameter angegeben ist bis einschließlich dem letzten Element derselben Ebene.  
  
 Dieser Mengenoperator weist kein funktionelles Äquivalent in MDX auf.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators.  
  
```  
-- This query returns the freight cost per user  
-- for products, averaged by month, for the first quarter.  
With Member [Measures].[Freight Per Customer] as  
 (  
     [Measures].[Internet Freight Cost]  
     /   
     [Measures].[Customer Count]  
)  
  
SELECT   
    {[Ship Date].[Calendar].[Month].&[2004]&[1] : [Ship Date].[Calendar].[Month].&[2004]&[3]} ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
