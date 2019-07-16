---
title: Rang (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1081cacd0676f4eb0512780e9ddc7641edb99ca1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037071"
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
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Ausdruck angegeben wird, die **Rang** -Funktion bestimmt den einsbasierten Rang für das angegebene Tupel, indem der angegebene numerische Ausdruck für das Tupel ausgewertet. Wenn ein numerischer Ausdruck angegeben wird, die **Rang** -Funktion Tupeln mit doppelten Werten in der Menge denselben Rang zugewiesen. Die Zuweisung desselben Ranges an doppelte Werte wirkt sich auf die Rangwerte nachfolgender Tupel in der Menge aus. Eine Menge besteht beispielsweise aus folgenden Tupeln: `{(a,b), (e,f), (c,d)}`. Das Tupel `(a,b)` weist denselben Wert auf wie das Tupel `(c,d)`. Wenn das Tupel `(a,b)` den Rang "1" aufweist, liegt für `(a,b)` und `(c,d)` der Rang "1" vor. Das Tupel `(e,f)` verfügt jedoch über den Rang "3". In diesem Satz kann kein Tupel mit dem Rang "2" vorhanden sein.  
  
 Wenn ein numerischer Ausdruck nicht angegeben wird, die **Rang** Funktion gibt die einsbasierte Ordnungsposition des angegebenen Tupels zurück.  
  
 Die **Rang** -Funktion sortiert die Menge nicht.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt die Menge der Tupel, die mit von Kunden und Kaufdaten mithilfe der **Filter**, **NonEmpty**, **Element**, und **Rang** Funktionen, um das Datum der letzten feststellen, dass es sich bei jeder Kunde einen Einkauf getätigt haben.  
  
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
  
 Im folgenden Beispiel wird die **Reihenfolge** -Funktion, statt auf den **Rang** -Funktion verwendet, um die Elemente der City-Hierarchie Rangfolge basierend auf dem Reseller Sales Amount-Measure und klicken Sie dann in der Rangreihenfolge angezeigt. Mithilfe der **Reihenfolge** -Funktion zum vorsortieren der Menge der Elemente der City-Hierarchie, die Sortierung nur einmal durchgeführt und anschließend ein linearer Scan vor der Anzeige der Sortierreihenfolge.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Reihenfolge &#40;MDX&#41;](../mdx/order-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
