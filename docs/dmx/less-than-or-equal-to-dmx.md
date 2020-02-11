---
title: '&lt;= (Kleiner als oder gleich) (DMX) | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8d88c4b986ab05ab3bd9e90308257dd94b9e6abf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008340"
---
# <a name="lt-less-than-or-equal-to-dmx"></a>&lt;= (Kleiner als oder gleich) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt einen Vergleich aus, bei dem ermittelt wird, ob der Wert eines DMX-Ausdrucks (Data Mining-Erweiterungen) kleiner als der oder gleich dem Wert eines anderen DMX-Ausdrucks ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DMX_Expression <= DMX_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *DMX_Expression*  
 Ein gültiger DMX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der TRUE enthält, wenn beide Parameter nicht NULL sind und der Wert des ersten Parameters kleiner gleich dem Wert des zweiten Parameters ist. Der boolesche Wert enthält FALSE, wenn beide Parameter nicht NULL sind und der Wert des ersten Parameters größer als der Wert des zweiten Parameters ist. Der boolesche Wert enthält einen NULL-Wert, wenn einer der Parameter oder beide Parameter ausgewertet einen NULL-Wert haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichs Operatoren &#40;DMX-&#41;](../dmx/operators-comparison.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
