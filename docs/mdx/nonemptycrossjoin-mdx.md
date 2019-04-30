---
title: NonEmptyCrossjoin (MDX) | Microsoft-Dokumentation
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
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63456564"
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
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der zurückzugebenden Mengen angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **NonEmptyCrossjoin** Funktion gibt das Kreuzprodukt von zwei oder mehr Mengen als eine Menge mit Ausnahme von leeren Tupeln oder Tupel ohne Daten, die vom zugrunde liegenden Faktentabellen bereitgestellt. Aufgrund der wie die **NonEmptyCrossjoin** -Funktion vorgeht, alle berechneten Elemente automatisch ausgeschlossen.  
  
 Wenn *Anzahl* nicht angegeben ist, die Funktion den cross Join aller angegebenen Mengen und schließt leere Elemente aus der Ergebnismenge. Wenn die Anzahl der Mengen angegeben wird, bildet die Funktion den Cross Join der angegebenen Anzahl von Mengen, beginnend mit der ersten angegebenen Menge. Die **NonEmptyCrossjoin** Funktion anhand aller verbleibenden Mengen, die, die in weiteren angegebenen Mengen angegeben sind, jedoch die noch nicht Cross verknüpft werden, um zu bestimmen, welche Member in der Ergebnismenge des cross Joins nicht leeren betrachtet werden. Die **NonEmptyCrossjoin** -Funktion berücksichtigt die **NON_EMPTY_BEHAVIOR** -Einstellung von berechneten Measures.  
  
> [!IMPORTANT]  
>  Diese Funktion ist veraltet, und Sie sollten sie nicht verwenden; sie wird nur beibehalten, um die Abwärtskompatibilität aufrechtzuerhalten. Sie sollten stattdessen die [Exists (MDX)](../mdx/exists-mdx.md) -Funktion mit dem Measuregruppennamen-Argument oder die [NonEmpty (MDX)](../mdx/nonempty-mdx.md) Funktion.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
