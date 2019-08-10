---
title: Inhaltstypen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: da8a5e5602b877c12284d8410f6b2a1c7da6bc58
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889144"
---
# <a name="content-types-dmx"></a>Inhaltstypen (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Data Mining-Algorithmen benötigen über den Datentyp hinausgehende, zusätzliche Informationen, damit sie richtig ausgewertet werden können, z. B. den Inhaltstyp. Der Inhaltstyp unterstützt dabei, für den jeweiligen Algorithmus zu ermitteln, wie die Daten in der Spalte verarbeitet werden sollen.  
  
 Jeder Algorithmus unterstützt bestimmte Inhaltstypen. Beispielsweise kann der [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Algorithmus keine kontinuierlichen Spalten verwenden. Wenn Sie eine kontinuierliche Spalte in einem [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Modell verwenden möchten, müssen Sie die Daten in der Spalte diskretisieren. Für einige Algorithmen sind bestimmte Inhaltstypen erforderlich, damit sie richtig funktionieren. Beispielsweise ist für den [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus eine Schlüsselzeitspalte erforderlich, um die Zeitspanne zu kennzeichnen, in der die Daten gesammelt wurden.  
  
 Eine umfassende Beschreibung der Inhaltstypen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , die von unterstützt werden, finden Sie unter [Data Mining &#40;&#41;-Inhaltstypen](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining).  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [DMX&#41; - &#40;Syntax Elemente für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [DMX&#41; - &#40;Funktionsreferenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41; - &#40;Operator Verweis für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41; - &#40;Anweisungs Referenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-statements.md)   
 [DMX&#41; - &#40;Syntax Konventionen für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Allgemeine Vorhersage &#40;Funktionen (DMX)&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
