---
description: PredictSupport (DMX)
title: Prätsupport (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cea4913bf3668c89fb0c1c66632359a372f3d54b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422254"
---
# <a name="predictsupport-dmx"></a>PredictSupport (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Gibt den Unterstützungswert für einen bestimmten Status zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein skalare Spalte.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert des Typs, der durch angegeben wird *\<*scalar column reference*>* .  
  
## <a name="remarks"></a>Bemerkungen  
 Ist der vorhergesagte Status (predicted state) nicht angegeben, wird der Status verwendet, der die höchste vorhersagbare Wahrscheinlichkeit hat, wobei der Bucket der fehlenden Status ausgeschlossen wird. Um den Bucket Missing States einzuschließen, legen \<predicted state> Sie den auf **INCLUDE_NULL**fest.  
  
 Wenn Sie die Unterstützung für die fehlenden Zustände zurückgeben möchten, legen \<predicted state> Sie auf NULL fest.  
  
> [!NOTE]  
>  Die Unterstützungswerte werden abweichend berechnet oder können in Abhängigkeit von dem abgefragten Modelltyp eine abweichende Interpretation aufweisen. Weitere Informationen zur Berechnung der Unterstützung für einen bestimmten Modelltyp finden Sie unter der Typ des einzelnen Algorithmus in [Mining Modell Inhalt &#40;Analysis Services Data Mining-&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine SINGLETON-Abfrage verwendet, um vorherzusagen, ob eine Person ein Fahrrad kaufen wird. Außerdem wird die Unterstützung der Vorhersage basierend auf dem TM Decision Tree-Miningmodell bestimmt.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictSupport([Bike Buyer]) AS [Support],  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
