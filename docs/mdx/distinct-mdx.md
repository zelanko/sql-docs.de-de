---
description: Distinct (MDX)
title: Verschieden (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6d3139623d0eca7986f6bcef1d27a3475b5f371a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491427"
---
# <a name="distinct-mdx"></a>Distinct (MDX)


  Wertet eine angegebene Menge aus, entfernt doppelte Tupel aus der Menge und gibt die resultierende Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Distinct(Set_Expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die unter **schiedliche** Funktion doppelte Tupel in der angegebenen Menge findet, behält die Funktion nur die erste Instanz des doppelten Tupels bei, wobei die Reihenfolge der Gruppe intakt bleibt.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Beispielabfrage zeigt die Verwendung der Distinct-Funktion mit einer benannten Menge, sowie mit der Count-Funktion, um die Anzahl verschiedener Tupel in einer Menge zu finden:  
  
 `WITH SET MySet AS`  
  
 `{[Customer].[Customer Geography].[Country].&[Australia],[Customer].[Customer Geography].[Country].&[Australia],`  
  
 `[Customer].[Customer Geography].[Country].&[Canada],[Customer].[Customer Geography].[Country].&[France],`  
  
 `[Customer].[Customer Geography].[Country].&[United Kingdom],[Customer].[Customer Geography].[Country].&[United Kingdom]}`  
  
 `MEMBER MEASURES.SETCOUNT AS`  
  
 `COUNT(MySet)`  
  
 `MEMBER MEASURES.SETDISTINCTCOUNT AS`  
  
 `COUNT(DISTINCT(MySet))`  
  
 `SELECT {MEASURES.SETCOUNT, MEASURES.SETDISTINCTCOUNT} ON 0,`  
  
 `DISTINCT(MySet) ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
