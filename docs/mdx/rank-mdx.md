---
description: Rank (MDX)
title: Rank (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 391ba9d805684a9fd469d8e6c66727caba71ce70
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341336"
---
# <a name="rank-mdx"></a>Rank (MDX)


  Gibt den einsbasierten Rang eines angegebenen Tupels in einer angegebenen Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Rank(Tuple_Expression, Set_Expression [ ,Numeric Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein numerischer Ausdruck angegeben wird, bestimmt die **Rang** Funktion den 1-basierten Rang für das angegebene Tupel, indem der angegebene numerische Ausdruck für das Tupel ausgewertet wird. Wenn ein numerischer Ausdruck angegeben wird, weist die **Rank** -Funktion den gleichen Rang Tupeln mit doppelten Werten im Satz zu. Die Zuweisung desselben Ranges an doppelte Werte wirkt sich auf die Rangwerte nachfolgender Tupel in der Menge aus. Eine Menge besteht beispielsweise aus folgenden Tupeln: `{(a,b), (e,f), (c,d)}`. Das Tupel `(a,b)` weist denselben Wert auf wie das Tupel `(c,d)`. Wenn das Tupel `(a,b)` den Rang "1" aufweist, liegt für `(a,b)` und `(c,d)` der Rang "1" vor. Das Tupel `(e,f)` verfügt jedoch über den Rang "3". In diesem Satz kann kein Tupel mit dem Rang "2" vorhanden sein.  
  
 Wenn kein numerischer Ausdruck angegeben wird, gibt die **Rank** -Funktion die einsbasierte Ordinalposition des angegebenen Tupels zurück.  
  
 Die **Rank** -Funktion sortiert die Menge nicht.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Satz von Tupeln mit Kunden und Kauf Daten mithilfe der **Filter**-, **NonEmpty**-, **Item**-und **Rank** -Funktionen zurückgegeben, um das letzte Datum zu ermitteln, an dem die einzelnen Kunden einen Kauf getätigt haben.  
  
```  
WITH SET MYROWS AS FILTER  
   (NONEMPTY  
      ([Customer].[Customer Geography].MEMBERS  
         * [Date].[Date].[Date].MEMBERS  
         , [Measures].[Internet Sales Amount]  
      ) AS MYSET  
   , NOT(MYSET.CURRENT.ITEM(0)  
      IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))  
   )  
SELECT [Measures].[Internet Sales Amount] ON 0,  
MYROWS ON 1  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die **Order** -Funktion anstelle der **Rang** Funktion verwendet, um die Elemente der City-Hierarchie basierend auf dem Reseller Sales Amount-Measure zu ordnen und Sie dann in der Reihenfolge der Rangfolge anzeigt. Wenn Sie die **Order** -Funktion verwenden, um die Menge der Elemente der City-Hierarchie zuerst zu sortieren, erfolgt die Sortierung nur ein Mal und anschließend eine lineare Überprüfung, bevor Sie in sortierter Reihenfolge dargestellt werden.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Order &#40;MDX-&#41;](../mdx/order-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
