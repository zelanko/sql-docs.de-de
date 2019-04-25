---
title: ODER (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a57d0b1c7f1fa75504e786712029326fc958135
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62501811"
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ein logischer Operator, der eine logische Disjunktion zweier numerischer Ausdrücke ausführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>Parameter  
 *Expression1*  
 Ein gültiger DMX-Ausdruck (Data Mining-Erweiterungen), der einen numerischen Wert zurückgibt.  
  
 *Expression2*  
 Ein gültiger DMX-Ausdruck, der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der TRUE zurückgibt, wenn eines der Argumente oder beide Argumente zu TRUE ausgewertet werden; anderenfalls FALSE.  
  
## <a name="remarks"></a>Hinweise  
 Beide Argumente werden als boolesche Werte (0 als FALSE, anderenfalls TRUE) behandelt, bevor der Operator die logische Disjunktion ausführt. Wird eines der Argumente oder werden beide Argumente zu TRUE ausgewertet, gibt der Operator TRUE zurück Wenn *Expression1* auf "true" ausgewertet wird und *Expression2* zu FALSE ausgewertet wird, gibt der Operator "true" zurück.  
  
 Die folgende Tabelle verdeutlicht, wie die logische Disjunktion ausgeführt wird.  
  
|Expression1|Expression2|Rückgabewert|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logische Operatoren &#40;DMX&#41;](../dmx/operators-logical.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
