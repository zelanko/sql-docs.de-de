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
ms.openlocfilehash: 2f03c3152e3144b137c079cbdfddeff5b9cd5156
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008176"
---
# <a name="operators-dmx"></a>Operatoren (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Mithilfe von DMX (Data Mining Extensions)-Operatoren können arithmetische, Vergleichs-, Verkettungs-und logische Operationen in einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Abfrage in durchgeführt werden.  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden Operatoren zum Ausführen folgender Aktionen verwendet:  
  
-   Suchen nach Werten oder Objekten, die mit einer bestimmten Bedingung übereinstimmen.  
  
-   Implementieren einer Entscheidung zwischen Werten oder Ausdrücken.  
  
 In DMX werden Operatoren aus verschiedenen Kategorien verwendet, die in den folgenden Abschnitten beschrieben sind. Weitere Informationen zu einzelnen Operatoren finden Sie unter [Data Mining Extensions &#40;DMX&#41; Operator Reference](../dmx/data-mining-extensions-dmx-operator-reference.md).  
  
|Operatorkategorie|Typ des Vorgangs|  
|-----------------------|-----------------------|  
|[Arithmetische Operatoren &#40;DMX-&#41;](../dmx/operators-arithmetic.md)|Ausführen einer Addition, Subtraktion, Multiplikation oder Division.|  
|[Vergleichs Operatoren &#40;DMX-&#41;](../dmx/operators-comparison.md)|Vergleicht einen Wert mit einem anderen Wert oder einem Ausdruck.|  
|[Logische Operatoren &#40;DMX-&#41;](../dmx/operators-logical.md)|Testen, ob eine Bedingung wahr ist (z. B. AND, OR oder NOT).|  
|[Unäre Operatoren &#40;DMX-&#41;](../dmx/operators-unary.md)|Ausführen einer Operation für einen einzelnen Operanden.|  
  
 Mit Operatoren können Sie kleinere Ausdrücke in DMX zu komplexeren Ausdrücken kombinieren. In solchen komplexen Ausdrücken werden die Operatoren in Abhängigkeit von der in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] definierten Operatorenrangfolge ausgewertet. Operatoren mit höherer Rangfolge werden vor Operatoren mit niedrigerer Rangfolge ausgeführt. Weitere Informationen zu Ausdrücken finden Sie unter [Ausdrücke &#40;DMX-&#41;](../dmx/expressions-dmx.md).  
  
 Wenn Sie einfache Ausdrücke zu einem komplexen Ausdruck kombinieren, wird der Datentyp des sich ergebenden Ausdrucks durch Kombinieren der Regeln für die Operatoren mit den Regeln für die Rangfolge der Datentypen bestimmt. Wenn das Ergebnis ein Zeichen oder ein Unicode-Wert ist, bestimmt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Sortierung des Ergebnisses durch Kombinieren der Regeln für die Operatoren mit den Regeln für die Sortierungsrangfolge. Außerdem gibt es Regeln, mit denen die Genauigkeit, die Dezimalstellen und die Länge des Ergebnisses basierend auf der Genauigkeit, der Skala und der Länge der einfachen Ausdrücke bestimmt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersage Abfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Grundlegendes zur SELECT-Anweisung (DMX)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
