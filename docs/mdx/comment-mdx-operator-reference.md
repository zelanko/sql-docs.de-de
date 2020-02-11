---
title: --(Kommentar) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c848277505dde5fabb10247641ee6b7f955d84e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006285"
---
# <a name="comment---mdx-operator-reference"></a>Kommentar: MDX-Operator Referenz


  Zeigt vom Benutzer bereitgestellten Kommentartext an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Parameter  
 *Comment_Text*  
 Die Zeichenfolge, die den Text des Kommentars enthält.  
  
## <a name="remarks"></a>Bemerkungen  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommentar &#40;MDX-&#41;](../mdx/comment-mdx.md)   
 [&#40;Kommentar&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
