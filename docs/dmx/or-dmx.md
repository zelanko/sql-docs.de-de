---
title: oder (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9ce963b2322e19e4e3a98982a88f99d3546cabc2
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83668735"
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
  
## <a name="remarks"></a>Bemerkungen  
 Beide Argumente werden als boolesche Werte (0 als FALSE, anderenfalls TRUE) behandelt, bevor der Operator die logische Disjunktion ausführt. Wird eines der Argumente oder werden beide Argumente zu TRUE ausgewertet, gibt der Operator TRUE zurück Wenn *expression1* als true ausgewertet wird und *expression2* zu false ausgewertet wird, gibt der Operator true zurück.  
  
 Die folgende Tabelle verdeutlicht, wie die logische Disjunktion ausgeführt wird.  
  
|Expression1|Expression2|Rückgabewert ist|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Logische Operatoren &#40;DMX-&#41;](../dmx/operators-logical.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
