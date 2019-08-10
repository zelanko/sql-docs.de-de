---
title: Prätwahrscheinlichkeits (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bd8365b2d3aac82c184af549ef21952fd4c8e649
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893903"
---
# <a name="predictprobability-dmx"></a>PredictProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Wahrscheinlichkeit für einen bestimmten Status zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein skalare Spalte.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert.  
  
## <a name="remarks"></a>Hinweise  
 Ist der vorhergesagte Status (predicted state) nicht angegeben, wird der Status verwendet, der die höchste Wahrscheinlichkeit hat, wobei der Bucket der fehlenden Status ausgeschlossen wird. Wenn Sie den Bucket Missing States einschließen möchten, \<legen Sie den vorhergesagten Status > auf **INCLUDE_NULL**fest. Legen Sie den \<vorhergesagten Status > auf NULL fest, um die Wahrscheinlichkeit für die fehlenden Zustände zurückzugeben.  
  
> [!NOTE]  
>  Einige Miningmodelle stellen keine Wahrscheinlichkeitswerte zur Verfügung und können diese Funktion daher nicht verwenden. Zudem werden Wahrscheinlichkeitswerte für jeden einzelnen Zielwert unterschiedlich berechnet, oder sie können eine in Abhängigkeit von dem abgefragten Modelltyp unterschiedliche Interpretation aufweisen. Weitere Informationen zur Berechnung der Wahrscheinlichkeit für einen bestimmten Modelltyp finden Sie im Thema zu einzelnen Algorithmen unter [Mining Modell Inhalt &#40;Analysis Services-Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine natürliche PREDICTION JOIN-Anweisung verwendet, um basierend auf dem TM Decision Tree-Miningmodell zu bestimmen, ob es wahrscheinlich ist, dass eine Person ein Fahrrad kaufen wird. Außerdem wird die Wahrscheinlichkeit für die Vorhersage bestimmt. Dieses Beispiel enthält zwei PredictProbability-Funktionen, eine für jeden möglichen Wert. Wenn Sie dieses Argument auslassen, gibt die Funktion die Wahrscheinlichkeit für den wahrscheinlichsten Wert zurück.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictProbability([Bike Buyer], 1) AS [Bike Buyer = Yes],  
  PredictProbability([Bike Buyer], 0) AS [Bike Buyer = No]  
FROM [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Beispielergebnisse:  
  
|Bike Buyer|Bike Buyer = Yes|Bike Buyer = No|  
|----------------|-----------------------|----------------------|  
|1|0.867074195848097|0.132755556974282|  
  
## <a name="see-also"></a>Siehe auch  
 [DMX&#41; - &#40;Funktionsreferenz für Data Mining-Erweiterungen](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;-DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersage &#40;Funktionen (DMX)&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
