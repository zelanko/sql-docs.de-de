---
title: 'C zu SQL: Zeitintervalle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c3f7efb443b442d44a94cfd43629cdaedd6195b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81291920"
---
# <a name="c-to-sql-day-time-intervals"></a>C zu SQL: Tag-Uhrzeit-Intervalle
Die Bezeichner für die ODBC-C-Datentypen für das Tag-Zeitintervall lauten wie folgt:  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen angezeigt, in die Intervall-C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR [a]<br /><br /> SQL_LONGVARCHAR [a]|Spalten Byte Länge >= Zeichen Byte Länge<br /><br /> Spalten Byte Länge < Zeichen Byte Länge [a]<br /><br /> Der Datenwert ist kein gültiges intervallliterale.|Nicht zutreffend<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Spalten Zeichen Länge >= Zeichen Länge von Daten<br /><br /> Spalten Zeichenlänge < Zeichen Länge von Daten [a]<br /><br /> Der Datenwert ist kein gültiges intervallliterale.|Nicht zutreffend<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b] SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b] SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Die Konvertierung eines einzelnen Feld Intervalls führte nicht zum Abschneiden ganzer Ziffern.<br /><br /> Die Konvertierung führte zum Abschneiden ganzer Ziffern.|Nicht zutreffend<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|Der Datenwert wurde ohne Abschneiden beliebiger Felder konvertiert.<br /><br /> Mindestens ein Feld mit einem Datenwert wurde während der Konvertierung abgeschnitten.|Nicht zutreffend<br /><br /> 22015|  
  
 [a] alle C-Intervall Datentypen können in einen Zeichen Datentyp konvertiert werden.  
  
 [b] Wenn das typanfeld in der Intervall Struktur so ist, dass es sich bei dem Intervall um ein einzelnes Feld (SQL_DAY, SQL_HOUR, SQL_MINUTE oder SQL_SECOND) handelt, kann der C-Typ des Intervalls in alle exakten numerischen Werte (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL oder SQL_NUMERIC) konvertiert werden.  
  
 Die Standard Konvertierung eines Interval-C-Typs erfolgt in den entsprechenden SQL-Typ für den Tag-Zeit-Intervall.  
  
 Der Treiber ignoriert den Längen-/indikatorenwert beim Umrechnen von Daten aus dem Datentyp Interval c und geht davon aus, dass die Größe des Daten Puffers der Größe des Datentyps Interval c entspricht. Der Wert für die Länge/den Indikator wird im *StrLen_Or_Ind* -Argument in **SQLPutData** und in dem Puffer übergeben, der mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wird. Der Datenpuffer wird mit dem *DataPtr* -Argument in **SQLPutData** und dem *ParameterValuePtr* -Argument in **SQLBindParameter**angegeben.  
  
 Im folgenden Beispiel wird veranschaulicht, wie die in der SQL_INTERVAL_STRUCT Struktur gespeicherten Intervall-C-Daten in eine Daten Bank Spalte gesendet werden. Die Intervall Struktur enthält ein DAY_TO_SECOND Intervall. Sie wird in einer Daten Bank Spalte vom Typ SQL_INTERVAL_DAY_TO_MINUTE gespeichert.  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
