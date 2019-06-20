---
title: Operatoren (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 072d0a36a4803f4de1d50ba066e4e86e5d171c5c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62502051"
---
# <a name="operators-dmx"></a>Operatoren (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Können Sie zum Ausführen von Arithmetik, Vergleich, Verkettung und logischen Operationen in einer Abfrage im Data Mining Extensions (DMX)-Operatoren [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden Operatoren zum Ausführen folgender Aktionen verwendet:  
  
-   Suchen nach Werten oder Objekten, die mit einer bestimmten Bedingung übereinstimmen.  
  
-   Implementieren einer Entscheidung zwischen Werten oder Ausdrücken.  
  
 In DMX werden Operatoren aus verschiedenen Kategorien verwendet, die in den folgenden Abschnitten beschrieben sind. Weitere Informationen zu einzelnen Operatoren finden Sie unter [Data Mining-Erweiterungen &#40;DMX&#41; -Operatorreferenz](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
|Operatorkategorie|Typ der Operation|  
|-----------------------|-----------------------|  
|[Arithmetische Operatoren &#40;DMX&#41;](../dmx/operators-arithmetic.md)|Ausführen einer Addition, Subtraktion, Multiplikation oder Division.|  
|[Vergleichsoperatoren &#40;DMX&#41;](../dmx/operators-comparison.md)|Vergleichen Sie einen Wert mit einem anderen Wert oder einen Ausdruck ein.|  
|[Logische Operatoren &#40;DMX&#41;](../dmx/operators-logical.md)|Testen, ob eine Bedingung wahr ist (z. B. AND, OR oder NOT).|  
|[Unäre Operatoren &#40;DMX&#41;](../dmx/operators-unary.md)|Ausführen einer Operation für einen einzelnen Operanden.|  
  
 Mit Operatoren können Sie kleinere Ausdrücke in DMX zu komplexeren Ausdrücken kombinieren. In solchen komplexen Ausdrücken werden die Operatoren in Abhängigkeit von der in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] definierten Operatorenrangfolge ausgewertet. Operatoren mit höherer Rangfolge werden vor Operatoren mit niedrigerer Rangfolge ausgeführt. Weitere Informationen zu Ausdrücken finden Sie unter [Ausdrücke &#40;DMX&#41;](../dmx/expressions-dmx.md).  
  
 Wenn Sie einfache Ausdrücke zu einem komplexen Ausdruck kombinieren, wird der Datentyp des sich ergebenden Ausdrucks durch Kombinieren der Regeln für die Operatoren mit den Regeln für die Rangfolge der Datentypen bestimmt. Wenn das Ergebnis ein Zeichen oder ein Unicode-Wert ist, bestimmt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Sortierung des Ergebnisses durch Kombinieren der Regeln für die Operatoren mit den Regeln für die Sortierungsrangfolge. Außerdem sind Regeln, die bestimmen, die Genauigkeit, Dezimalstellen und Länge des Ergebnisses basierend auf der Genauigkeit, Dezimalstellen und Länge der einfachen Ausdrücke vorhanden.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
