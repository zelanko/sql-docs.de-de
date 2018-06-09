---
title: NonEmptyCrossjoin (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7da56ac658f57d6eb664762f9dd94351df39fe0f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742649"
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)


  Gibt eine Menge zurück, die das Kreuzprodukt mindestens einer Menge enthält, wobei leere Tupel und Tupel ohne zugeordnete Daten einer Faktentabelle ausgeschlossen werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Anzahl*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der zurückzugebenden Mengen angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **NonEmptyCrossjoin** Funktion gibt das Kreuzprodukt zweier oder mehrerer Mengen als eine Menge mit Ausnahme von leeren Tupeln oder Tupel ohne Daten, die vom zugrunde liegenden Faktentabellen bereitgestellt. Aufgrund der **NonEmptyCrossjoin** -Funktion vorgeht, alle berechneten Elemente automatisch ausgeschlossen.  
  
 Wenn *Anzahl* nicht angegeben wird, die Funktion den cross Join aller angegebenen Mengen und schließt leere Elemente aus der Ergebnismenge aus. Wenn die Anzahl der Mengen angegeben wird, bildet die Funktion den Cross Join der angegebenen Anzahl von Mengen, beginnend mit der ersten angegebenen Menge. Die **NonEmptyCrossjoin** Funktion anhand aller verbleibenden Mengen, die in weiteren angegebenen Mengen angegeben sind, jedoch die noch nicht Cross verknüpft, um zu bestimmen, welche Member in der Ergebnismenge des cross nicht leeren berücksichtigt werden. Die **NonEmptyCrossjoin** -Funktion berücksichtigt die **NON_EMPTY_BEHAVIOR** -Einstellung von berechneten Measures.  
  
> [!IMPORTANT]  
>  Diese Funktion ist veraltet, und Sie sollten sie nicht verwenden; sie wird nur beibehalten, um die Abwärtskompatibilität aufrechtzuerhalten. Stattdessen sollten Sie verwenden die [Exists (MDX)](../mdx/exists-mdx.md) -Funktion mit dem Measuregruppennamen-Argument oder die [NonEmpty (MDX)](../mdx/nonempty-mdx.md) Funktion.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
