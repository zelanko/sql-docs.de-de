---
title: Rangemax (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 08882071e142fa97139dc2a89adffaa8e5d5f738
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970665"
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Gibt das obere Ende des vorhergesagten Buckets zurück, der für eine diskretisierte Spalte ermittelt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Gilt für  
 Skalare Spalten.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein Skalarwert.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **RangeMax** -Funktion kann in SELECT-unter [schieden von &#60;Modell &#62; &#40;DMX-&#41;](../dmx/select-distinct-from-model-dmx.md) Abfragen verwendet werden. Wird der Verweis auf skalare Spalten mit diesem Abfragetyp verwendet, kann er kontinuierliche oder diskrete Spalten enthalten, die entweder vorhersagbar oder Eingabe sind.  
  
 Bei Verwendung mit [Select from &#60;Model&#62; Vorhersage Join &#40;DMX-&#41;](../dmx/select-from-model-prediction-join-dmx.md)werden die tatsächlichen Begrenzungs Werte des angegebenen Bucket von der **RangeMin**-, **RangeMid**-und **RangeMax** -Funktion zurückgegeben. Wenn Sie z. B. eine Vorhersage für eine diskretisierte Spalte ausführen, gibt die Abfrage die vorhergesagte Bucketnummer in der diskretisierten Spalte zurück. Die **RangeMin**-, **RangeMid**-und **RangeMax** -Funktionen beschreiben den Bucket, der in der Vorhersage angegeben wird. Wenn die **RangeMax** -Funktion mit einer Vorhersage JOIN-Anweisung verwendet wird, kann der Verweis auf eine skalare Spalte nur diskrete, vorhersagbare Spalten enthalten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Mindest-, Höchst- und Durchschnittswerte für die kontinuierliche Spalte Yearly Income im Decision Tree-Miningmodell zurückgegeben.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX-&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX-&#41;](../dmx/rangemin-dmx.md)  
  
  
