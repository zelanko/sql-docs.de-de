---
title: RangeMax (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 61552cd8e38f77d12d7f4da10e2bbe9281e6073d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041680"
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt das obere Ende des vorhergesagten Buckets zurück, der für eine diskretisierte Spalte ermittelt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Skalare Spalten.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert.  
  
## <a name="remarks"></a>Hinweise  
 Die **RangeMax** Funktion kann verwendet werden, [SELECT DISTINCT FROM &#60;Modell &#62; &#40;DMX&#41; ](../dmx/select-distinct-from-model-dmx.md) Abfragen. Wird der Verweis auf skalare Spalten mit diesem Abfragetyp verwendet, kann er kontinuierliche oder diskrete Spalten enthalten, die entweder vorhersagbar oder Eingabe sind.  
  
 Bei Verwendung mit [SELECT FROM &#60;Modell&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), **RangeMin**, **RangeMid**, und **RangeMax**  Funktionen geben die tatsächlichen Begrenzungswerte des angegebenen Buckets zurück. Wenn Sie z. B. eine Vorhersage für eine diskretisierte Spalte ausführen, gibt die Abfrage die vorhergesagte Bucketnummer in der diskretisierten Spalte zurück. Die **RangeMin**, **RangeMid**, und **RangeMax** Funktionen beschreiben den Bucket, der die Vorhersage angibt. Wenn die **RangeMax** Funktion, die mit einer PREDICTION JOIN-Anweisung verwendet wird, den Verweis auf skalare Spalte kann nur diskrete vorhersagbare Spalten enthalten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Mindest-, Höchst- und Durchschnittswerte für die kontinuierliche Spalte Yearly Income im Decision Tree-Miningmodell zurückgegeben.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
