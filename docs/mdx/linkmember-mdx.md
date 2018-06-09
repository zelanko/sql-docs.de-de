---
title: LinkMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 71235953f592572bd7ac0dcb2493d97dd509f8b7
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741499"
---
# <a name="linkmember-mdx"></a>LinkMember (MDX)


  Gibt das Element zurück, das in einer angegebenen Hierarchie gleichbedeutend mit dem angegebenen Element ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **LinkMember** Funktion gibt das Element zurück, aus der angegebenen Hierarchie, die die Schlüsselwerte auf jeder Ebene des angegebenen Elements in einer zugehörigen Hierarchie entspricht. Die Attribute auf jeder Ebene müssen die gleiche Schlüsselkardinalität und den gleichen Datentyp aufweisen. Wenn es bei unnatürlichen Hierarchien mehr als eine Entsprechung für den Schlüsselwert eines Attributs gibt, ist das Resultat ein Fehler oder unbestimmt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **LinkMember** Funktion, um das Standardmeasure im Adventure Works-Cube für die Vorgänger des July 1, 2002-Elements der Date.Date-Attributhierarchie in der Calendar-Hierarchie zurückzugeben.  
  
```  
SELECT  Hierarchize  
   (Ascendants   
      (LinkMember   
         ([Date].[Date].[July 1, 2002], [Date].[Calendar]  
         )  
       )  
    ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [HIERARCHIZE &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [ASCENDANTS &#40;MDX&#41;](../mdx/ascendants-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
