---
title: '&gt;= (Größer als oder gleich) (DMX) | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3615dc8b5de0e5057e2dedaa0077aae51ed87ebe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074791"
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= (Größer als oder gleich) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="see-also"></a>Siehe auch  
 [Vergleichsoperatoren &#40;DMX&#41;](../dmx/operators-comparison.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
