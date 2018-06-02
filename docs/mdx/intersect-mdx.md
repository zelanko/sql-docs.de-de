---
title: Intersect (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7acc509891dd1c975ad819bd904e840e369f0d4b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578522"
---
# <a name="intersect-mdx"></a>Intersect (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Hinweise  
 Die **Intersect** Funktion gibt die Schnittmenge zweier Mengen zurück. Doppelte Werte werden von der Funktion standardmäßig aus den beiden Mengen entfernt, bevor die Schnittmenge gebildet wird. Die beiden angegebenen Mengen müssen dieselbe Dimensionalität haben.  
  
 Das optionale **alle** Flag werden doppelte Werte beibehalten. Wenn **alle** angegeben wird, die **Intersect** Funktion Schnittmenge Elemente wie gewohnt überschneidet, und jeder doppelte Wert in der ersten Menge, die über einen übereinstimmenden doppelten in der zweiten Menge verfügt auch überschneidet. Die beiden angegebenen Mengen müssen dieselbe Dimensionalität haben.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
