---
title: Verzögerung (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 170e2f8b565f8b3d9d5e385b2bba9f183e743ace
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008348"
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
  
  
