---
title: / / (Kommentar) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6eb4b54df98cfbf297e6347dac336aa7405d1347
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006294"
---
# <a name="comment-mdx-double-slash"></a>Kommentar MDX doppelten Schrägstrich


  Gibt vom Benutzer bereitgestellten Text an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Parameter  
 *Comment_Text*  
 Die Zeichenfolge, die den Text des Kommentars enthält.  
  
## <a name="remarks"></a>Hinweise  
 Kommentare können in einer eigenen Zeile, geschachtelt am Ende einer MDX-Skriptzeile (Multidimensional Expressions) oder geschachtelt in einer MDX-Anweisung eingefügt werden. Der Kommentar wird vom Server nicht ausgewertet.  
  
 Verwenden Sie // nur für einzeilige Kommentare. Kommentare, die mit // eingefügt werden, sind durch das Neue-Zeile-Zeichen begrenzt.  
  
 Es gibt keine Maximallänge für Kommentare.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators.  
  
```  
// This member returns the gross profit margin for product types  
// and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM // Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Kommentar &#40;MDX&#41;](../mdx/comment-mdx.md)   
 [-- &#40;Kommentar&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)   
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
