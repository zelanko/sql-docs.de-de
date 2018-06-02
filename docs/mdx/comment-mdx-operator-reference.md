---
title: --(Kommentar) (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 564327619cabc00684b064585aa323c9426597c2
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577372"
---
# <a name="comment---mdx-operator-reference"></a>Comment - MDX-Operatorreferenz
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Zeigt vom Benutzer bereitgestellten Kommentartext an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Parameter  
 *Comment_Text*  
 Die Zeichenfolge, die den Text des Kommentars enthält.  
  
## <a name="remarks"></a>Hinweise  
 Kommentare können in einer eigenen Zeile, geschachtelt am Ende einer MDX-Skriptzeile (Multidimensional Expressions) oder geschachtelt in einer MDX-Anweisung eingefügt werden. Der Kommentar wird vom Server nicht ausgewertet.  
  
 Verwenden Sie diesen Operator für einzeilige oder geschachtelte Kommentare. Kommentare, die mit -- eingefügt werden, sind vom Zeilenschaltzeichen begrenzt.  
  
 Es gibt keine Maximallänge für Kommentare.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators.  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Kommentar &#40;MDX&#41;](../mdx/comment-mdx.md)   
 [&#40;Kommentar&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
