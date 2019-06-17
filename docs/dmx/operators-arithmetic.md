---
title: Arithmetische Operatoren (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: edbe8a3404217f330b5b62a9d433c7d560b28656
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62502690"
---
# <a name="operators---arithmetic"></a>Operatoren – arithmetisch
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sie können arithmetische Operatoren in Data Mining Extensions (DMX) für arithmetische Berechnungen in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], einschließlich der Addition, Subtraktion, Multiplikation und Division.  
  
 In der folgenden Tabelle sind die arithmetischen Operatoren aufgeführt, die DMX unterstützt.  
  
|Operator|Description|  
|--------------|-----------------|  
|[+ &#40;Add&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Addiert zwei Zahlen.|  
|[- &#40;Subtract&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Subtrahiert eine Zahl von einer anderen Zahl.|  
|[&#42; &#40;Multiply&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Multipliziert eine Zahl mit einer anderen Zahl.|  
|[&#40;Divide&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|Dividiert eine Zahl durch eine andere Zahl.|  
  
 Die folgenden Regeln bestimmen die Rangfolge, die arithmetische Operatoren in einem DMX-Ausdruck haben.  
  
-   Sind in einem Ausdruck mehrere arithmetische Operatoren vorhanden, werden Multiplikationen und Divisionen vor Subtraktionen und Additionen berechnet.  
  
-   Wenn alle arithmetischen Operatoren in einem Ausdruck in der Rangfolge gleichwertig sind, werden sie von links nach rechts ausgewertet.  
  
-   Ausdrücke, die in Klammern stehen, erhalten Vorrang vor allen anderen Operationen.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Ausdrücke &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
