---
title: Intersect (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f253dad526c509edff5c837b61ae2faae07d5758
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105358"
---
# <a name="intersect-mdx"></a>Intersect (MDX)


  Gibt die Schnittmenge zweier Eingabesets zurück. Optional werden doppelte Werte beibehalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Intersect(Set_Expression1 , Set_Expression2 [ , ALL ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Intersect** -Funktion gibt die Schnittmenge zweier Mengen zurück. Doppelte Werte werden von der Funktion standardmäßig aus den beiden Mengen entfernt, bevor die Schnittmenge gebildet wird. Die beiden angegebenen Mengen müssen dieselbe Dimensionalität haben.  
  
 Das optionale **all** -Flag behält Duplikate bei. Wenn **all** angegeben wird, interschneidet die **Intersect** -Funktion nicht duplizierte Elemente wie üblich und schneidet auch jedes Duplikat in der ersten Menge mit einem übereinstimmenden Duplikat in der zweiten Menge ab. Die beiden angegebenen Mengen müssen dieselbe Dimensionalität haben.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage gibt die Jahre 2003 und 2004 zurück, die beiden Elemente, die in beiden angegebenen Mengen vorhanden sind:  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001], [Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003]}`  
  
 `, {[Date].[Calendar Year].&[2002],[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Die folgende Abfrage schlägt fehl, da die beiden angegebenen Mengen Elemente aus verschiedenen Hierarchien enthalten:  
  
 `SELECT`  
  
 `INTERSECT(`  
  
 `{[Date].[Calendar Year].&[2001]}`  
  
 `, {[Customer].[City].&[Abingdon]&[ENG]})`  
  
 `ON 0`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
