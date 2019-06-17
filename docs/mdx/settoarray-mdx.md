---
title: SetToArray (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e545cb4b41f1a0d60e471c15753a82079978ee5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149301"
---
# <a name="settoarray-mdx"></a>SetToArray (MDX)


  Konvertiert eine Menge oder mehrere Mengen in ein Array zum Verwenden in einer benutzerdefinierten Funktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **SetToArray** -Funktion konvertiert eine oder mehrere Mengen in ein Array zur Verwendung in einer benutzerdefinierten Funktion. Die Anzahl der Dimensionen in dem sich ergebenden Array ist dieselbe wie die Anzahl der angegebenen Mengen.  
  
 Durch die optionale Angabe eines numerischen Ausdrucks können die Werte für die Arrayzellen bereitgestellt werden. Wenn kein numerischer Ausdruck angegeben ist, wird der Cross Join der Mengen im aktuellen Kontext ausgewertet.  
  
 Die Zellenkoordinaten in dem sich ergebenden Array entsprechen der Position der Mengen in der Liste. Beispielsweise sind drei Mengen, `SA`, `SB` und `SC`, vorhanden. Jede dieser Mengen weist zwei Elemente auf. Die MDX-Anweisung `SetToArray(SA, SB, SC)` erstellt das folgende dreidimensionale Array:  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  Der Rückgabetyp der **SetToArray** -Funktion ist der VARIANT-Typ VT_ARRAY. Aus diesem Grund die Ausgabe der **SetToArray** Funktion sollte nur als Eingabe für eine benutzerdefinierte Funktion verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Array zurückgegeben.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
