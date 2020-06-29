---
title: SUBSTRING (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SUBSTRING function
- part of expression returned [Integration Services]
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f69a2fcfaca55b77d828ece6cd5309c2ebc08f2
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428077"
---
# <a name="substring-ssis-expression"></a>SUBSTRING (SSIS-Ausdruck)
  Gibt den Teil eines Zeichenausdrucks zurück, der an der angegebenen Position beginnt und die angegebene Länge besitzt. Der *position* -Parameter und der *length* -Parameter müssen zu einer ganzen Zahl ausgewertet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Ein Zeichenausdruck, von dem Zeichen extrahiert werden sollen.  
  
 *position*  
 Eine ganze Zahl, die den Beginn der Teilzeichenfolge angibt.  
  
 *length*  
 Eine ganze Zahl, die die Länge der Teilzeichenfolge als Anzahl von Zeichen angibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_WSTR  
  
## <a name="remarks"></a>Bemerkungen  
 SUBSTRING verwendet einen einsbasierten Index. Falls *position* 1 ist, beginnt die Teilzeichenfolge mit dem ersten Zeichen in *character_expression*.  
  
 SUBSTRING kann nur mit dem DT_WSTR-Datentyp verwendet werden. Ein *character_expression* -Argument, das ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird implizit in den DT_WSTR-Datentyp umgewandelt, bevor SUBSTRING ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services-Datentypen](../data-flow/integration-services-data-types.md) und [CAST &#40;SSIS-Ausdruck&#41;](cast-ssis-expression.md).  
  
 SUBSTRING gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Für alle Argumente des Ausdrucks können Variablen und Spalten verwendet werden.  
  
 Das *length* -Argument kann länger als die Zeichenfolge sein. In diesem Fall gibt die Funktion die restliche Zeichenfolge zurück.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel werden zwei Zeichen eines Zeichenfolgenliterals zurückgegeben, und zwar beginnend mit Zeichen 4. Als Ergebnis wird "ph" zurückgegeben.  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 In diesem Beispiel wird der Rest eines Zeichenfolgenliterals zurückgegeben, und zwar beginnend mit dem vierten Zeichen. Als Ergebnis wird "phant" zurückgegeben. Es ist kein Fehler, wenn das *length* -Argument länger als die Zeichenfolge ist.  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 In diesem Beispiel wird der erste Buchstabe der **MiddleName** -Spalte zurückgegeben.  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 In diesem Beispiel werden Variablen für die Argumente *position* und *length* verwendet. Falls **Start** 1 und **Length** 5 ist, gibt die Funktion die ersten fünf Zeichen der **Name** -Spalte zurück.  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 In diesem Beispiel werden die letzten vier Zeichen der **PostalCode** -Variable zurückgegeben, und zwar beginnend mit dem sechsten Zeichen.  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 In diesem Beispiel wird eine leere Zeichenfolge aus einem Zeichenfolgenliteral zurückgegeben.  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
