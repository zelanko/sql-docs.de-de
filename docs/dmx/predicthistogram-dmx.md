---
title: PredictHistogram (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e7129985eac09d741ea9d00c551a9507ee92c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659174"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt eine Tabelle zurück, die einem Histogramm für die Vorhersage einer bestimmten Spalte entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Einen Verweis auf eine skalare Spalte oder eine Clusterspalte. Kann mit allen Algorithmentypen außer dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus verwendet werden.  
  
## <a name="return-type"></a>Rückgabetyp  
 Tabelle  
  
## <a name="remarks"></a>Hinweise  
 Ein Histogramm generiert Statistikspalten. Die Spaltenstruktur des zurückgegebenen Histogramms hängt der Typ des Spaltenverweises, die verwendet wird, mit der **PredictHistogram** Funktion.  
  
## <a name="scalar-columns"></a>Skalare Spalten  
 Für eine \<skalarspaltenverweis >, das Histogramm, das **PredictHistogram** Funktionsrückgaben besteht aus den folgenden Spalten:  
  
-   Der Wert, der vorhergesagt wird.  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] Datamining-Algorithmen unterstützen keine **$ProbabilityVariance**. Diese Spalte enthält für [!INCLUDE[msCoName](../includes/msconame-md.md)]-Algorithmen immer 0.  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] Datamining-Algorithmen unterstützen keine **$ProbabilityStdev**. Diese Spalte enthält für [!INCLUDE[msCoName](../includes/msconame-md.md)]-Algorithmen immer 0.  
  
-   **$AdjustedProbability**  
  
     Die **$AdjustedProbability** Spalte ist eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Erweiterung der [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB für Data Mining-Spezifikation.  
  
## <a name="cluster-columns"></a>Clusterspalten  
 Das Histogramm, das **PredictHistogram** Funktionsergebnis ist für eine \<Spaltenverweis cluster > besteht aus den folgenden Spalten:  
  
-   **$Cluster** (entspricht dem Clusternamen)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der vorhergesagte Status der Bike Buyer-Spalte in einer SINGLETON-Abfrage zurückgegeben. Die Abfrage gibt auch die oberen beiden wahrscheinlichsten Statuswerte des Bike Buyer-Attributs, basierend auf der angepassten Wahrscheinlichkeit abgerufen, indem Sie mit der **PredictHistogram** Funktion.  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)   
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
