---
title: Modellierungsflags (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 01be0e2d0ead01a3b6c630e0ddd0f53e55620104
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008317"
---
# <a name="modeling-flags-dmx"></a>Modellierungsflags (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sie können mithilfe der Modellierungsflags in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] einem Data Mining-Algorithmus zusätzliche Informationen zu den Daten zur Verfügung stellen, die in einer Falltabelle definiert sind. Der Algorithmus kann diese Informationen verwenden, um ein genaueres Data Mining-Modell zu erstellen. Sie können Modellierungsflags sowohl für Miningstruktur- aus auch für Miningmodellspalten definieren.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt die folgenden Modellierungsflags:  
  
 **NOT NULL**  
 Die Werte für die Attributspalte dürfen auf keinen Fall einen NULL-Wert enthalten. Es führt zu einem Fehler, wenn [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] während des Modelltrainings einen NULL-Wert für diese Attributspalte findet. Dieses Flag ist für eine Miningstrukturspalte definiert.  
  
 **REGRESSOR**  
 Zeigt an, dass der Algorithmus die angegebene Spalte in der Regressionsformel von Regressionsalgorithmen verwenden kann. Dieses Flag wird vom [!INCLUDE[msCoName](../includes/msconame-md.md)] Linear Regression- und vom [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus unterstützt und ist für eine Miningmodellspalte definiert.  
  
 **MODEL_EXISTENCE_ONLY**  
 Die Werte für die Attributspalte sind weniger wichtig als das Vorhandensein des Attributs. Dieses Flag ist für eine Miningmodellspalte definiert.  
  
 Algorithmen von Drittanbietern unterstützen möglicherweise weitere Modellierungsflags. Um zu bestimmen, welche Modellierungsflags ein Algorithmus unterstützt, verwenden Sie die **SUPPORTED_MODELING_FLAGS** -Schemarowsets. Sie können auch den Miningdienst auf dem Server abfragen, um festzustellen, welche Modellierungsflags für einen bestimmten Algorithmus unterstützt werden. Die folgende Abfrage gibt beispielsweise die Modellierungsflags zurück, die für den Microsoft Linear Regression-Algorithmus auf dem aktuellen Server unterstützt werden:  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 Erwartete Ergebnisse:  
  
 NOT NULL,REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>Festlegen von Modellierungsflags auf einem Miningmodell  
 Beispiele für die Syntax, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt, für das Festlegen eines Flags für eine Miningstrukturspalte, finden Sie unter [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
 Ein Beispiel für die Syntax zum Angeben eines Modellierungsflags für eine Miningmodellspalte, finden Sie unter [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
 Weitere Informationen zum Arbeiten mit Miningmodellspalten finden Sie unter [Miningmodellspalten](../analysis-services/data-mining/mining-model-columns.md).  
  
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
  
  
