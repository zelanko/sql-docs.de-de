---
title: nicht (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 98c40dba282c82f124d4e4ac009a046a44a283cb
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971631"
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
  
## <a name="remarks"></a>Bemerkungen  
 Das Argument wird als boolescher Wert (0 als FALSE, anderenfalls TRUE) behandelt, bevor der Operator die logische Negation ausführt. Wenn *expression1* den Wert true hat, gibt der Operator false zurück. Wenn *expression1* den Wert false hat, gibt der Operator true zurück. Die folgende Tabelle verdeutlicht, wie die logische Konjunktion ausgeführt wird.  
  
|Expression1|Rückgabewert ist|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logische Operatoren &#40;DMX-&#41;](../dmx/operators-logical.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
