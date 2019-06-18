---
title: IsGeneration (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a726470f89f2d3ea1677259e849735a09909a42d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62629413"
---
# <a name="isgeneration-mdx"></a>IsGeneration (MDX)


  Gibt zurück, ob sich ein angegebenes Element in einer angegebenen Generation befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsGeneration(Member_Expression, Generation_Number)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Generation_Number*  
 Ein gültiger numerischer Ausdruck, der die Generierung angibt, für die das angegebene Element ausgewertet wird.  
  
## <a name="remarks"></a>Hinweise  
 Die **IsGeneration** -Funktion zurückgegeben **"true"** , wenn das angegebene Element in der angegebenen Generierungsnummer befindet. Die Funktion hingegen gibt **"false"** . Auch wenn das angegebene Element zu einem leeren Element ausgewertet wird die **IsGeneration** -Funktion zurückgegeben **"false"** .  
  
 Für die Zwecke der Generierungsindizierung haben Blattelemente den Generierungsindex 0. Der Generationsindex von Nichtblattelementen wird bestimmt, indem zuerst der höchste Generationsindex aus der Vereinigung aller untergeordneten Elemente des angegebenen Elements abgerufen wird und dann 1 zu diesem Index addiert wird. Aufgrund der Bestimmungsweise des Generationsindexes von Nichtblattelementen kann es vorkommen, dass ein bestimmtes Nichtblattelement mehreren Generationen angehört.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird TRUE zurückgegeben, wenn [Date].[Fiscal].CurrentMember Teil der zweiten Generierung ist:  
  
 `WITH MEMBER MEASURES.ISGENERATIONDEMO AS`  
  
 `IsGeneration([Date].[Fiscal].CURRENTMEMBER, 2)`  
  
 `SELECT {MEASURES.ISGENERATIONDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
