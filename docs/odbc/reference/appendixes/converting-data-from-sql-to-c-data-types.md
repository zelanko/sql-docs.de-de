---
title: Konvertieren von Daten aus SQL-In-C-Datentypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC]
- data conversions from SQL to C types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- data types [ODBC], SQL data types
- SQL data types [ODBC], converting to C types
- converting data from SQL to c types [ODBC]
- converting data from SQL to c types [ODBC], about converting
- C data types [ODBC], converting from SQL types
ms.assetid: 029727f6-d3f0-499a-911c-bcaf9714e43b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a10730cb3910c55679c264583801cd57c83bfc3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284750"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Konvertieren von Daten von SQL- zu C-Datentypen
Wenn eine Anwendung **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**aufruft, ruft der Treiber die Daten aus der Datenquelle ab. Bei Bedarf werden die Daten aus dem Datentyp, in dem der Treiber sie abgerufen hat, in den Datentyp konvertiert, der durch das *TargetType-Argument* in **SQLBindCol** oder **SQLGetData** angegeben wird. Schließlich werden die Daten an der Position gespeichert, auf die das *TargetValuePtr-Argument* in **SQLBindCol** oder **SQLGetData** (und das SQL_DESC_DATA_PTR Feld der ARD) zeigt.  
  
 Die folgende Tabelle zeigt die unterstützten Konvertierungen von ODBC SQL-Datentypen in ODBC C-Datentypen. Ein ausgefüllter Kreis gibt die Standardkonvertierung für einen SQL-Datentyp an (den C-Datentyp, in den die Daten konvertiert werden, wenn der Wert von *TargetType* SQL_C_DEFAULT ist). Ein hohler Kreis zeigt eine unterstützte Konvertierung an.  
  
 Für eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, wird die Konvertierung von treiberspezifischen Datentypen möglicherweise nicht unterstützt.  
  
 Das Format der konvertierten Daten wird von der Windows®-Ländereinstellung nicht beeinflusst.  
  
 In den Tabellen in den folgenden Abschnitten wird beschrieben, wie der Treiber oder die Datenquelle die aus der Datenquelle abgerufenen Daten konvertiert. Treiber sind erforderlich, um Konvertierungen in alle ODBC C-Datentypen aus den von ihnen unterstützten ODBC SQL-Datentypen zu unterstützen. Für einen bestimmten ODBC SQL-Datentyp listet die erste Spalte der Tabelle die rechtlichen Eingabewerte des *TargetType-Arguments* in **SQLBindCol** und **SQLGetData**auf. In der zweiten Spalte werden die Ergebnisse eines Tests aufgelistet, der häufig das in **SQLBindCol** oder **SQLGetData**angegebene *BufferLength-Argument* verwendet, das der Treiber ausführt, um zu bestimmen, ob er die Daten konvertieren kann. Für jedes Ergebnis werden in der dritten und vierten Spalte die Werte aufgeführt, die in den Puffern platziert werden, die vom *TargetValuePtr* angegeben *werden,* und StrLen_or_IndPtr Argumente, die in **SQLBindCol** oder **SQLGetData** angegeben sind, nachdem der Treiber versucht hat, die Daten zu konvertieren. (Das *StrLen_or_IndPtr* Argument entspricht dem SQL_DESC_OCTET_LENGTH_PTR der ARD.) In der letzten Spalte wird die SQLSTATE aufgeführt, die für jedes Ergebnis von **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**zurückgegeben wird.  
  
 Wenn das *TargetType-Argument* in **SQLBindCol** oder **SQLGetData** einen Bezeichner für einen ODBC C-Datentyp enthält, der in der Tabelle für einen bestimmten ODBC SQL-Datentyp nicht angezeigt wird, **gibt SQLFetch**, **SQLFetchScroll**oder **SQLGetData** SQLSTATE 07006 (Restricted data type attribute violation) zurück. Wenn das *TargetType-Argument* einen Bezeichner enthält, der eine Konvertierung von einem treiberspezifischen SQL-Datentyp in einen ODBC C-Datentyp angibt und diese Konvertierung vom Treiber nicht unterstützt wird, gibt **SQLFetch**, **SQLFetchScroll**oder **SQLGetData** SQLSTATE HYC00 zurück (Optionale Funktion ist nicht implementiert).  
  
 Obwohl er nicht in den Tabellen angezeigt wird, gibt der Treiber SQL_NULL_DATA im Puffer zurück, der durch das *Argument StrLen_or_IndPtr* angegeben wird, wenn der SQL-Datenwert NULL ist. Eine Erläuterung der Verwendung von *StrLen_or_IndPtr,* wenn mehrere Aufrufe zum Abrufen von Daten durchgeführt werden, finden Sie in der [SQLGetData-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetdata-function.md) Wenn SQL-Daten in Zeichen-C-Daten konvertiert \*werden, enthält die in *StrLen_or_IndPtr* zurückgegebene Zeichenanzahl nicht das Null-Beendigungs-Byte. Wenn *TargetValuePtr* ein Nullzeiger ist, gibt **SQLGetData** SQLSTATE HY009 (Ungültige Verwendung von NULL-Zeiger) zurück. in **SQLBindCol**wird die Bindung der Spalte aufgekleben.  
  
 Die folgenden Begriffe und Konventionen werden in den Tabellen verwendet:  
  
-   **Bytelänge der Daten** ist die Anzahl der Bytes von C-Daten, die in **TargetValuePtr*zurückgegeben werden können, unabhängig davon, ob die Daten abgeschnitten werden, bevor sie an die Anwendung zurückgegeben werden. Bei Zeichenfolgendaten enthält dies nicht den Speicherplatz für das Null-Beendigungszeichen.  
  
-   **Die Zeichenbytelänge** ist die Gesamtzahl der Bytes, die zum Anzeigen der Daten im Zeichenformat erforderlich sind. Dies ist wie für jeden C-Datentyp im Abschnitt [Anzeigegröße](../../../odbc/reference/appendixes/display-size.md)definiert, mit der Ausnahme, dass die Zeichenbytelänge in Bytes liegt, während die Anzeigegröße in Zeichen angegeben ist.  
  
-   Wörter in *Kursivschrift* stellen Funktionsargumente oder Elemente der SQL-Grammatik dar. Die Syntax von Grammatikelementen finden Sie unter [Anhang C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [SQL to C: Character (SQL zu C: Zeichen)](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL to C: Numeric (SQL zu C: Numerisch)](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL to C: Bit (SQL zu C: Bit)](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL to C: Binary (SQL zu C: Binär)](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL to C: Date (SQL zu C: Datum)](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL to C: GUID (SQL zu C: GUID)](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL to C: Time (SQL zu C: Zeit)](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL to C: Timestamp (SQL zu C: Zeitstempel)](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL to C: Year-Month Intervals (SQL zu C: Jahr-Monat-Intervalle)](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL to C: Day-Time Intervals (SQL zu C: Taginvervalle)](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [SQL to C Data Conversion Examples (Beispiele für die Datenkonvertierung von SQL zu C)](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
