---
description: Dividieren (DMX)
title: Glie (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2249701d074f12e0fc4dc3383d2e62b31ac275f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414066"
---
# <a name="divide-dmx"></a>Dividieren (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Führt eine arithmetische Operation aus, die eine Zahl durch eine andere dividiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Parameter  
 *Dividend*  
 Ein gültiger DMX-Ausdruck (Data Mining-Erweiterungen), der einen numerischen Wert zurückgibt.  
  
 *Divisor*  
 Ein gültiger DMX-Ausdruck, der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert, der den Datentyp des Parameters aufweist, der in der Rangfolge höher eingestuft ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert, den dieser Operator zurückgibt, entspricht dem Quotienten des ersten und des zweiten Ausdrucks.  
  
 Beide Ausdrücke müssen denselben Datentyp haben, oder es muss möglich sein, einen Ausdruck implizit in den Datentyp des anderen Ausdrucks zu konvertieren. Wenn der Divisor ausgewertet den Wert NULL hat, löst der Operator einen Fehler aus. Wenn sowohl der Divisor als auch der Dividend ausgewertet den Wert NULL haben, gibt der Operator den Wert NULL zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arithmetische Operatoren &#40;DMX-&#41;](../dmx/operators-arithmetic.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)   
 [&#40;SSIS-Ausdruck Aufteilen&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;dividieren&#41; &#40;Transact-SQL-&#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
