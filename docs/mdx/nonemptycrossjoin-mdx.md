---
description: NonEmptyCrossjoin (MDX)
title: NonEmptyCrossjoin (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6fafaad2f6fa0f46d826bf94b26ceb6fdbe9df55
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471802"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **NonEmptyCrossjoin** -Funktion gibt das Kreuz Produkt zweier oder mehrerer Mengen als eine Menge zurück, wobei leere Tupel oder Tupel ohne Daten, die von den zugrunde liegenden Fakten Tabellen bereitgestellt werden, ausgeschlossen werden. Aufgrund der Funktionsweise der **NonEmptyCrossjoin** -Funktion werden alle berechneten Elemente automatisch ausgeschlossen.  
  
 Wenn *count* nicht angegeben wird, führt die Funktion Cross Joins für alle angegebenen Mengen durch und schließt leere Elemente aus der resultierenden Menge aus. Wenn die Anzahl der Mengen angegeben wird, bildet die Funktion den Cross Join der angegebenen Anzahl von Mengen, beginnend mit der ersten angegebenen Menge. Die **NonEmptyCrossjoin** -Funktion verwendet alle verbleibenden Mengen, die in nachfolgenden festgelegten Mengen angegeben sind, jedoch nicht quer verknüpft wurden, um zu bestimmen, welche Member in der resultierenden Kreuz verknüpften Gruppe als nicht leer betrachtet werden. Die **NonEmptyCrossjoin** -Funktion respektiert die **NON_EMPTY_BEHAVIOR** Einstellung berechneter Measures.  
  
> [!IMPORTANT]  
>  Diese Funktion ist veraltet, und Sie sollten sie nicht verwenden; sie wird nur beibehalten, um die Abwärtskompatibilität aufrechtzuerhalten. Stattdessen sollten Sie die [vorhanden (MDX)](../mdx/exists-mdx.md) -Funktion mit dem Measure Group Name-Argument oder der [NonEmpty (MDX)](../mdx/nonempty-mdx.md) -Funktion verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
