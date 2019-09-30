---
title: ~ (Bitweises NOT) (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9ac40997cd2d9962d067d181a66e9614de477d1
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297683"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (Bitweises NOT) (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Führt eine bitweise Negation einer ganzen Zahl aus. Dieser Operator kann auf integer-Datentypen mit und ohne Vorzeichen angewendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Argumente  
 *integer_expression*  
 Ein beliebiger gültiger Ausdruck eines integer-Datentyps. *integer*_*expression* ist eine ganze Zahl, die für die bitweise Operation in eine binäre Zahl transformiert wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt den Datentyp von *integer_expression*zurück.  
  
## <a name="remarks"></a>Remarks  
 None  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird eine bitweise ~ (NOT)-Operation für die Zahl 170 (0000 0000 1010 1010) ausgeführt. Diese Zahl ist eine ganze Zahl mit Vorzeichen.  
  
```  
  
~ 170  
```  
  
 Der Ausdruck wird zu -170 (1111111101010101) ausgewertet.  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatorenrangfolge und -assoziativität](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
