---
title: '&amp; (Bitweises AND) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c17df738a3b8a97639a0c4097e01643c2e571119
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058746"
---
# <a name="amp-bitwise-and-ssis-expression"></a>&amp; (Bitweises AND) (SSIS-Ausdruck)
  Führt eine bitweise AND-Operation mit zwei ganzzahligen Werten aus. Jedes Bit des ersten Operanden wird mit dem entsprechenden Bit des zweiten Operanden verglichen. Wenn beide Bits 1 sind, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 festgelegt.  
  
 Beide Bedingungen müssen als Datentyp eine ganze Zahl mit Vorzeichen oder aber eine ganze Zahl ohne Vorzeichen aufweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a>Argumente  
 *integer_expression1, integer_expression2*  
 Ein gültiger Ausdruck eines integer-Datentyps mit oder ohne Vorzeichen. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Die Ergebnistypen werden von den Datentypen der beiden Argumente bestimmt. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine der Bedingungen NULL ist, lautet das Ergebnis des Ausdrucks NULL.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird eine bitweise AND-Operation mit den Spalten **NumberA** und **NumberB**ausgeführt. **NumberA** enthält 3 (0000011) und die Spalte **NumberB** enthält 7 (00000111).  
  
```  
NumberA & NumberB  
```  
  
 Der Ausdruck wird zu 3 (00000011) ausgewertet.  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000011  
  
 In diesem Beispiel wird eine bitweise AND-Operation mit den Spalten **ReorderPoint** und **SafetyStockLevel** ausgeführt.  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 Falls **ReorderPoint** gleich 10 und **SafetyStockLevel** gleich 8 ist, wird der Ausdruck zu 8 (00001000) ausgewertet.  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001000  
  
 In diesem Beispiel wird eine bitweise AND-Operation mit zwei ganzen Zahlen ausgeführt.  
  
```  
3 & 5   
```  
  
 Der Ausdruck wird zu 1 (00000001) ausgewertet.  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000001  
  
## <a name="see-also"></a>Siehe auch  
 [& & &#40;Logisches AND&#41; &#40;SSIS-Ausdruck&#41;](logical-and-ssis-expression.md)   
 [Operatorrangfolge und Assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  