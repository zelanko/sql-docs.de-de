---
title: Explizite Datentypkonvertierungsfunktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2de8a8cb6177e9210e8d48c0ce097d13c9a276fd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306991"
---
# <a name="explicit-data-type-conversion-function"></a>Explizite Datentyp-Konvertierungsfunktion
Die explizite Datentypkonvertierung wird in Bezug auf SQL-Datentypdefinitionen angegeben.  
  
 Die ODBC-Syntax für die explizite Datentypkonvertierungsfunktion schränkt Konvertierungen nicht ein. Die Gültigkeit bestimmter Konvertierungen eines Datentyps in einen anderen Datentyp wird von jeder treiberspezifischen Implementierung bestimmt. Der Treiber lehnt beim Übersetzen der ODBC-Syntax in die systemeigene Syntax jene Konvertierungen ab, die zwar in der ODBC-Syntax legal sind, aber von der Datenquelle nicht unterstützt werden. Die ODBC-Funktion **SQLGetInfo**mit den Konvertierungsoptionen (z. B. SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH usw.) bietet eine Möglichkeit, sich nach Konvertierungen zu erkundigen, die von der Datenquelle unterstützt werden.  
  
 Das Format der **CONVERT-Funktion** ist:  
  
 **CONVERT(** _value_exp_, _data_type_**)**  
  
 Die Funktion gibt den von *value_exp* angegebenen Wert zurück, der in die angegebene *data_type*konvertiert wird, wobei *data_type* eines der folgenden Schlüsselwörter ist:  
  
|||  
|-|-|  
|SQL_BIGINT|SQL_INTERVAL_HOUR_TO_MINUTE|  
|SQL_BINARY|SQL_INTERVAL_HOUR_TO_SECOND|  
|SQL_BIT|SQL_INTERVAL_MINUTE_TO_SECOND|  
|SQL_CHAR|SQL_LONGVARBINARY|  
|SQL_DECIMAL|SQL_LONGVARCHAR|  
|SQL_DOUBLE|SQL_NUMERIC|  
|SQL_FLOAT|SQL_REAL|  
|SQL_GUID|SQL_SMALLINT|  
|SQL_INTEGER|SQL_DATE|  
|SQL_INTERVAL_MONTH|SQL_TIME|  
|SQL_INTERVAL_YEAR|SQL_TIMESTAMP|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_TINYINT|  
|SQL_INTERVAL_DAY|SQL_VARBINARY|  
|SQL_INTERVAL_HOUR|SQL_VARCHAR|  
|SQL_INTERVAL_MINUTE|SQL_WCHAR|  
|SQL_INTERVAL_SECOND|SQL_WLONGVARCHAR|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_WVARCHAR|  
|SQL_INTERVAL_DAY_TO_MINUTE||  
|SQL_INTERVAL_DAY_TO_SECOND||  
  
 Die ODBC-Syntax für die explizite Datentypkonvertierungsfunktion unterstützt keine Spezifikation des Konvertierungsformats. Wenn die Spezifikation expliziter Formate von der zugrunde liegenden Datenquelle unterstützt wird, muss ein Treiber einen Standardwert angeben oder eine Formatspezifikation implementieren.  
  
 Das Argument *value_exp* kann ein Spaltenname, das Ergebnis einer anderen Skalarfunktion oder ein numerisches oder Zeichenfolgenliteral sein. Beispiel:  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 konvertiert die Ausgabe der CURDATE Skalarfunktion in eine Zeichenfolge.  
  
 Da ODBC keinen Datentyp für Rückgabewerte aus skalaren Funktionen anlegt (da die Funktionen häufig datenquellenspezifisch sind), sollten Anwendungen nach Möglichkeit die scalar-Funktion CONVERT verwenden, um die Datentypkonvertierung zu erzwingen.  
  
 Die folgenden beiden Beispiele veranschaulichen die Verwendung der **CONVERT-Funktion.** In diesen Beispielen wird das Vorhandensein einer Tabelle mit dem Namen EMPLOYEES mit einer EMPNO-Spalte vom Typ SQL_SMALLINT und einer EMPNAME-Spalte vom Typ SQL_CHAR angenommen.  
  
 Wenn eine Anwendung die folgende SQL-Anweisung angibt:  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Ein Treiber für ORACLE übersetzt die SQL-Anweisung in:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Ein Treiber für SQL Server übersetzt die SQL-Anweisung in:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Wenn eine Anwendung die folgende SQL-Anweisung angibt:  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Ein Treiber für ORACLE übersetzt die SQL-Anweisung in:  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Ein Treiber für SQL Server übersetzt die SQL-Anweisung in:  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Ein Treiber für Ingres übersetzt die SQL-Anweisung in:  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
