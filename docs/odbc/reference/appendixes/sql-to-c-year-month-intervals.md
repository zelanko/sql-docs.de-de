---
title: 'SQL in C: Jahr-Monat-Intervalle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2c7412226dd0674022da022b0a0a63e5bf2063cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065043"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL in C: Jahr-Monat-Intervalle

Der Bezeichner für die Jahr-Monat-Intervall-ODBC-SQL-Datentypen sind die folgenden:

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in die Jahr-Monat Intervall SQL-Daten konvertiert werden kann. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typ-ID|Test|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH[a]<br /><br /> SQL_C_INTERVAL_YEAR[a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH[a]|Nachfolgende Felder Teil nicht abgeschnitten<br /><br /> Nachfolgende Felder Teil abgeschnitten<br /><br /> Die führende Genauigkeit des Ziels ist nicht groß genug zum Speichern von Daten aus der Quelle|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Länge der Daten in bytes<br /><br /> Nicht definiert|n/v<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b]<br /><br /> SQL_C_UTINYINT[b]<br /><br /> SQL_C_USHORT[b]<br /><br /> SQL_C_SHORT[b]<br /><br /> SQL_C_SLONG[b]<br /><br /> SQL_C_ULONG[b]<br /><br /> SQL_C_NUMERIC[b]<br /><br /> SQL_C_BIGINT[b]|Intervall-Genauigkeit wurde ein einzelnes Feld aus, und die Daten ohne Abschneiden konvertiert wurde<br /><br /> Intervall-Genauigkeit wurde ein einzelnes Feld und das gesamte abgeschnittene<br /><br /> Intervall-Genauigkeit war kein einzelnes Feld|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Länge der Daten in bytes<br /><br /> Anzahl der C-Datentyp|n/v<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Die Bytelänge der Daten < = *Pufferlänge*<br /><br /> Die Bytelänge der Daten > *Pufferlänge*|Daten<br /><br /> Nicht definiert|Länge der Daten in bytes<br /><br /> Nicht definiert|n/v<br /><br /> 22003|  
|SQL_C_CHAR|Zeichen-Byte-Länge < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) > = *Pufferlänge*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Anzahl der C-Datentyp<br /><br /> Nicht definiert|n/v<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichenlänge < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) > = *Pufferlänge*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Anzahl der C-Datentyp<br /><br /> Nicht definiert|n/v<br /><br /> 01004<br /><br /> 22003|  
  
 [a] ein Jahr-Monat-Intervall SQL-Typ kann auf einen beliebigen Jahr-Monat-C-Intervall-Typ konvertiert werden.  
  
 [b] Wenn das Intervall ein einzelnes Feld (eine Jahr oder Monat) übersteigt, kann das Intervall SQL-Typ in genauer numerischer Wert (SQL_C_STINYINT SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) konvertiert werden.  

## <a name="default-conversions"></a>Standardkonvertierungen

Die standardkonvertierung eines Intervalls SQL-Typ ist in den Datentyp der entsprechenden C-Intervall. Die Anwendung dann bindet die Spalte oder des Parameters (oder legt das SQL_DESC_DATA_PTR-Feld in den entsprechenden Datensatz der ARD), zeigen Sie auf die initialisierte SQL_INTERVAL_STRUCT-Struktur (oder übergibt einen Zeiger auf die SQL_ INTERVAL_STRUCT-Struktur wie die *TargetValuePtr* Argument in einem Aufruf von **SQLGetData**).
