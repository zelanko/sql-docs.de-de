---
description: Current (MDX)
title: Current (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 105bb306cb84f151024a288f5aa15eb09ddbf5c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387546"
---
# <a name="current-mdx"></a>Current (MDX)


  Gibt das aktuelle Tupel in einer Menge während einer Iteration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression.Current   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei jedem Schritt einer Iteration ist das gerade bearbeitete Tupel das aktuelle Tupel. Die **aktuelle** Funktion gibt dieses Tupel zurück. Diese Funktion ist nur während einer Iteration über eine Menge gültig.  
  
 MDX-Funktionen, die eine Menge durchlaufen, enthalten die [Generate](../mdx/generate-mdx.md) -Funktion.  
  
> [!NOTE]  
>  Diese Funktion ist nur mit benannten Mengen ausführbar, d. h. beim Verwenden eines Mengen-Alias oder Definieren einer benannten Menge.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie die **aktuelle** Funktion in **Generate**verwendet wird:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of all Calendar Years crossjoined with`  
  
 `//all Product Categories`  
  
 `SET MyTuples AS CROSSJOIN(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `//Iterates through each tuple in the set and returns the name of the Calendar`  
  
 `//Year in each tuple`  
  
 `MEMBER MEASURES.CURRENTDEMO AS`  
  
 `GENERATE(MyTuples, MyTuples.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
