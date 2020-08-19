---
description: '* Lik DMX'
title: '* Lik (DMX) | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3c7ef5a8893d29e2d20d31517c85abacfc4a3a9b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426282"
---
# <a name="-multiply-dmx"></a>* (Multiplikation) (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Führt eine arithmetische Operation aus, bei der eine Zahl mit einer anderen Zahl multipliziert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *Numeric_Expression*  
 Ein gültiger DMX-Ausdruck (Data Mining-Erweiterungen), der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert, der den Datentyp des Parameters aufweist, der in der Rangfolge höher eingestuft ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Beide Ausdrücke müssen denselben Datentyp haben, oder es muss möglich sein, einen Ausdruck implizit in den Datentyp des anderen Ausdrucks zu konvertieren. Wenn ein Ausdruck zu einem NULL-Wert ausgewertet wird, gibt der Operator einen NULL-Wert zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arithmetische Operatoren &#40;DMX-&#41;](../dmx/operators-arithmetic.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
