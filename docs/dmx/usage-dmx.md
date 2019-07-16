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
ms.openlocfilehash: 4f576243ead99869ae4b12dfc4e79a1a6d57f5cc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939905"
---
# <a name="usage-dmx"></a>Verwendung (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Wenn Sie Data Mining Extensions (DMX) verwenden, definieren Sie ein neues Datamining-Modell in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], müssen Sie angeben, wie Datamining-Algorithmus, der das Modell erstellt die einzelnen Spalten verwendet. Sie können für eine Spalte angeben, dass sie einen der folgenden Typen hat:  
  
-   **Key**  
  
-   **Tastenkombination**  
  
-   **Schlüsselzeit**  
  
-   **Predict**  
  
-   **PredictOnly**  
  
 Spalten, für die kein Typ in DMX angegeben ist, werden als Eingabespalten behandelt.  
  
 Damit der Algorithmus ein Modell richtig verarbeiten kann, muss Folgendes angegeben werden: die Schlüsselspalte, mit der jede Zeile eindeutig bestimmt wird, die Zielspalte für das Erstellen von Vorhersagen (wenn Sie ein vorhersagbares Modell erstellen) und die Spalten, die als Eingabespalten verwendet werden sollen, um die Beziehungen zu erstellen, anhand derer die Zielspalte vorhergesagt wird.  
  
 Spalten, die als angegeben sind die **Predict** Typ verwendet wird, als Eingabe-und Ausgabespalten. Spalten, die als angegeben sind **PredictOnly** werden nur als Ausgabespalten verwendet. Bestimmte Algorithmen behandeln Predict-Spalten möglicherweise anders.  
  
 Weitere Informationen über die Spalte spaltenverwendungstypen, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt, finden Sie unter [Mining Model Columns](../analysis-services/data-mining/mining-model-columns.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
