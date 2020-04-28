---
title: IsInNode (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6e4c7df84bc7bf3a4804db76d952b1219100ef5a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008360"
---
# <a name="isinnode-dmx"></a>IsInNode (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Zeigt an, ob der angegebene Knoten den aktuellen Fall enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsInNode(<NodeID>)  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein boolescher Typ.  
  
## <a name="remarks"></a>Bemerkungen  
 **IsInNode** wird nur in [&#62; Select from &#60;Model verwendet. Fälle &#40;DMX-&#41;](../dmx/select-from-model-cases-dmx.md) und [Wählen aus &#60;Modell&#62; aus. SAMPLE_CASES &#40;DMX-&#41;](../dmx/select-from-model-sample-cases-dmx.md) Abfragen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Fälle zurückgegeben, die zum Erstellen des Modells verwendet wurden, das mit dem in der IsInNode-Funktion angegebenen Knoten verknüpft ist.  
  
```  
Select * from [TM Decision Tree].Cases  
WHERE IsInNode('0')  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
