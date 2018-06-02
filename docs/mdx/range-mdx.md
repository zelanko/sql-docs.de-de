---
title: ': (Bereich) (MDX) | Microsoft Docs'
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 152158128a58cc2df12c0975b9c00976800fe64d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581192"
---
# <a name="-range-mdx"></a>: (Bereich) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Hinweise  
 Beide Parameter müssen Elemente in derselben Ebene und Hierarchie einer bestimmten Dimension angeben. Wenn beide Parameter dasselbe Element an, geben Sie die **: (Bereich)** -Operator eine Menge zurück, die nur das angegebene Element enthält. Wenn der erste Parameter NULL ist, enthält die Menge alle Elemente vom Anfang der Ebene des Elements, das im zweiten Parameter angegeben ist, bis einschließlich jenes Elements. Wenn der zweite Parameter NULL ist, enthält die Menge alle Elemente vom Element, das im ersten Parameter angegeben ist bis einschließlich dem letzten Element derselben Ebene.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
