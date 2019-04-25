---
title: '- (Subtrahieren) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03ede2272de2c574909ed44bb0291b3c56911f0b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768730"
---
# <a name="--subtract-ssis-expression"></a>- (Subtrahieren) (SSIS-Ausdruck)
  Subtrahiert den zweiten numerischen Ausdruck vom ersten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
numeric_expression1 - numeric_expression2  
  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression1, numeric_expression2*  
 Jeder gültige Ausdruck mit einem numerischen Datentyp. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Die Ergebnistypen werden von den Datentypen der beiden Argumente bestimmt. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Hinweise  
 Schließen Sie den unären Minusausdruck in Klammern ein, um sicherzustellen, dass der Ausdruck in der richtigen Reihenfolge ausgewertet wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn einer der Operanden NULL ist, ist das Ergebnis NULL.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel werden numerische Literale subtrahiert.  
  
```  
5 - 6.09  
```  
  
 In diesem Beispiel wird der Wert in der **StandardCost** -Spalte vom Wert in der **ListPrice** -Spalte subtrahiert.  
  
```  
ListPrice - StandardCost  
```  
  
 In diesem Beispiel wird ein berechneter Wert von der **ListPrice** -Spalte subtrahiert. Die **Discount%** -Variable muss in eckige Klammern eingeschlossen werden, weil der Name das Zeichen % enthält. Weitere Informationen finden Sie unter [Bezeichner &#40;SSIS&#41;](identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
