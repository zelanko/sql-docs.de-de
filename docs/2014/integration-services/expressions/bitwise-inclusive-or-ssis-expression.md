---
title: '| (Bitweises inklusives OR) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- '| (bitwise inclusive OR)'
- bitwise inclusive OR (|)
ms.assetid: 4dce9eb2-3680-4adc-81a3-816ea52cef49
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e168433f7f7001037ac1d5360cf4115ff246f228
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054160"
---
# <a name="-bitwise-inclusive-or-ssis-expression"></a>| (Bitweises inklusives OR) (SSIS-Ausdruck)
  Führt eine bitweise OR-Operation mit zwei ganzzahligen Werten aus. Jedes Bit des ersten Operanden wird mit dem entsprechenden Bit des zweiten Operanden verglichen. Wenn eines der Bits 1 ist, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 (null) festgelegt.  
  
 Beide Bedingungen müssen als Datentyp eine ganze Zahl mit Vorzeichen oder aber eine ganze Zahl ohne Vorzeichen aufweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
integer_expression1 | integer_expression2  
  
```  
  
## <a name="arguments"></a>Argumente  
 *integer_expression1, integer_expression2*  
 Ein gültiger Ausdruck eines integer-Datentyps mit oder ohne Vorzeichen. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Die Ergebnistypen werden von den Datentypen der beiden Argumente bestimmt. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine der Bedingungen NULL ist, lautet das Ergebnis des Ausdrucks NULL.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird eine bitweise inklusive OR-Operation mit den Variablen **NumberA** und **NumberB**ausgeführt. **NumberA** enthält 3 (00000011) und **NumberB** enthält 9 (00001001).  
  
```  
@NumberA | @NumberB  
```  
  
 Der Ausdruck wird zu 11 (00001011) ausgewertet.  
  
 00000011  
  
 00001001  
  
 ----------\-  
  
 00001011  
  
 In diesem Beispiel wird eine bitweise inklusive OR-Operation mit den Spalten **ReorderPoint** und **SafetyStockLevel** ausgeführt.  
  
```  
ReorderPoint | SafetyStockLevel  
```  
  
 Falls **ReorderPoint** gleich 10 und **SafetyStockLevel** gleich 8 ist, wird der Ausdruck zu 10 (00001010) ausgewertet.  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001010  
  
 In diesem Beispiel wird eine bitweise inklusive OR-Operation mit zwei ganzen Zahlen ausgeführt.  
  
```  
3 | 5   
```  
  
 Der Ausdruck wird zu 7 (00000111) ausgewertet.  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000111  
  
## <a name="see-also"></a>Siehe auch  
 [&#124;&#124;&#40;Logisches OR&#41; &#40;SSIS-Ausdruck&#41;](logical-or-ssis-expression.md)   
 [^ &#40;Bitweises exklusives OR&#41; &#40;SSIS-Ausdruck&#41;](bitwise-exclusive-or-ssis-expression.md)   
 [Operatorrangfolge und Assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
