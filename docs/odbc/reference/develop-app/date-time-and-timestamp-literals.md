---
title: Datums-, Uhrzeit- und Zeitstempelliterale | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d899938be4689daab50a773f189219a797794006
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288296"
---
# <a name="date-time-and-timestamp-literals"></a>Datums-, Zeit- und Zeitstempelliterale
Die Escapesequenz für Datums-, Uhrzeit- und Zeitstempelliterale ist  
  
 **-Typ**_-type_ **'** _Wert_ **'**    
  
 wobei *der Literaltyp* einer der in der folgenden Tabelle aufgeführten Werte ist.  
  
|*Literaltyp*|Bedeutung|Format des *Wertes*|  
|---------------------|-------------|-----------------------|  
|**D**|Date|*yyyy*-*mm*-*dd*|  
|**T**|Zeit*|*hh*:*mm*:*ss*[1]|  
|**Ts**|Timestamp|*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.* f...*] [1]|  
  
 [1] Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in einem Zeit- oder Zeitstempelintervallliteral, das eine Sekundenkomponente enthält, hängt von der Sekundengenauigkeit ab, wie sie im SQL_DESC_PRECISION Deskriptorfeld enthalten ist. (Weitere Informationen finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Weitere Informationen zu Datums-, Uhrzeit- und Zeitstempelescapesequenzen finden Sie unter [Datum, Uhrzeit und Zeitstempel-Escape-Sequenzen](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) in Anhang C: SQL-Grammatik.  
  
 Beispielsweise aktualisieren beide der folgenden SQL-Anweisungen das offene Datum des Verkaufsauftrags 1023 in der Tabelle Orders. Die erste Anweisung verwendet die Escapesequenzsyntax. Die zweite Anweisung verwendet die systemeigene Oracle Rdb-Syntax für die DATE-Spalte und ist nicht interoperabel.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 Die Escapesequenz für ein Datums-, Zeit- oder Zeitstempelliteral kann auch in einer Zeichenvariablen platziert werden, die an einen Datums-, Uhrzeit- oder Zeitstempelparameter gebunden ist. Der folgende Code verwendet z. B. einen Datumsparameter, der an eine Zeichenvariable gebunden ist, um das offene Datum des Verkaufsauftrags 1023 in der Tabelle Orders zu aktualisieren:  
  
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
  
 In der Regel ist es jedoch effizienter, den Parameter direkt an eine Datumsstruktur zu binden:  
  
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
  
 Um zu bestimmen, ob ein Treiber die ODBC-Escapesequenzen für Datums-, Uhrzeit- oder Zeitstempelliterale unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Wenn die Datenquelle einen Datentyp für Datum, Uhrzeit oder Zeitstempel unterstützt, muss sie auch die entsprechende Escapesequenz unterstützen.  
  
 Datenquellen können auch die in der ANSI SQL-92-Spezifikation definierten Datumszeitliterale unterstützen, die sich von den ODBC-Escapesequenzen für Datums-, Uhrzeit- oder Zeitstempelliterale unterscheiden. Um zu bestimmen, ob eine Datenquelle die ANSI-Literale unterstützt, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_ANSI_SQL_DATETIME_LITERALS auf.  
  
 Um zu bestimmen, ob ein Treiber die ODBC-Escapesequenzen für Intervallliterale unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Wenn die Datenquelle einen Datetime-Intervalldatentyp unterstützt, muss sie auch die entsprechende Escapesequenz unterstützen.  
  
 Datenquellen können auch die in der ANSI SQL-92-Spezifikation definierten Datumszeitliterale unterstützen, die sich von den ODBC-Escapesequenzen für Datumszeitintervallliterale unterscheiden. Um zu bestimmen, ob eine Datenquelle die ANSI-Literale unterstützt, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_ANSI_SQL_DATETIME_LITERALS auf.
