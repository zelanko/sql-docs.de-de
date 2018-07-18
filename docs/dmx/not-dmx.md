---
title: KEINE (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 053eb905edb1379bfdc40ec010dc6d4efadcba26
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037908"
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ein logischer Operator, der eine logische Negation für einen numerischen Ausdruck ausführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Parameter  
 *Expression1*  
 Ein gültiger DMX-Ausdruck, der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der FALSE zurückgibt, wenn das Argument zu TRUE ausgewertet wird; anderenfalls FALSE.  
  
## <a name="remarks"></a>Hinweise  
 Das Argument wird als boolescher Wert (0 als FALSE, anderenfalls TRUE) behandelt, bevor der Operator die logische Negation ausführt. Wenn *Expression1* ist "true", gibt der Operator "false" zurück. Wenn *Expression1* ist "false", der Operator gibt "true" zurück. Die folgende Tabelle verdeutlicht, wie die logische Konjunktion ausgeführt wird.  
  
|Expression1|Rückgabewert|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logische Operatoren &#40;DMX&#41;](../dmx/operators-logical.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
