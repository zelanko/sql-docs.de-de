---
description: IsDescendant (DMX)
title: Isnachfolger (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9fe1c150f243e78c379823427e9940bba3680cb1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88352646"
---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Zeigt an, ob der aktuelle Knoten ein untergeordneter Knoten des angegebenen Knotens ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein boolescher Typ.  
  
## <a name="remarks"></a>Bemerkungen  
 **Isnachfolger** wird nur in [&#62; Select from &#60;Model verwendet. Inhalt &#40;DMX-&#41;](../dmx/select-from-model-content-dmx.md) und [aus &#60;Modell&#62; auswählen. DIMENSION_CONTENT &#40;DMX-&#41;](../dmx/select-from-model-dimension-content-dmx.md) Abfragen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Fälle zurückgegeben, die Nachfolger des Knotens sind, der in der IsDescendant-Funktion angegeben ist.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
