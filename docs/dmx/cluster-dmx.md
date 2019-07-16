---
title: (DMX)-Cluster | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa7df2782b8102e386c70d5e874a25f7868dbb1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071079"
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
 Die **Cluster** Funktion erfordert keine Parameter.  
  
 Die **Cluster** Funktion gibt einen Skalarwert eines Clusternamens zurück. Aber wenn Sie diese Funktion als Argument einer anderen Funktion verwenden, Sie müssen betrachten Sie dies als eine \<cluster Spaltenverweis >.  
  
## <a name="remarks"></a>Hinweise  
 **Cluster** kann auch verwendet werden, als eine `<`cluster Spaltenverweis`>` für eine **PredictHistogram** Funktion.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Singleton-Abfrage mit der [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md) und Funktionen, um die Entfernung des einzelnen Falls von jedem Cluster das TM Clustering-Miningmodell zurückzugeben und die die Wahrscheinlichkeit, dass der einzelne Fall in jedem Cluster vorhanden sind.  
  
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
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
