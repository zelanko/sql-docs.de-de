---
title: LinRegR2 (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 42c703e703e8c557b4de8466a0cd1b686217fd4b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63136204"
---
# <a name="linregr2-mdx"></a>LinRegR2 (MDX)


  Berechnet die lineare Regression einer Menge und gibt den Bestimmungskoeffizienten, R<sup>2</sup>.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LinRegR2(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression_y*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die Y-Achse dar.  
  
 *Numeric_Expression_x*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die X-Achse dar.  
  
## <a name="remarks"></a>Hinweise  
 Die lineare Regression berechnet mit der Methode der kleinsten Quadrate die Gleichung einer Regressionsgeraden (d. h. der Ausgleichsgeraden für eine Reihe von Punkten). Die Regressionszeile hat die folgende Gleichung, in denen eine die Neigung und b ist das Konstante Glied:  
  
 y = ax+b  
  
 Die **LinRegR2** -Funktion wertet den angegebenen Setagainst den ersten numerischen Expressionto die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion die angegebene Menge für den zweiten numerischen Ausdruck, sofern angegeben, aus, um die Werte für die X-Achse zu erhalten. Wenn Sie den zweiten numerischen AusdruckIS nicht angegeben ist, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die x-Achse an. Die X-Axisargument nicht angegeben wird häufig mit der Time-Dimension verwendet.  
  
 Nach dem Abrufen des Satzes von Punkten, die **LinRegR2** Funktionsergebnis ist eine das statistische Koeffizient R<sup>2</sup> , die die Übereinstimmung der linearen Gleichung mit den Punkten beschreibt.  
  
> [!NOTE]  
>  Die **LinRegR2** Funktion ignoriert leere Zellen oder Zellen, die Text oder logische Werte enthalten. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt das statistische Koeffizient R<sup>2</sup> , die die Qualität der Übereinstimmung der linearen Gleichung mit den Punkten für die Unit Sales- und Store sales-Measures beschreibt.  
  
```  
LinRegR2(LastPeriods(10), [Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
