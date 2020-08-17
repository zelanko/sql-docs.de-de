---
description: '&gt;= (Größer als oder gleich) (DMX)'
title: '&gt;= (Größer als oder gleich) (DMX) | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c34473ee7d8334ae332ce71bc44f94bcfdaee598
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353076"
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= (Größer als oder gleich) (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Führt eine Vergleichsoperation aus, bei der ermittelt wird, ob der Wert eines DMX-Ausdrucks (Data Mining Extensions) größer oder gleich dem Wert eines anderen DMX-Ausdrucks ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DMX_Expression >= DMX_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *DMX_Expression*  
 Ein gültiger DMX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der TRUE enthält, wenn beide Parameter nicht NULL sind und der Wert des ersten Parameters größer gleich dem Wert des zweiten Parameters ist. Der boolesche Wert enthält FALSE, wenn beide Parameter nicht NULL sind und der Wert des ersten Parameters kleiner als der Wert des zweiten Parameters ist. Der boolesche Wert enthält einen NULL-Wert, wenn einer der Parameter oder beide Parameter ausgewertet einen NULL-Wert haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichs Operatoren &#40;DMX-&#41;](../dmx/operators-comparison.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
