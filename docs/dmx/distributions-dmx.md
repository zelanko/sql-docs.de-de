---
title: Verteilungen (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fda2eb169985eb670614f611764fbf149c71a42d
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892793"
---
# <a name="distributions-dmx"></a>Verteilungen (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  In [!INCLUDE[msCoName](../includes/msconame-md.md)] könnenSieden[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Inhalt von Spalten in einer Mining Struktur definieren, um zu beeinflussen, wie Algorithmen die Daten in diesen Spalten verarbeiten, wenn Sie Mining Modelle erstellen. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Für einige Algorithmen ist es hilfreich, vor dem Verarbeiten des Modells für jede kontinuierliche Spalte die Verteilung zu definieren, wenn für die Spalten bekannt ist, dass sie normal verteilte Werte enthalten. Wenn Sie die Verteilungen nicht definieren, liefern die sich ergebenden Miningmodelle möglicherweise ungenauere Vorhersagen, da die Algorithmen weniger Informationen zum Interpretieren der Daten haben.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Mining-Algorithmen unterstützen die folgenden Verteilungstypen:  
  
 **NORMALER**  
 Die Werte für die kontinuierliche Spalte bilden ein Histogramm, das einer gaußschen Normalverteilung folgt.  
  
 **Log Normal**  
 Die Werte für die kontinuierliche Spalte bilden ein Histogramm, bei dem der Logarithmus der Werte normal verteilt ist.  
  
 **GLEICH**  
 Die Werte für die kontinuierliche Spalte bilden eine flache Kurve, in der alle Werte gleich wahrscheinlich sind.  
  
 Weitere Informationen zu [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Mining Algorithmen finden Sie unter [Data Mining- &#40;Algorithmen Analysis Services Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining). Algorithmenanbieter von Drittanbietern unterstützen möglicherweise weitere Verteilungstypen. Verwenden Sie das **SUPPORTED_DISTRIBUTION_FLAGS** -Schemarowset, um zu bestimmen, welche Verteilungs Typen ein Algorithmus unterstützt.  
  
 Weitere Informationen zu Verteilungs Typen finden Sie unter [Data Mining &#40;&#41;für Spalten Verteilungen](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining).  
  
## <a name="see-also"></a>Siehe auch  
 [Inhaltstypen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [DMX&#41; - &#40;Syntax Elemente für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [DMX&#41; - &#40;Funktionsreferenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41; - &#40;Operator Verweis für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41; - &#40;Anweisungs Referenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-statements.md)   
 [DMX&#41; - &#40;Syntax Konventionen für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Allgemeine Vorhersage &#40;Funktionen (DMX)&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
