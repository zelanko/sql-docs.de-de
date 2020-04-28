---
title: Dimension (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 58bee93a4cef37a8a5a71211b292a16392687f12
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67999959"
---
# <a name="dimension-mdx"></a>Dimension (MDX)


  Gibt die Hierarchie zurück, die ein angegebenes Element, eine angegebene Ebene oder Hierarchie enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.Dimension  
  
Level syntax  
Level_Expression.Dimension  
  
Member syntax  
Member_Expression.Dimension  
  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **Dimensions** Funktion in Verbindung mit der **Name** -Funktion verwendet, um den Hierarchienamen des angegebenen Elements zurückzugeben.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Name  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die Dimension-Funktion in Verbindung mit der Levels- und der Count-Funktion verwendet, um die Anzahl der Ebenen in der Hierarchie zurückzugeben, die das angegebene Element enthalten.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die **Dimensions** Funktion in Verbindung mit den Membern **und** den **count** -Funktionen verwendet, um die Anzahl der Elemente in der Hierarchie zurückzugeben, die das angegebene Element enthält.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#40;Hierarchieebenen&#41; &#40;MDX-&#41;zählen](../mdx/count-hierarchy-levels-mdx.md)   
 [Anzahl &#40;fest geleg&#41; &#40;MDX-&#41;](../mdx/count-set-mdx.md)   
 [Ebenen &#40;MDX-&#41;](../mdx/levels-mdx.md)   
 [Member &#40;&#41; &#40;MDX festgelegt&#41;](../mdx/members-set-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
