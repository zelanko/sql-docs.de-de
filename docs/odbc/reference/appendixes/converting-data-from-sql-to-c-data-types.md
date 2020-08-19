---
description: Konvertieren von Daten von SQL- zu C-Datentypen
title: Datentypen werden von SQL in C-Datentypen umgerechnet | Microsoft-Dokumentation
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
ms.openlocfilehash: 5c1306564a9e4a5c1cbd9cac74508529a1e6df9a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429692"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Konvertieren von Daten von SQL- zu C-Datentypen
Wenn eine Anwendung **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**aufruft, ruft der Treiber die Daten aus der Datenquelle ab. Bei Bedarf werden die Daten aus dem Datentyp, in dem der Treiber Sie abgerufen hat, in den Datentyp konvertiert, der durch das *TargetType* -Argument in **SQLBindCol** oder **SQLGetData** angegeben wird. Schließlich werden die Daten an dem Speicherort gespeichert, auf den durch das *targetvalueptr* -Argument in **SQLBindCol** oder **SQLGetData** (und das SQL_DESC_DATA_PTR-Feld der ARD) verwiesen wird.  
  
 In der folgenden Tabelle sind die unterstützten Konvertierungen von ODBC-SQL-Datentypen in ODBC-C-Datentypen aufgeführt. Ein ausgefüllter Kreis gibt die Standard Konvertierung für einen SQL-Datentyp an (der C-Datentyp, in den die Daten konvertiert werden, wenn der Wert von *TargetType* SQL_C_DEFAULT). Ein leerer Kreis gibt eine unterstützte Konvertierung an.  
  
 Für eine ODBC *3. x* -Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, wird die Konvertierung von treiberspezifischen Datentypen möglicherweise nicht unterstützt.  
  
 Das Format der konvertierten Daten wird von der Einstellung für das Windows-® Land nicht beeinträchtigt.  
  
 In den Tabellen in den folgenden Abschnitten wird beschrieben, wie der Treiber oder die Datenquelle aus der Datenquelle abgerufene Daten konvertiert. Treiber sind erforderlich, um Konvertierungen in alle ODBC C-Datentypen von den unterstützten ODBC-SQL-Datentypen zu unterstützen. Für einen bestimmten ODBC SQL-Datentyp listet die erste Spalte der Tabelle die zulässigen Eingabewerte des *TargetType* -Arguments in **SQLBindCol** und **SQLGetData**auf. In der zweiten Spalte sind die Ergebnisse eines Tests aufgeführt. häufig wird das in **SQLBindCol** oder **SQLGetData**angegebene *BufferLength* -Argument verwendet, um zu bestimmen, ob die Daten konvertiert werden können. Für jedes Ergebnis werden in der dritten und vierten Spalte die Werte aufgeführt, die in den von *targetvalueptr* angegebenen Puffern abgelegt werden, und *StrLen_or_IndPtr* in **SQLBindCol** oder **SQLGetData** angegebenen Argumente, nachdem der Treiber versucht hat, die Daten zu konvertieren. (Das *StrLen_or_IndPtr* -Argument entspricht dem SQL_DESC_OCTET_LENGTH_PTR Feld der ARD.) Die letzte Spalte listet den SQLSTATE auf, der für jedes Ergebnis von **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**zurückgegeben wurde.  
  
 Wenn das *TargetType* -Argument in **SQLBindCol** oder **SQLGetData** einen Bezeichner für einen ODBC C-Datentyp enthält, der in der Tabelle für einen bestimmten ODBC-SQL-Datentyp nicht angezeigt wird, gibt **SQLFetch**, **SQLFetchScroll**oder **SQLGetData** SQLSTATE 07006 (eingeschränkte Datentyp Attribut Verletzung) zurück. Wenn das *TargetType* -Argument einen Bezeichner enthält, der eine Konvertierung von einem treiberspezifischen SQL-Datentyp in einen ODBC-C-Datentyp angibt, und diese Konvertierung nicht vom Treiber, **SQLFetch**, **SQLFetchScroll**oder **SQLGetData** unterstützt wird, gibt SQLSTATE HYC00 (optionales Feature nicht implementiert) zurück.  
  
 Obwohl Sie in den Tabellen nicht angezeigt wird, gibt der Treiber SQL_NULL_DATA in dem Puffer zurück, der durch das *StrLen_or_IndPtr* -Argument angegeben wird, wenn der SQL-Datenwert NULL ist. Eine Erläuterung der Verwendung von *StrLen_or_IndPtr* , wenn mehrere Aufrufe zum Abrufen von Daten durchgeführt werden, finden Sie in der Beschreibung der [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)-Funktion. Wenn SQL-Daten in Zeichen-C-Daten konvertiert werden, enthält die in StrLen_or_IndPtr zurückgegebene Zeichen Anzahl \* *StrLen_or_IndPtr* nicht das NULL-Terminierungs Byte. Wenn *targetvalueptr* ein NULL-Zeiger ist, gibt **SQLGetData** SQLSTATE HY009 (Ungültige Verwendung des NULL-Zeigers) zurück. in **SQLBindCol**wird dadurch die Bindung der Spalte entbindet.  
  
 Die folgenden Begriffe und Konventionen werden in den Tabellen verwendet:  
  
-   Die **Byte Länge der Daten** ist die Anzahl der Bytes von C-Daten, die in **targetvalueptr*zurückgegeben werden können, unabhängig davon, ob die Daten abgeschnitten werden, bevor Sie an die Anwendung zurückgegeben werden. Bei Zeichen folgen Daten enthält dies nicht den Platz für das NULL-Terminierungs Zeichen.  
  
-   **Zeichen Byte Länge** ist die Gesamtanzahl der Bytes, die zum Anzeigen der Daten im Zeichenformat benötigt werden. Dies ist für jeden C-Datentyp in der Abschnitts [Anzeige Größe](../../../odbc/reference/appendixes/display-size.md)definiert, mit dem Unterschied, dass die Zeichen Länge in Byte liegt, während die Anzeige Größe in Zeichen angegeben ist.  
  
-   *Kursiv* geschriebene Wörter stellen Funktionsargumente oder Elemente der SQL-Grammatik dar. Die Syntax von Grammatik Elementen finden Sie in [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
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
