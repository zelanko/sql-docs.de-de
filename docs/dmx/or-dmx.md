---
description: OR (DMX)
title: oder (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 86a9aede9f1b9b12f465fa52b0343cf22c04b295
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88395436"
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
  
## <a name="remarks"></a>Bemerkungen  
 Beide Argumente werden als boolesche Werte (0 als FALSE, anderenfalls TRUE) behandelt, bevor der Operator die logische Disjunktion ausführt. Wird eines der Argumente oder werden beide Argumente zu TRUE ausgewertet, gibt der Operator TRUE zurück Wenn *expression1* als true ausgewertet wird und *expression2* zu false ausgewertet wird, gibt der Operator true zurück.  
  
 Die folgende Tabelle verdeutlicht, wie die logische Disjunktion ausgeführt wird.  
  
|Expression1|Expression2|Rückgabewert ist|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|false|true|  
|false|TRUE|TRUE|  
|false|false|false|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logische Operatoren &#40;DMX-&#41;](../dmx/operators-logical.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
