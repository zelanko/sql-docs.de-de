---
description: Explizite Datentyp-Konvertierungsfunktion
title: Explizite Datentyp-Konvertierungs Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: da897469d26cd0403dc023cfcd3f3e03bfceeba4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466187"
---
# <a name="explicit-data-type-conversion-function"></a>Explizite Datentyp-Konvertierungsfunktion
Eine explizite Datentyp Konvertierung wird in Bezug auf SQL-Datentyp Definitionen angegeben.  
  
 Die ODBC-Syntax für die explizite Datentyp-Konvertierungs Funktion schränkt Konvertierungen nicht ein. Die Gültigkeit spezifischer Konvertierungen eines Datentyps in einen anderen Datentyp wird von jeder treiberspezifischen Implementierung bestimmt. Der Treiber lehnt beim Konvertieren der ODBC-Syntax in die native Syntax diese Konvertierungen ab, die in der ODBC-Syntax zulässig sind, aber nicht von der Datenquelle unterstützt werden. Die ODBC-Funktion **SQLGetInfo**mit den Konvertierungsoptionen (z. b. SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH usw.) bietet eine Möglichkeit, von Konvertierungen zu Fragen, die von der Datenquelle unterstützt werden.  
  
 Die **Convert** -Funktion hat folgendes Format:  
  
 **Konvertieren (** _value_exp_ _data_type_**)**  
  
 Die-Funktion gibt den von *value_exp* angegebenen Wert zurück, der in den angegebenen *data_type*konvertiert wurde, wobei *data_type* eines der folgenden Schlüsselwörter ist:  

:::row:::
    :::column:::
        SQL_BIGINT  
        SQL_BINARY  
        SQL_BIT  
        SQL_CHAR  
        SQL_DATE  
        SQL_DECIMAL  
        SQL_DOUBLE  
        SQL_FLOAT  
        SQL_GUID  
        SQL_INTEGER  
        SQL_INTERVAL_DAY  
        SQL_INTERVAL_DAY_TO_HOUR  
    :::column-end:::
    :::column:::
        SQL_INTERVAL_DAY_TO_MINUTE  
        SQL_INTERVAL_DAY_TO_SECOND  
        SQL_INTERVAL_HOUR  
        SQL_INTERVAL_HOUR_TO_MINUTE  
        SQL_INTERVAL_HOUR_TO_SECOND  
        SQL_INTERVAL_MINUTE  
        SQL_INTERVAL_MINUTE_TO_SECOND  
        SQL_INTERVAL_MONTH  
        SQL_INTERVAL_SECOND  
        SQL_INTERVAL_YEAR  
        SQL_INTERVAL_YEAR_TO_MONTH  
        SQL_LONGVARBINARY  
    :::column-end:::
    :::column:::
        SQL_LONGVARCHAR  
        SQL_NUMERIC  
        SQL_REAL  
        SQL_SMALLINT  
        SQL_TIME  
        SQL_TIMESTAMP  
        SQL_TINYINT  
        SQL_VARBINARY  
        SQL_VARCHAR  
        SQL_WCHAR  
        SQL_WLONGVARCHAR  
        SQL_WVARCHAR  
    :::column-end:::
:::row-end:::

 Die ODBC-Syntax für die explizite Datentyp-Konvertierungs Funktion unterstützt keine Angabe des Konvertierungs Formats. Wenn die Spezifikation expliziter Formate von der zugrunde liegenden Datenquelle unterstützt wird, muss ein Treiber einen Standardwert angeben oder die Format Spezifikation implementieren.  
  
 Das Argument *value_exp* kann ein Spaltenname, das Ergebnis einer anderen Skalarfunktion oder ein numerisches oder ein Zeichenfolgenliteralwert sein. Beispiel:  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 Konvertiert die Ausgabe der scaldate-Skalarfunktion in eine Zeichenfolge.  
  
 Da ODBC keinen Datentyp für Rückgabewerte von skalaren Funktionen zuweist (da die Funktionen häufig Datenquellen spezifisch sind), sollten Anwendungen die Convert-Skalarfunktion verwenden, wenn dies möglich ist, um die Datentyp Konvertierung zu erzwingen.  
  
 Die folgenden beiden Beispiele veranschaulichen die Verwendung der **Convert** -Funktion. In diesen Beispielen wird davon ausgegangen, dass eine Tabelle mit dem Namen Employees und eine EmpNo-Spalte vom Typ SQL_SMALLINT und eine EmpName-Spalte vom Typ SQL_CHAR vorhanden ist.  
  
 Wenn eine Anwendung die folgende SQL-Anweisung angibt:  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Ein Treiber für Oracle übersetzt die SQL-Anweisung in:  
  
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
  
-   Ein Treiber für Oracle übersetzt die SQL-Anweisung in:  
  
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
