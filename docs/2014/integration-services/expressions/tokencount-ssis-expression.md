---
title: TOKENCOUNT (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6e90b37f594bf2dd80963d7acf7357a050a3e290
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62896697"
---
# <a name="tokencount-ssis-expression"></a>TOKENCOUNT (SSIS-Ausdruck)
  Gibt die Anzahl der Token in einer Zeichenfolge zurück, die durch die angegebenen Trennzeichen getrennte Token enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Eine Zeichenfolge, die durch Trennzeichen getrennte Token enthält.  
  
 *delimiter_string*  
 Eine Zeichenfolge, die Begrenzungszeichen enthält. „; ,“ enthält beispielsweise drei Begrenzungszeichen: ein Semikolon, ein Leerzeichen und ein Komma.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_I4  
  
## <a name="remarks"></a>Bemerkungen  
 Die folgenden Hinweise gelten für die TOKEN-Funktion:  
  
-   Die Trennzeichenfolge kann ein oder mehrere Trennzeichen enthalten.  
  
-   Führende Trennzeichen werden übersprungen.  
  
-   TOKENCOUNT kann nur mit dem DT_WSTR-Datentyp verwendet werden. Ein *character_expression* -Argument, das ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird implizit in den DT_WSTR-Datentyp umgewandelt, bevor TOKEN ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden.  
  
-   TOKENCOUNT gibt 0 (null) zurück, wenn character_expression NULL ist.  
  
-   Sie können Variablen und Spalten als Argumente für diesen Ausdruck verwenden.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Im folgenden Beispiel gibt die TOKENCOUNT-Funktion „3“ zurück, da die Zeichenfolge drei Token enthält: „01“, „12“, „2011“.  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 Im darauf folgenden Beispiel gibt die TOKENCOUNT-Funktion „4“ zurück, da vier Token („a“, „little“, „white“, „dog“) vorhanden sind.  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 Im folgenden Beispiel gibt die TOKENCOUNT-Funktion 1 zurück. Die Funktion analysiert die Eingabezeichenfolge für Trennzeichen, und da es in der Zeichenfolge keine gibt, fügt es die ganze Zeichenfolge als erstes Token hinzu.  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 Im folgenden Beispiel gibt die TOKENCOUNT-Funktion 4 zurück. Die Trennzeichenfolge in diesem Beispiel enthält 5 Trennzeichen. Die Eingabezeichenfolge enthält 4 Token: „a“, „little“, „white“, „dog“.  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 Im folgenden Beispiel gibt die TOKENCOUNT-Funktion 4 zurück. Es ignoriert alle führenden Leerzeichen.  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
