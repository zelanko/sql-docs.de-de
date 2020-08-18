---
description: = (Ist gleich) (DMX)
title: = (Gleich) (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ba57583c8af1b739335abc27c33eaaf2ea54dc1f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413357"
---
# <a name="-equal-to-dmx"></a>= (Ist gleich) (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Führt einen Vergleich aus, bei dem ermittelt wird, ob der Wert eines DMX-Ausdrucks (Data Mining-Erweiterungen) gleich dem Wert eines anderen DMX-Ausdrucks ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DMX_Expression = DMX_Expression   
```  
  
#### <a name="parameters"></a>Parameter  
 *DMX_Expression*  
 Ein gültiger DMX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der TRUE enthält, wenn beide Parameter nicht NULL sind und der Wert des ersten Parameters gleich dem Wert des zweiten Parameters ist. Der boolesche Wert enthält FALSE, wenn beide Parameter nicht NULL sind und der Wert des ersten Parameters ungleich dem Wert des zweiten Parameters ist. Der boolesche Wert enthält einen NULL-Wert, wenn einer der Parameter oder beide Parameter ausgewertet einen NULL-Wert haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichs Operatoren &#40;DMX-&#41;](../dmx/operators-comparison.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
