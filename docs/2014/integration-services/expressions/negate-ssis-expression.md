---
title: '- (Negation) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 587ac12e6628104613d8b1457b02088e1baf4998
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52799842"
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
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
