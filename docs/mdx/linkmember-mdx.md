---
title: LinkMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8a00388e067878d9c2165cbae6844f8020b7c63e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905601"
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
 Die **LinkMember** -Funktion gibt das Element aus der angegebenen Hierarchie zurück, das den Schlüsselwerten auf jeder Ebene des angegebenen Elements in einer zugehörigen Hierarchie entspricht. Die Attribute auf jeder Ebene müssen die gleiche Schlüsselkardinalität und den gleichen Datentyp aufweisen. Wenn es bei unnatürlichen Hierarchien mehr als eine Entsprechung für den Schlüsselwert eines Attributs gibt, ist das Resultat ein Fehler oder unbestimmt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **LinkMember** -Funktion verwendet, um das Standardmeasure im Adventure Works-Cube für die Vorgänger des 1. Juli 2002-Members der Date. Date-Attribut Hierarchie in der Calendar-Hierarchie zurückzugeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Hierarchize &#40;MDX-&#41;](../mdx/hierarchize-mdx.md)   
 [Vorgänger &#40;MDX-&#41;](../mdx/ascendants-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
