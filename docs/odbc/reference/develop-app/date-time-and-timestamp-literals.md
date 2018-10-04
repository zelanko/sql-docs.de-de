---
title: Date, Time und Timestampliterale | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], literals
ms.assetid: 2b42a52a-6353-494c-a179-3a7533cd729f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa7fb107e67d529c656a49b271744757a1a73746
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651318"
---
# <a name="date-time-and-timestamp-literals"></a>Datums-, Zeit- und Zeitstempelliterale
Die Escapesequenz für Datum, Uhrzeit und timestampliterale lautet  
  
 **{***-Typ* **"** *Wert* **'}**   
  
 wo *Literal-Typ* ist einer der Werte in der folgenden Tabelle aufgeführt.  
  
|*Literal-Typ*|Bedeutung|Formatieren von *Wert*|  
|---------------------|-------------|-----------------------|  
|**d**|date|*yyyy*-*mm*-*dd*|  
|**t**|Uhrzeit *|*Hh*:*mm*:*ss*[1]|  
|**Terminaldienste**|Timestamp|*Yyyy*-*mm*-*TT* *Hh*:*mm*:*ss*[.*f...*] [1]|  
  
 [1] die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in einem Zeichenfolgenliteral mit einer Komponente für Sekunden Uhrzeit oder Zeitstempel Intervall ist abhängig von der Genauigkeit, wie in das Deskriptorfeld SQL_DESC_PRECISION enthalten. (Weitere Informationen finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Weitere Informationen zu dem Datum, Uhrzeit und Timestamp-Escapesequenzen finden Sie unter [Date, Time und Timestamp-Escapesequenzen](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) in Anhang C: SQL-Grammatik.  
  
 Z. B. aktualisieren beide der folgenden SQL-Anweisungen das öffnende Datum der Bestellung 1023 in der Orders-Tabelle. Die erste Anweisung verwendet die Escape-Sequenz-Syntax. Die zweite Anweisung verwendet die systemeigene Oracle Rdb-Syntax für die DATE-Spalte, und es ist nicht interoperabel.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 Die Escapesequenz für ein Datum, Uhrzeit oder Zeitstempel-literal kann auch in eine Zeichenvariable auf ein Datum, Uhrzeit oder Zeitstempelparameter gebunden platziert werden. Der folgende Code verwendet beispielsweise einen Date-Parameter, die an eine Zeichenvariable gebunden öffnende Datum das Bestellung 1023 in der Orders-Tabelle zu aktualisieren:  
  
```  
SQLCHAR      OpenDate[56]; // The size of a date literal is 55.  
SQLINTEGER   OpenDateLenOrInd = SQL_NTS;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_TYPE_DATE, 0, 0,  
                  OpenDate, sizeof(OpenDate), &OpenDateLenOrInd);  
  
// Place the date in the OpenDate variable. In addition to the escape  
// sequence shown, it would also be possible to use either of the  
// strings "{d '1995-01-15'}" and "15-Jan-1995", although the latter  
// is data source-specific.  
strcpy_s( (char*) OpenDate, _countof(OpenDate), "{d '1995-01-15'}");  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Orders SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Es ist jedoch in der Regel effizienter, den Parameter direkt auf eine Datumsstruktur binden:  
  
```  
SQL_DATE_STRUCT   OpenDate;  
SQLINTEGER        OpenDateInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &OpenDate, 0, &OpenDateLen);  
  
// Place the date in the dsOpenDate structure.  
OpenDate.year = 1995;  
OpenDate.month = 1;  
OpenDate.day = 15;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Employee SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Um zu bestimmen, ob ein Treiber die ODBC-Escapesequenzen für Datum, Uhrzeit oder zeitstempelliterale unterstützt, eine Anwendung ruft **SQLGetTypeInfo**. Wenn die Datenquelle einen Datentyp für Datum, Uhrzeit oder Zeitstempel unterstützt, muss es auch die entsprechende Escapesequenz unterstützen.  
  
 Datenquellen können auch die Datetime-Literale, die in der ANSI SQL-92-Spezifikation definiert unterstützen, die sich von der ODBC-Escapesequenzen für Datum, Uhrzeit oder zeitstempelliterale sind. Um zu bestimmen, ob eine Datenquelle die ANSI-Literale unterstützt, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Um zu bestimmen, ob ein Treiber die ODBC-Escapesequenzen für Intervall-Literale unterstützt, eine Anwendung ruft **SQLGetTypeInfo**. Wenn die Datenquelle einen Datetime-Intervall-Datentyp unterstützt, muss es auch die entsprechende Escapesequenz unterstützen.  
  
 Datenquellen können auch die Datetime-Literale, die in der ANSI SQL-92-Spezifikation definiert unterstützen, die sich von den ODBC-Escapesequenzen für Datetime-Intervall-Literale sind. Um zu bestimmen, ob eine Datenquelle die ANSI-Literale unterstützt, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_ANSI_SQL_DATETIME_LITERALS.
