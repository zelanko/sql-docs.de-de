---
title: Datamining-Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80e7a793973ddbe0e55862d2e68f23e6c7e31dc3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746832"
---
# <a name="data-mining-properties"></a>Data Mining-Eigenschaften
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden die in den folgenden Tabellen aufgeführten Data Mining-Eigenschaften unterstützt. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Gilt für:** Nur mehrdimensionaler Servermodus  
  
## <a name="non-specific-category"></a>Nicht spezifische Kategorie  
 `AllowSessionMiningModels`  
 Eine boolesche Eigenschaft, die anzeigt, ob Sitzungsminingmodelle erstellt werden können.  
  
 Der Standardwert für diese Eigenschaft ist FALSE. Dies bedeutet, dass keine Sitzungsminingmodelle erstellt werden können.  
  
 `AllowAdHocOpenRowsetQueries`  
 Eine boolesche Eigenschaft, die anzeigt, ob Ad-hoc-Abfragen für geöffnete Rowsets zulässig sind.  
  
 Der Standardwert für diese Eigenschaft ist FALSE. Dies bedeutet, dass während einer Sitzung keine Abfragen für geöffnete Rowsets zugelassen sind.  
  
 `AllowedProvidersInOpenRowset`  
 Eine Zeichenfolge, die die in einem geöffneten Rowset zulässigen Anbieter identifiziert. Die Zeichenfolge kann aus einer durch Kommas bzw. Semikolons getrennten Liste von Anbieter-ProgIDs oder aus dem Wert [All] bestehen.  
  
 `MaxConcurrentPredictionQueries`  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die maximale Anzahl von gleichzeitigen Vorhersageabfragen definiert.  
  
## <a name="algorithms-category"></a>Algorithmus-Kategorie  
 `Microsoft_Association_Rules\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_Association_Rules-Algorithmus aktiviert ist.  
  
 `Microsoft_Clustering\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_Clustering-Algorithmus aktiviert ist.  
  
 `Microsoft_Decision_Trees\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_DecisionTrees-Algorithmus aktiviert ist.  
  
 `Microsoft_Naive_Bayes\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_ Naive_Bayes-Algorithmus aktiviert ist.  
  
 `Microsoft_Neural_Network\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_Neural_Network-Algorithmus aktiviert ist.  
  
 `Microsoft_Sequence_Clustering\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_Sequence_Clustering-Algorithmus aktiviert ist.  
  
 `Microsoft_Time_Series\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_Time_Series-Algorithmus aktiviert ist.  
  
 `Microsoft_Linear_Regression\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_Linear_Regression-Algorithmus aktiviert ist.  
  
 `Microsoft_Logistic_Regression\ Enabled`  
 Eine boolesche Eigenschaft, die anzeigt, ob der Microsoft_Logistic_Regression-Algorithmus aktiviert ist.  
  
> [!NOTE]  
>  Zusätzlich zu den Data Mining-Diensten, die auf dem Server verfügbar sind, sind Data Mining-Eigenschaften vorhanden, die das Verhalten bestimmter Algorithmen definieren. Sie konfigurieren diese Eigenschaften, wenn Sie ein einzelnes Data Mining-Modell erstellen, nicht auf Serverebene. Weitere Informationen finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Physische Architektur &#40;Analysis Services – Data Mining&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md)   
 [Konfigurieren von Servereigenschaften in Analysis Services](server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
