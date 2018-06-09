---
title: Cluster (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 41f835a93e5976945281b6b04258c516b0322236
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841303"
---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt den Cluster zurück, der mit der höchsten Wahrscheinlichkeit den Eingabefall enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Gilt für  
 Diese Funktion kann nur verwendet werden, wenn das zugrunde liegende Data Mining-Modell Cluster unterstützt.  
  
## <a name="return-type"></a>Rückgabetyp  
 Die **Cluster** Funktion keine Parameter erfordert.  
  
 Die **Cluster** Funktion gibt einen Skalarwert eines Clusternamens zurück. Jedoch, wenn Sie diese Funktion als Argument einer anderen Funktion verwenden, Sie müssen unter Berücksichtigung als eine \<cluster Spaltenverweis >.  
  
## <a name="remarks"></a>Hinweise  
 **Cluster** kann auch verwendet werden, als ein `<`cluster Spaltenverweis`>` für eine **"PredictHistogram"** Funktion.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Singleton-Abfrage mit der ["PredictHistogram" &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md) und -Funktionen, um die Entfernung des einzelnen Falls von jedem Cluster des Miningmodells TM Clustering zurückzugeben und die die Wahrscheinlichkeit, dass die einzelnen Groß-/Kleinschreibung in jedem Cluster vorhanden ist.  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis-Funktion](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
