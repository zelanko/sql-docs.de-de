---
description: SetToArray (MDX)
title: Setto Array (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f5b0c4b39761e25065b2c262943b4ce335fccf6e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386976"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **setto Array** -Funktion konvertiert eine oder mehrere Mengen in ein Array zur Verwendung in einer benutzerdefinierten Funktion. Die Anzahl der Dimensionen in dem sich ergebenden Array ist dieselbe wie die Anzahl der angegebenen Mengen.  
  
 Durch die optionale Angabe eines numerischen Ausdrucks können die Werte für die Arrayzellen bereitgestellt werden. Wenn kein numerischer Ausdruck angegeben ist, wird der Cross Join der Mengen im aktuellen Kontext ausgewertet.  
  
 Die Zellenkoordinaten in dem sich ergebenden Array entsprechen der Position der Mengen in der Liste. Beispielsweise sind drei Mengen, `SA`, `SB` und `SC`, vorhanden. Jede dieser Mengen weist zwei Elemente auf. Die MDX-Anweisung `SetToArray(SA, SB, SC)` erstellt das folgende dreidimensionale Array:  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  Der Rückgabetyp der **setdearray** -Funktion ist der Variant-Typ, VT_ARRAY. Daher sollte die Ausgabe der **setdearray** -Funktion nur als Eingabe für eine benutzerdefinierte Funktion verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Array zurückgegeben.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
