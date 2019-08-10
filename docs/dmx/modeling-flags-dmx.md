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
ms.openlocfilehash: a610f3aed7f520163dc4e2b30651d8b0397ef644
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893932"
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
  
 Algorithmen von Drittanbietern unterstützen möglicherweise weitere Modellierungsflags. Um zu ermitteln, welche Modellierungsflags ein Algorithmus unterstützt, verwenden Sie das **SUPPORTED_MODELING_FLAGS** -Schemarowset Sie können auch den Miningdienst auf dem Server abfragen, um festzustellen, welche Modellierungsflags für einen bestimmten Algorithmus unterstützt werden. Die folgende Abfrage gibt beispielsweise die Modellierungsflags zurück, die für den Microsoft Linear Regression-Algorithmus auf dem aktuellen Server unterstützt werden:  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 Erwartete Ergebnisse:  
  
 NOT NULL,REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>Festlegen von Modellierungsflags auf einem Miningmodell  
 Beispiele für die Syntax [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , die unterstützt, um ein Flag für eine Mining Struktur Spalte anzugeben, finden Sie unter [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
 Ein Beispiel für die Syntax zum Angeben einer Modellierungs-Modellierungsflags für eine Mining Modell Spalte finden Sie unter [Alter Mining &#40;Structure DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
 Weitere Informationen zum Arbeiten mit Mining Modell Spalten finden Sie unter [Mining Modell Spalten](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
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
  
  
