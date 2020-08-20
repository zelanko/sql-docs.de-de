---
description: Lag (DMX)
title: Verzögerung (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4e7aa504c3afd236ddd748a7ee81cbbb6cf90b7c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466568"
---
# <a name="lag-dmx"></a>Lag (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Gibt die Zeitscheibe zwischen dem Datum des aktuellen Falles und dem letzten Datum der Trainingsmenge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert mit dem Typ integer.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die **lag** -Funktion für ein Modell verwendet wird, in dem sich die Key Time-Spalte in einer geschachtelten Tabelle befindet, muss sich die Funktion in der untergeordneten SELECT-Anweisung der Anweisung befinden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Fälle zurückgegeben, die in den letzten 12 Monaten der Daten liegen, die zum Trainieren des Modells verwendet wurden.  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
