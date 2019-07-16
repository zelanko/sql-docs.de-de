---
title: '- (Subtrahieren) (DMX) | Microsoft-Dokumentation'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1af4739743385d786f8b7c6a5daa5f316543c008
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079022"
---
# <a name="--subtract-dmx"></a>- (Subtraktion) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt eine arithmetische Operation aus, die eine Zahl von einer anderen subtrahiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric_Expression - Numeric_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *Numeric_expression*  
 Ein gültiger DMX-Ausdruck (Data Mining-Erweiterungen), der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert, der den Datentyp des Parameters aufweist, der in der Rangfolge höher eingestuft ist.  
  
## <a name="remarks"></a>Hinweise  
 Beide Ausdrücke müssen denselben Datentyp haben, oder es muss möglich sein, einen Ausdruck implizit in den Datentyp des anderen Ausdrucks zu konvertieren. Hat ein Ausdruck als Ergebnis den Wert NULL, gibt der Operator das Ergebnis des anderen Ausdrucks zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Arithmetische Operatoren &#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
