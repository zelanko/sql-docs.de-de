---
description: IsGeneration (MDX)
title: Isgene ration (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e7b7f3df41af6af51a826352814fc6aef52ef0a0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471832"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **IsGeneration** -Funktion gibt **true** zurück, wenn das angegebene Element in der angegebenen Generierungs Nummer ist. Andernfalls gibt die Funktion **false**zurück. Wenn das angegebene Element zu einem leeren Member ausgewertet wird, gibt die **IsGeneration** -Funktion **false**zurück.  
  
 Für die Zwecke der Generierungsindizierung haben Blattelemente den Generierungsindex 0. Der Generationsindex von Nichtblattelementen wird bestimmt, indem zuerst der höchste Generationsindex aus der Vereinigung aller untergeordneten Elemente des angegebenen Elements abgerufen wird und dann 1 zu diesem Index addiert wird. Aufgrund der Bestimmungsweise des Generationsindexes von Nichtblattelementen kann es vorkommen, dass ein bestimmtes Nichtblattelement mehreren Generationen angehört.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird TRUE zurückgegeben, wenn [Date].[Fiscal].CurrentMember Teil der zweiten Generierung ist:  
  
 `WITH MEMBER MEASURES.ISGENERATIONDEMO AS`  
  
 `IsGeneration([Date].[Fiscal].CURRENTMEMBER, 2)`  
  
 `SELECT {MEASURES.ISGENERATIONDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
