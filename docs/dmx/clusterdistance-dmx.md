---
title: ClusterDistance (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 523c57811ca29956edc3c18b8143844732c163b6
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892393"
---
# <a name="clusterdistance-dmx"></a>ClusterDistance (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die **ClusterDistance** -Funktion gibt den Abstand des Eingabe falls von dem angegebenen Cluster zurück, oder, wenn kein Cluster angegeben wurde, den Abstand des Eingabe falls von dem wahrscheinlichsten Cluster.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>Gilt für  
 Diese Funktion kann nur verwendet werden, wenn das zugrunde liegende Data Mining-Modell Cluster unterstützt. Die Funktion kann mit jedem Clusteringmodell verwendet werden (EM, K-Means usw.), die Ergebnisse unterscheiden sich jedoch in Abhängigkeit von dem Algorithmus.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert.  
  
## <a name="remarks"></a>Hinweise  
 Die **ClusterDistance** -Funktion gibt den Abstand zwischen dem Eingabe Fall und dem Cluster mit der höchsten Wahrscheinlichkeit für diesen Eingabe Fall zurück.  
  
 Im Fall von K-Means-Clustering, bei dem jeder Fall nur zu einem Cluster gehören kann und die Mitgliedschaftsgewichtung 1,0 beträgt, ist der Clusterabstand immer 0. In K-Means wird jedoch davon ausgegangen, dass jeder Cluster einen Schwerpunkt besitzt. Sie können den Wert des Schwerpunkts abrufen, indem Sie im Miningmodellinhalt die geschachtelte Tabelle NODE_DISTRIBUTION abfragen oder durchsuchen. Weitere Informationen zu diesem Algorithmus finden Sie unter [Mingingmodellinhalt von Clustermodellen &#40;Analysis Services – Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining).  
  
 Im Fall der standardmäßigen EM-Clusteringmethode werden alle Punkte innerhalb des Clusters als gleich wahrscheinlich betrachtet, daher ist programmbedingt kein Schwerpunkt für den Cluster vorhanden. Der Wert von **ClusterDistance** zwischen einem bestimmten Fall und einem bestimmten Cluster *N* wird wie folgt berechnet:  
  
 ClusterDistance (n) = 1-(mitgliedführungs Gewichtung (n))  
  
 Oder:  
  
 ClusterDistance (n) = 1-clusterwahrscheinlichkeits (n))  
  
## <a name="related-prediction-functions"></a>Zugehörige Vorhersagefunktionen  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt folgende zusätzliche Funktionen für die Abfrage von Clusteringmodellen bereit:  
  
-   Verwenden Sie [die &#40;Cluster-&#41; DMX](../dmx/cluster-dmx.md) -Funktion, um den wahrscheinlichsten Cluster zurückzugeben.  
  
-   Verwenden Sie die [DMX &#40;&#41; -Funktion Clusterwahrscheinlichkeiten](../dmx/clusterprobability-dmx.md) zum Ermitteln der Wahrscheinlichkeit, dass ein Fall zu einem bestimmten Cluster gehört. Dieser Wert stellt die Umkehrung des Clusterabstands dar.  
  
-   Verwenden Sie die [DMX&#41; - &#40;Funktion "präthistogram](../dmx/predicthistogram-dmx.md) ", um ein Histogramm der Wahrscheinlichkeit zurückzugeben, dass der Eingabe Fall in jedem Cluster des Modells vorhanden ist.  
  
-   Verwenden Sie die [DMX &#40;&#41; -Funktion "prätcaselikelihood](../dmx/predictcaselikelihood-dmx.md) ", um ein Measure zwischen 0 und 1 zurückzugeben, das angibt, wie wahrscheinlich ein Eingabe Fall vorhanden sein muss, wenn das vom Algorithmus erlernte Modell berücksichtigt wird.  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>"Example1" Abrufen der clusterentfernung zum wahrscheinlichsten Cluster  
 Im folgenden Beispiel wird der Abstand von dem angegebenen Fall zu dem Cluster angegeben, zu dem der Fall höchstwahrscheinlich gehört.  
  
```  
SELECT  
    ClusterDistance()  
FROM  
    [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Beispielergebnisse:  
  
|expression|  
|----------------|  
|0.0477390930705145|  
  
 Sie können im vorstehenden Beispiel `Cluster` durch `ClusterDistance` ersetzen, um festzustellen, um welchen Cluster es sich handelt.  
  
 Beispielergebnisse:  
  
|$CLUSTER|  
|--------------|  
|Cluster 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>"Example2" Abrufen der Entfernung zu einem angegebenen Cluster  
 In der folgenden Syntax wird das Schemarowset für den Inhalt eines Miningmodells verwendet, um eine Liste mit Knoten-IDs und Knotenbeschriftungen für die Cluster zurückzugeben, die im Miningmodell vorhanden sind. Anschließend können Sie die Knoten Beschriftung als Clusterbezeichnerargument in der **ClusterDistance** -Funktion verwenden.  
  
```  
SELECT NODE_UNIQUE_NAME, NODE_CAPTION   
FROM <model>.CONTENT   
WHERE NODE_TYPE = 5  
```  
  
 Beispielergebnisse:  
  
|NODE_UNIQUE_NAME|NODE_CAPTION|  
|------------------------|-------------------|  
|001|Cluster 1|  
|002|Cluster 2|  
  
 Im folgenden Syntaxbeispiel wird der Abstand zwischen dem angegebenen Fall und dem Cluster mit der Bezeichnung Cluster 2 zurückgeben.  
  
```  
SELECT  
    ClusterDistance('Cluster 2')  
AS [Cluster 2 Distance]  
FROM [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Beispielergebnisse:  
  
|Cluster 2 Distance|  
|------------------------|  
|0.97008209236394|  
  
## <a name="see-also"></a>Siehe auch  
 [Cluster &#40;-DMX&#41;](../dmx/cluster-dmx.md)   
 [DMX&#41; - &#40;Funktionsreferenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;-DMX&#41;](../dmx/functions-dmx.md)   
 [Miningmodellinhalt von Clustermodellen &#40;Analysis Services - Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining)  
  
  
