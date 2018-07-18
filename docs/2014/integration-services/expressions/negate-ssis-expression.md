---
title: '- (Negation) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aceb64965279799f8e682b070752b25bec0eb37b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215610"
---
# <a name="--negate-ssis-expression"></a>- (Negation) (SSIS-Ausdruck)
  Negiert einen numerischen Ausdruck.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Jeder gültige Ausdruck mit einem numerischen Datentyp. Nur numerische Datentypen mit Vorzeichen werden unterstützt. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt den Datentyp von *numeric_expression*zurück.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird der Wert der **Counter** -Variablen negiert und das numerische Literal 50 hinzugefügt.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge und Assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
