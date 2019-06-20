---
title: BottomPercent (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a627ea8e5dd7a8f8266fcf0ea374e6abcde4bdc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208799"
---
# <a name="bottompercent-mdx"></a>BottomPercent (MDX)


  Sortiert eine Menge in aufsteigender Reihenfolge und gibt eine Menge von Tupeln mit den niedrigsten Werten zurück, deren kumulativer Gesamtwert größer oder gleich einem angegebenen Prozentsatz ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Prozentwert*  
 Ein gültiger numerischer Ausdruck, der den Prozentsatz der zurückzugebenden Tupel angibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **BottomPercent** -Funktion berechnet die Summe der angegebenen numerischen Ausdrucks, ausgewertet über einer angegebenen Menge, die Menge in aufsteigender Reihenfolge sortieren. Anschließend gibt die Funktion die Elemente mit den niedrigsten Werten zurück, deren kumulativer Prozentsatz des Gesamtwertes mindestens dem angegebenen Prozentsatz entspricht. Diese Funktion gibt die kleinste Teilmenge einer Menge zurück, deren kumulativer Gesamtwert mindestens dem angegebenen Prozentsatz entspricht. Die zurückgegebenen Elemente werden der Größe nach absteigend sortiert.  
  
> [!IMPORTANT]  
>  Die **BottomPercent** ordnungsgemäß verwendet werden, wie z. B. die [TopPercent](../mdx/toppercent-mdx.md) funktionieren, immer die Hierarchie unterbrochen. Weitere Informationen finden Sie unter Order-Funktion.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird für die Bike-Kategorie die kleinste Menge der Elemente der City-Ebene in der Geography-Hierarchie in der Geography-Dimension für das Geschäftsjahr 2003 zurückgegeben, deren kumulativer Gesamtwert bezüglich des Reseller Sales Amount-Measures mindestens 15 % des kumulativen Gesamtwertes (beginnend mit den Elementen dieser Menge, die den geringsten Umsatz aufweisen) beträgt.  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
