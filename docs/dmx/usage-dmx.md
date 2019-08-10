---
title: Verwendung (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b961282ba6bc25caa260a3e156f843a413a5ef1a
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893110"
---
# <a name="usage-dmx"></a>Verwendung (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Wenn Sie Data Mining-Erweiterungen (DMX) verwenden, um ein neues Data Mining Modell [!INCLUDE[msCoName](../includes/msconame-md.md)] in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]zu definieren, müssen Sie angeben, wie der Data Mining Algorithmus, der das Modell erstellt, jede Spalte verwenden soll. Sie können für eine Spalte angeben, dass sie einen der folgenden Typen hat:  
  
-   **Key**  
  
-   **Schlüssel Sequenz**  
  
-   **Schlüsselzeit**  
  
-   **Predict**  
  
-   **PredictOnly**  
  
 Spalten, für die kein Typ in DMX angegeben ist, werden als Eingabespalten behandelt.  
  
 Damit der Algorithmus ein Modell richtig verarbeiten kann, muss Folgendes angegeben werden: die Schlüsselspalte, mit der jede Zeile eindeutig bestimmt wird, die Zielspalte für das Erstellen von Vorhersagen (wenn Sie ein vorhersagbares Modell erstellen) und die Spalten, die als Eingabespalten verwendet werden sollen, um die Beziehungen zu erstellen, anhand derer die Zielspalte vorhergesagt wird.  
  
 Als **Vorhersage** Typen angegebene Spalten werden sowohl als Eingabe-als auch als Ausgabespalten verwendet. Als **prätonly** angegebene Spalten werden nur als Ausgabespalten verwendet. Bestimmte Algorithmen behandeln Predict-Spalten möglicherweise anders.  
  
 Weitere Informationen zu den von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützten Spalten Verwendungs Typen finden Sie unter [Mining Modell Spalten](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
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
  
  
