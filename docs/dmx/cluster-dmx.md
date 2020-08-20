---
description: Cluster (DMX)
title: Cluster (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0722e53752cfa01ffee086cb8cf1f6a84f82fd4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457846"
---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Gibt den Cluster zurück, der mit der höchsten Wahrscheinlichkeit den Eingabefall enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Gilt für  
 Diese Funktion kann nur verwendet werden, wenn das zugrunde liegende Data Mining-Modell Cluster unterstützt.  
  
## <a name="return-type"></a>Rückgabetyp  
 Für die **Cluster** Funktion sind keine Parameter erforderlich.  
  
 Die **Cluster** Funktion gibt einen skalaren Wert eines Cluster namens zurück. Wenn Sie diese Funktion jedoch als Argument einer anderen Funktion verwenden, müssen Sie Sie als ein-Wert betrachten \<cluster column reference> .  
  
## <a name="remarks"></a>Bemerkungen  
 **Cluster** kann auch als `<` Clusterspaltenverweis `>` für eine **präthistogram** -Funktion verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine SINGLETON-Abfrage mit dem [präthistogram-&#40;DMX-&#41;](../dmx/predicthistogram-dmx.md) und Cluster Funktionen verwendet, um die Entfernung des einzelnen falls von jedem Cluster des TM Clustering-Mining Modells und die Wahrscheinlichkeit zurückzugeben, dass der jeweilige Fall in jedem Cluster vorhanden ist.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Clusterwahrscheinlichkeit &#40;DMX-&#41;](../dmx/clusterprobability-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
