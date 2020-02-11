---
title: '&gt;(Größer als) (DMX) | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9156525f463a3597c60421be7de0af64bd4f4ac7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074826"
---
# <a name="gt-greater-than-dmx"></a>&gt;(Größer als) DMX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt eine Vergleichsoperation aus, bei der ermittelt wird, ob der Wert eines DMX-Ausdrucks (Data Mining Extensions) größer als der Wert eines anderen DMX-Ausdrucks ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DMX_Expression > DMX_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *DMX_Expression*  
 Ein gültiger DMX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der TRUE enthält, wenn beide Parameter ungleich NULL sind und der erste Parameter einen Wert hat, der größer als der Wert des zweiten Parameters ist. Der boolesche Wert enthält FALSE, wenn beide Parameter ungleich NULL sind und der erste Parameter einen Wert aufweist, der gleich dem oder kleiner als der Wert des zweiten Parameters ist. Der boolesche Wert enthält einen NULL-Wert, wenn einer der Parameter oder beide Parameter ausgewertet einen NULL-Wert haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichs Operatoren &#40;DMX-&#41;](../dmx/operators-comparison.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
