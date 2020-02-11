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
ms.openlocfilehash: e78241252733e8298c0bc727f9c45dd6df2768ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008211"
---
# <a name="operators---arithmetic"></a>Operatoren – arithmetisch
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sie können arithmetische Operatoren in Data Mining-Erweiterungen (DMX) für arithmetische [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Berechnungen in verwenden, einschließlich Addition, Subtraktion, Multiplikation und Division.  
  
 In der folgenden Tabelle sind die arithmetischen Operatoren aufgeführt, die DMX unterstützt.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|[+ &#40;&#41; &#40;DMX hinzufügen&#41;](../dmx/add-dmx.md)|Addiert zwei Zahlen.|  
|[-&#40;subtrahieren&#41; &#40;DMX-&#41;](../dmx/subtract-dmx.md)|Subtrahiert eine Zahl von einer anderen Zahl.|  
|[&#42; &#40;multiplizieren&#41; &#40;DMX-&#41;](../dmx/multiply-dmx.md)|Multipliziert eine Zahl mit einer anderen Zahl.|  
|[&#40;dividieren&#41; &#40;DMX-&#41;](../dmx/divide-dmx.md)|Dividiert eine Zahl durch eine andere Zahl.|  
  
 Die folgenden Regeln bestimmen die Rangfolge, die arithmetische Operatoren in einem DMX-Ausdruck haben.  
  
-   Sind in einem Ausdruck mehrere arithmetische Operatoren vorhanden, werden Multiplikationen und Divisionen vor Subtraktionen und Additionen berechnet.  
  
-   Wenn alle arithmetischen Operatoren in einem Ausdruck in der Rangfolge gleichwertig sind, werden sie von links nach rechts ausgewertet.  
  
-   Ausdrücke, die in Klammern stehen, erhalten Vorrang vor allen anderen Operationen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Ausdrücke &#40;DMX-&#41;](../dmx/expressions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersage Abfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Grundlegendes zur SELECT-Anweisung (DMX)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
