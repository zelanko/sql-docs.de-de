---
title: Prädistogram (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fdc63d1c93d1290c701233cb94f71f157c771182
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893853"
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
 Ein Histogramm generiert Statistikspalten. Die Spalten Struktur des zurückgegebenen Histogramms hängt vom Typ des Spalten Verweises ab, der mit der Funktion "vorherd..." verwendet wird.  
  
## <a name="scalar-columns"></a>Skalare Spalten  
 Bei einem \<Verweis > für eine skalare Spalte besteht das Histogramm, das die Funktion " **präthistogram** " zurückgibt, aus den folgenden Spalten:  
  
-   Der Wert, der vorhergesagt wird.  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]Data Mining Algorithmen unterstützen **$ProbabilityVariance**nicht. Diese Spalte enthält für [!INCLUDE[msCoName](../includes/msconame-md.md)]-Algorithmen immer 0.  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)]Data Mining Algorithmen unterstützen **$ProbabilityStdev**nicht. Diese Spalte enthält für [!INCLUDE[msCoName](../includes/msconame-md.md)]-Algorithmen immer 0.  
  
-   **$AdjustedProbability**  
  
     Die **$AdjustedProbability** Spalte ist eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Erweiterung der [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB für Data Mining-Spezifikation.  
  
## <a name="cluster-columns"></a>Clusterspalten  
 Das Histogramm, das die Funktion " **präthistogram** " \<für einen Cluster Spalten Verweis zurückgibt > besteht aus den folgenden Spalten:  
  
-   **$Cluster** (stellt den Cluster Namen dar)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der vorhergesagte Status der Bike Buyer-Spalte in einer SINGLETON-Abfrage zurückgegeben. Die Abfrage gibt auch die beiden wahrscheinlichsten Zustände des Bike Buyer-Attributs basierend auf der angepassten Wahrscheinlichkeit zurück, die mithilfe der Funktion " **präthistogram** " abgerufen wurde.  
  
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
 [Cluster &#40;-DMX&#41;](../dmx/cluster-dmx.md)   
 [Clusterwahrscheinlichkeits &#40;-DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [Präwahrscheinlichkeits &#40;-DMX&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)   
 [Prätsupport &#40;-DMX&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)   
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [DMX&#41; - &#40;Funktionsreferenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;-DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersage &#40;Funktionen (DMX)&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
