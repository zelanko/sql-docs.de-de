---
description: 'SQL zu C: Tag-Uhrzeit-Intervalle'
title: 'SQL zu C: Tages Intervalle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f3c878434a6fc3b2dcbb8b09a4acfb41ecf44a84
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429572"
---
# <a name="sql-to-c-day-time-intervals"></a>SQL zu C: Tag-Uhrzeit-Intervalle

Die Bezeichner für die ODBC-SQL-Datentypen für das Tag-Zeitintervall lauten wie folgt:

- SQL_INTERVAL_DAY
- SQL_INTERVAL_DAY_TO_MINUTE
- SQL_INTERVAL_HOUR
- SQL_INTERVAL_DAY_TO_SECOND
- SQL_INTERVAL_MINUTE
- SQL_INTERVAL_HOUR_TO_MINUTE
- SQL_INTERVAL_SECOND
- SQL_INTERVAL_HOUR_TO_SECOND
- SQL_INTERVAL_DAY_TO_HOUR
- SQL_INTERVAL_MINUTE_TO_SECOND

In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die die SQL-Daten für das Zeitintervall konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).

|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Alle Tag-Zeit-C-Intervall Typen|Teil der nachfolgenden Felder nicht abgeschnitten<br /><br /> Teil der nachfolgenden Felder abgeschnitten<br /><br /> Die führende Genauigkeit des Ziels ist nicht groß genug zum Speichern von Daten aus der Quelle.|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b] SQL_C_UTINYINT [b] SQL_C_USHORT [b] SQL_C_SHORT [b] SQL_C_SLONG [b] SQL_C_ULONG [b] SQL_C_NUMERIC [b] SQL_C_BIGINT [b]|Die Intervall Genauigkeit war ein einzelnes Feld, und die Daten wurden ohne Abschneiden konvertiert.<br /><br /> Intervall Genauigkeit war ein einzelnes Feld und abgeschnittene Bruchteile<br /><br /> Intervall Genauigkeit war ein einzelnes Feld und ein abgeschnittenes ganzes<br /><br /> Intervall Genauigkeit war kein einzelnes Feld|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des C-Datentyps<br /><br /> Länge der Daten<br /><br /> Länge der Daten<br /><br /> Größe des C-Datentyps|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_CHAR|Zeichen Byte Länge < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des C-Datentyps<br /><br /> Größe des C-Datentyps<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichen Länge < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des C-Datentyps<br /><br /> Größe des C-Datentyps<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
  
 [a] ein Zeitintervall-SQL-Typ kann in einen beliebigen Tag-Zeit-Intervall-C-Typ konvertiert werden.  
  
 [b] Wenn die Intervall Genauigkeit ein einzelnes Feld (einer von Tag, Stunde, Minute oder Sekunde) ist, kann der SQL-Datentyp des Intervalls in alle exakten numerischen Werte (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) konvertiert werden.  
  
Die Standard Konvertierung eines SQL-Datentyps für das Intervall erfolgt in den entsprechenden Datentyp von C-Intervall. Die Anwendung bindet dann die Spalte oder den Parameter (oder legt das SQL_DESC_DATA_PTR Feld im entsprechenden Datensatz der ARD) so fest, dass Sie auf die initialisierte SQL_INTERVAL_STRUCT Struktur verweist (oder übergibt einen Zeiger an die SQL_ INTERVAL_STRUCT Struktur als *targetvalueptr* -Argument in einem **SQLGetData**-Befehl).  
  
Im folgenden Beispiel wird veranschaulicht, wie Daten aus einer Spalte vom Typ SQL_INTERVAL_DAY_TO_MINUTE in die SQL_INTERVAL_STRUCT Struktur übertragen werden, sodass Sie als DAY_TO_HOUR Intervall wiederholt wird.  

```cpp
SQL_INTERVAL_STRUCT is;  
SQLINTEGER    cbValue;  
SQLUINTEGER   days, hours;  
  
// Execute a select statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &is, sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Fetch  
SQLFetch(hstmt);  
  
// Process data  
days = is.intval.day_second.day;  
hours = is.intval.day_second.hour;  
```
