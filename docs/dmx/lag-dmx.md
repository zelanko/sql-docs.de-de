---
title: Verzögerung (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f984e50b2c6a800a66f689d88b21dfcb487e282
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842493"
---
# <a name="lag-dmx"></a>Lag (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Zeitscheibe zwischen dem Datum des aktuellen Falles und dem letzten Datum der Trainingsmenge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert mit dem Typ integer.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die **Lag** Funktion dient für ein Modell, in denen die KEY TIME-Spalte in einer geschachtelten Tabelle befindet, kann die Funktion muss in der untergeordneten Select-Anweisung die gefunden werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Fälle zurückgegeben, die in den letzten 12 Monaten der Daten liegen, die zum Trainieren des Modells verwendet wurden.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis-Funktion](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
