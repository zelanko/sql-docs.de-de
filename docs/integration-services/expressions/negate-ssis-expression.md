---
title: '- (Negation) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: 9b91bd3dabde220ef8f31981e6a3df71e4b85bd3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47829704"
---
# <a name="--negate-ssis-expression"></a>- (Negation) (SSIS-Ausdruck)
  Negiert einen numerischen Ausdruck.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Jeder gültige Ausdruck mit einem numerischen Datentyp. Nur numerische Datentypen mit Vorzeichen werden unterstützt. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt den Datentyp von *numeric_expression*zurück.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird der Wert der **Counter** -Variablen negiert und das numerische Literal 50 hinzugefügt.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Operatorenrangfolge und -assoziativität](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
