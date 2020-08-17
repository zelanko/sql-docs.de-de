---
description: Verwendung (DMX)
title: Verwendung (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3886cd500282d34ef07145913e036a6ab4ad4852
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88394856"
---
# <a name="usage-dmx"></a>Verwendung (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Wenn Sie Data Mining-Erweiterungen (DMX) verwenden, um ein neues Data Mining Modell in zu definieren [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , müssen Sie angeben, wie der Data Mining Algorithmus, der das Modell erstellt, jede Spalte verwenden soll. Sie können für eine Spalte angeben, dass sie einen der folgenden Typen hat:  
  
-   **Schlüssel**  
  
-   **Key Sequence**  
  
-   **Key Time**  
  
-   **Voraus**  
  
-   **Nur vorhersagen**  
  
 Spalten, für die kein Typ in DMX angegeben ist, werden als Eingabespalten behandelt.  
  
 Damit der Algorithmus ein Modell richtig verarbeiten kann, muss Folgendes angegeben werden: die Schlüsselspalte, mit der jede Zeile eindeutig bestimmt wird, die Zielspalte für das Erstellen von Vorhersagen (wenn Sie ein vorhersagbares Modell erstellen) und die Spalten, die als Eingabespalten verwendet werden sollen, um die Beziehungen zu erstellen, anhand derer die Zielspalte vorhergesagt wird.  
  
 Als **Vorhersage** Typen angegebene Spalten werden sowohl als Eingabe-als auch als Ausgabespalten verwendet. Als **prätonly** angegebene Spalten werden nur als Ausgabespalten verwendet. Bestimmte Algorithmen behandeln Predict-Spalten möglicherweise anders.  
  
 Weitere Informationen zu den von unterstützten Spalten Verwendungs Typen finden Sie unter [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [Mining Modell Spalten](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersage Abfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
