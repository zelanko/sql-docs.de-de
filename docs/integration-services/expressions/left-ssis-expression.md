---
title: LEFT (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f65ac38bd8ce47d368720a0b3b4882be08a6db21
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="left-ssis-expression"></a>LEFT (SSIS-Ausdruck)
  Gibt die angegebene Anzahl von Zeichen ab der äußersten linken Position des angegebenen Zeichenausdrucks zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Ein Zeichenausdruck, von dem Zeichen extrahiert werden sollen.  
  
 *number*  
 Ein ganzzahliger Ausdruck, der die Anzahl der zurückzugebenden Zeichen angibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Wenn *number* größer ist als die Länge von *character_expression*, gibt die Funktion *character_expression*zurück.  
  
 Falls *number* gleich Null ist, gibt die Funktion eine leere Zeichenfolge zurück.  
  
 Falls *number* eine negative Zahl ist, gibt die Funktion einen Fehler zurück.  
  
 Für das *number* -Argument sind Variablen und Spalten möglich.  
  
 LEFT kann nur mit dem DT_WSTR-Datentyp verwendet werden. Ein *character_expression* -Argument, das ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird implizit in den DT_WSTR-Datentyp umgewandelt, bevor LEFT ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services-Datentypen](../../integration-services/data-flow/integration-services-data-types.md) und [Cast &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 LEFT gibt ein NULL-Ergebnis zurück, wenn eines der Argumente NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Im folgenden Beispiel wird ein Zeichenfolgenliteral verwendet. Als Ergebnis wird `"Mountain"`zurückgegeben.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [RIGHT &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/right-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
