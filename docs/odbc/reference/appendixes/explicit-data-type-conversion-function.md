---
title: Explizite Datentyp-Konvertierungsfunktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc229e2bef69069ba1fc5f8cb3077e592d959a55
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52521932"
---
# <a name="explicit-data-type-conversion-function"></a>Explizite Datentyp-Konvertierungsfunktion
Explizite datentypkonvertierung wird in SQL-Datentypdefinitionen angegeben.  
  
 Die ODBC-Syntax für die explizite Datentyp-Konvertierungsfunktion Konvertierungen nicht eingeschränkt. Die Gültigkeit des bestimmte Konvertierungen von einem Datentyp in einen anderen Datentyp wird von jeder Treiber-spezifische Implementierung bestimmt. Der Treiber, wie er in der systemeigenen Syntax die ODBC-Syntax übersetzt diese Konvertierungen abgelehnt, die, obwohl es zulässig, in der ODBC-Syntax wird von der Datenquelle nicht unterstützt werden. Der ODBC-Funktion **SQLGetInfo**, mit der Konvertierung bietet Optionen (z. B. SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH und So weiter), eine Möglichkeit, erkundigen Sie sich von der Datenquelle unterstützten Konvertierungen .  
  
 Das Format der **konvertieren** -Funktion ist:  
  
 **KONVERTIEREN (** *Value_exp*, _Data_type_**)**  
  
 Die Funktion gibt den Wert gemäß *Value_exp* konvertiert in den angegebenen *Data_type*, wobei *Data_type* ist eine der folgenden Schlüsselwörter:  
  
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
  
 Die ODBC-Syntax für die explizite Datentyp-Konvertierungsfunktion unterstützt Spezifikation des Formats der Konvertierung nicht. Wenn die Spezifikation der explizite Formate, die von der zugrunde liegenden Datenquelle unterstützt wird, muss ein Treiber einen Standardwert angeben oder Formatspezifikation zu implementieren.  
  
 Das Argument *Value_exp* können einen Spaltennamen an, das Ergebnis eine andere skalare Funktion oder ein numerischer oder die Zeichenfolge literal sein. Zum Beispiel:  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 die Ausgabe der CURDATE skalare Funktion konvertiert in eine Zeichenfolge.  
  
 Da ODBC nicht über einen Datentyp für die Rückgabe von Werten aus vorschreibt Skalarfunktionen (da die Funktionen, die häufig Daten datenquellenspezifische sind), Anwendungen sollten die CONVERT-Skalarfunktion nach Möglichkeit, um die datentypkonvertierung erzwingen verwenden.  
  
 Die folgenden beiden Beispiele veranschaulichen die Verwendung des der **konvertieren** Funktion. Diese Beispiele nehmen an, das Vorhandensein einer Tabelle, die Mitarbeiter, mit einer EMPNO-Spalte vom Typ SQL_SMALLINT und eine EMPNAME-Spalte vom Typ SQL_CHAR aufgerufen wird.  
  
 Wenn eine Anwendung die folgende SQL-Anweisung angibt:  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Ein Treiber für ORACLE übersetzt, die SQL-Anweisung:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Ein Treiber für SQL Server übersetzt, die SQL-Anweisung:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Wenn eine Anwendung die folgende SQL-Anweisung angibt:  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Ein Treiber für ORACLE übersetzt, die SQL-Anweisung:  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Ein Treiber für SQL Server übersetzt, die SQL-Anweisung:  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Ein Treiber für Ingres übersetzt, die SQL-Anweisung:  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
