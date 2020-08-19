---
description: NOT (DMX)
title: nicht (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 03a8ea859160af36b9c822bf01c4197e8b4c3175
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426262"
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
|true|false|  
|false|true|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logische Operatoren &#40;DMX-&#41;](../dmx/operators-logical.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
