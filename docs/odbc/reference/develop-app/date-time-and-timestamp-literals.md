---
description: Datums-, Zeit- und Zeitstempelliterale
title: Datums-, Uhrzeit-und Zeitstempel Literale | Microsoft-Dokumentation
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
ms.openlocfilehash: 10fb362a8ab61595a9b7205492de9c1115ae7013
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424782"
---
# <a name="date-time-and-timestamp-literals"></a>Datums-, Zeit- und Zeitstempelliterale
Die Escapesequenz für Datums-, Uhrzeit-und Zeitstempel-Literale ist  
  
 **{**  _-Type_ **'** _value_ **'}**  
  
 Dabei ist der *Literaltyp* einer der in der folgenden Tabelle aufgeführten Werte.  
  
|*Literaltyp*|Bedeutung|Format des *Werts*|  
|---------------------|-------------|-----------------------|  
|**d**|Datum|*JJJJ* - *mm* - *DD*|  
|**Bund**|Zeit|*HH*:*mm*:*SS*[1]|  
|**TS**|Timestamp|*JJJJ* - *mm* - *dd* TT *HH*:*mm*:*SS*[.* f...*] 1|  
  
 [1] die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in einem Zeit-oder Zeitstempel-intervallal, das eine Sekunden Komponente enthält, hängt von der Sekunden Genauigkeit ab, wie im Feld SQL_DESC_PRECISION Deskriptor enthalten. (Weitere Informationen finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Weitere Informationen zu Datums-, Uhrzeit-und Zeitstempel-Escapesequenzen finden Sie unter [Datums-, Uhrzeit-und Zeitstempel-](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) Escapesequenzen in Anhang C: SQL-Grammatik.  
  
 Die beiden folgenden SQL-Anweisungen aktualisieren z. b. das Öffnungs Datum von Sales Order 1023 in der Orders-Tabelle. In der ersten Anweisung wird die Escapesequenzsyntax verwendet. Die zweite Anweisung verwendet die native Oracle RDB-Syntax für die Date-Spalte und ist nicht interoperabel.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 Die Escapesequenz für ein Date-, Time-oder Zeitstempel-Literalzeichen kann auch in eine Zeichen Variable eingefügt werden, die an einen Date-, Time-oder Zeitstempel-Parameter gebunden ist. Im folgenden Code wird z. b. ein Datums Parameter verwendet, der an eine Zeichen Variable gebunden ist, um das Öffnungs Datum von Sales Order 1023 in der Orders-Tabelle zu aktualisieren:  
  
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
  
 Es ist jedoch in der Regel effizienter, den Parameter direkt an eine Datums Struktur zu binden:  
  
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
  
 Um zu ermitteln, ob ein Treiber die ODBC-Escapesequenzen für Datums-, Uhrzeit-oder Zeitstempel-Literale unterstützt, ruft eine Anwendung **sqlgettypeingefo**auf. Wenn die Datenquelle einen Datums-, Uhrzeit-oder Zeitstempel-Datentyp unterstützt, muss Sie auch die entsprechende Escapesequenz unterstützen.  
  
 Datenquellen können auch die in der ANSI SQL-92-Spezifikation definierten datetime-Literale unterstützen, die sich von den ODBC-Escapesequenzen für Datums-, Uhrzeit-oder Zeitstempel-Literale unterscheiden. Um zu ermitteln, ob eine Datenquelle die ANSI-Literale unterstützt, ruft eine Anwendung **SQLGetInfo** mit der SQL_ANSI_SQL_DATETIME_LITERALS-Option auf.  
  
 Um zu ermitteln, ob ein Treiber die ODBC-Escapesequenzen für intervallliterale unterstützt, ruft eine Anwendung **sqlgettypeingefo**auf. Wenn die Datenquelle einen DateTime-Intervall Datentyp unterstützt, muss Sie auch die entsprechende Escapesequenz unterstützen.  
  
 Datenquellen können auch die in der ANSI SQL-92-Spezifikation definierten datetime-Literale unterstützen, die sich von den ODBC-Escapesequenzen für DateTime Interval-Literale unterscheiden. Um zu ermitteln, ob eine Datenquelle die ANSI-Literale unterstützt, ruft eine Anwendung **SQLGetInfo** mit der SQL_ANSI_SQL_DATETIME_LITERALS-Option auf.
