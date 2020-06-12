---
title: Clusterwahrscheinlichkeit (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e06563d9b6a69bc8903a55ee1e67cda962f246ba
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669350"
---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Wahrscheinlichkeit zurück, mit der der Eingabefall zum angegebenen Cluster gehört.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>Gilt für  
 Diese Funktion kann nur verwendet werden, wenn das zugrunde liegende Data Mining-Modell Cluster unterstützt.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert.  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Syntax wird das Schemarowset für den Inhalt eines Miningmodells verwendet, um die Knotenbeschriftungen zurückzugeben, die im Miningmodell vorhanden sind.  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 Weitere Informationen zur Verwendung dieser Syntax finden Sie unter [Select from &#60;Model&#62;. Inhalt &#40;DMX-&#41;](../dmx/select-from-model-content-dmx.md). Weitere Informationen zum Schemarowset des Mining Modell Inhalts finden Sie unter [DMSCHEMA_MINING_MODEL_CONTENT-Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
 Wenn eine \< Knoten Beschriftung> nicht angegeben ist, gibt die Funktion die Wahrscheinlichkeit zurück, mit der die Eingabe Fälle zum wahrscheinlichsten Cluster gehören. Verwenden Sie die **Cluster** Funktion, um den wahrscheinlichsten Cluster zurückzugeben.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Wahrscheinlichkeit dafür zurückgegeben, dass der angegebene Fall im Cluster mit der Bezeichnung Cluster 2 enthalten ist.  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cluster &#40;DMX-&#41;](../dmx/cluster-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
