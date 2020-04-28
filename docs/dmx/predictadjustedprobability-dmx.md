---
title: Prätadjustedwahrscheinlichkeits (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c2ae90886d6469802543f62bf5636ccaafeb32fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008090"
---
# <a name="predictadjustedprobability-dmx"></a>PredictAdjustedProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die angepasste Wahrscheinlichkeit für einen bestimmten Status zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictAdjustedProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Gilt für  
 Ein skalare Spalte.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist der vorhergesagte Status (predicted state) nicht angegeben, wird der Status verwendet, der die höchste vorhersagbare Wahrscheinlichkeit hat, wobei der Bucket der fehlenden Status ausgeschlossen wird. Wenn Sie den Bucket für fehlende Zustände einschließen möchten \<, legen Sie den vorhergesagten Status> auf **INCLUDE_NULL**fest.  
  
 Um die angepasste Wahrscheinlichkeit für die fehlenden Zustände zurückzugeben, legen \<Sie den vorhergesagten Status> auf NULL fest.  
  
 Die **"prätadjustedwahrscheinlichkeits** " [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Funktion ist [!INCLUDE[msCoName](../includes/msconame-md.md)] eine Erweiterung des OLE DB für die Data Mining-Spezifikation.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine natürliche PREDICTION JOIN-Anweisung verwendet, um basierend auf dem TM Decision Tree-Miningmodell zu bestimmen, ob es wahrscheinlich ist, dass eine Person ein Fahrrad kaufen wird. Außerdem wird die angepasste Wahrscheinlichkeit für die Vorhersage bestimmt.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictAdjustedProbability([Bike Buyer]) AS [Adjusted Probability]  
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
  
  
