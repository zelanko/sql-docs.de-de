---
title: ^ (Bitweises exklusives OR) (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- bitwise exclusive OR (^)
ms.assetid: 6ac53cab-29c4-4835-9f87-371b058b2f38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb2a9c0ebdc6616940f09c2b8770dbefa6ca15e6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201270"
---
# <a name="-bitwise-exclusive-or-ssis-expression"></a>^ (Bitweises exklusives OR) (SSIS-Ausdruck)
  Führt eine bitweise exklusive OR-Operation mit zwei ganzzahligen Werten aus. Jedes Bit des ersten Operanden wird mit dem entsprechenden Bit des zweiten Operanden verglichen. Wenn ein Bit 0 und das andere 1 ist, wird das entsprechende Ergebnisbit auf 1 festgelegt. Wenn beide Bits 0 oder 1 sind, wird das entsprechende Ergebnisbit auf 0 festgelegt.  
  
 Beide Bedingungen müssen als Datentyp eine ganze Zahl mit Vorzeichen oder aber eine ganze Zahl ohne Vorzeichen aufweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
integer_expression1 ^ integer_expression2  
  
```  
  
## <a name="arguments"></a>Argumente  
 *integer_expression1, integer_expression2*  
 Ein gültiger Ausdruck eines integer-Datentyps mit oder ohne Vorzeichen. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Die Ergebnistypen werden von den Datentypen der beiden Argumente bestimmt. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine der Bedingungen NULL ist, lautet das Ergebnis des Ausdrucks NULL.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird eine bitweise exklusive OR-Operation mit den Variablen **NumberA** und **NumberB**ausgeführt. **NumberA** enthält 3 (00000011) und **NumberB** enthält 7 (00000111).  
  
```  
@NumberA ^ @NumberB  
```  
  
 Der Ausdruck wird zu 4 (00000100) ausgewertet.  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000100  
  
 In diesem Beispiel wird eine bitweise exklusive OR-Operation mit den Spalten **ReorderPoint** und **SafetyStockLevel** ausgeführt.  
  
```  
ReorderPoint ^ SafetyStockLevel  
```  
  
 Falls **ReorderPoint** gleich 10 und **SafetyStockLevel** gleich 8 ist, wird der Ausdruck zu 2 (00000010) ausgewertet.  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00000010  
  
 In diesem Beispiel wird eine bitweise exklusive OR-Operation mit zwei ganzen Zahlen ausgeführt.  
  
```  
3 ^ 5   
```  
  
 Der Ausdruck wird zu 6 (00000110) ausgewertet.  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000110  
  
## <a name="see-also"></a>Siehe auch  
 [&#124;&#124;&#40;Logisches OR&#41; &#40;SSIS-Ausdruck&#41;](logical-or-ssis-expression.md)   
 [&#124;&#40;Bitweises inklusives OR&#41; &#40;SSIS-Ausdruck&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [Operatorrangfolge und Assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
