---
title: Datentypen werden von C in SQL-Datentypen umgerechnet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], about converting
- converting data from c to SQL types [ODBC]
- data conversions from C to SQL types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- SQL data types [ODBC], converting from C types
- data types [ODBC], SQL data types
- data conversions from C to SQL types [ODBC]
- C data types [ODBC], converting to SQL types
ms.assetid: ee0afe78-b58f-4d34-ad9b-616bb23653bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8fb707e77df7d793277d4a23146adc980eede6fd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304659"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Konvertieren von Daten von C- zu SQL-Datentypen
Wenn eine Anwendung **SQLExecute** oder **SQLExecDirect**aufruft, ruft der Treiber die Daten für alle Parameter ab, die mit **SQLBindParameter** an den Speicherorten in der Anwendung gebunden sind. Wenn eine Anwendung **SQLSetPos**aufruft, ruft der Treiber die Daten für einen Update-oder Add-Vorgang aus Spalten ab, die mit **SQLBindCol**gebunden sind. Bei Data-at-Execution-Parametern sendet die Anwendung die Parameterdaten mit **SQLPutData**. Falls erforderlich, konvertiert der Treiber die Daten aus dem Datentyp, der vom *ValueType* -Argument in **SQLBindParameter** angegeben wird, in den Datentyp, der durch das *Parameter Type* -Argument in **SQLBindParameter**angegeben wird, und sendet die Daten dann an die Datenquelle.  
  
 In der folgenden Tabelle werden die unterstützten Konvertierungen von ODBC C-Datentypen in ODBC-SQL-Datentypen gezeigt. Ein ausgefüllter Kreis gibt die Standard Konvertierung für einen SQL-Datentyp an (der C-Datentyp, von dem die Daten konvertiert werden, wenn der Wert von *ValueType* oder das SQL_DESC_CONCISE_TYPE Deskriptorfeld SQL_C_DEFAULT ist). Ein leerer Kreis gibt eine unterstützte Konvertierung an.  
  
 Das Format der konvertierten Daten wird von der Einstellung für das Windows-® Land nicht beeinträchtigt.  
  
 ![Unterstützte Konvertierungen: ODBC C- in SQL-Datentypen](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 In den Tabellen in den folgenden Abschnitten wird beschrieben, wie der Treiber oder die Datenquelle die an die Datenquelle gesendeten Daten konvertiert. Treiber sind erforderlich, um Konvertierungen von allen ODBC-C-Datentypen in die von Ihnen unterstützten ODBC-SQL-Datentypen zu unterstützen. Für einen bestimmten ODBC-C-Datentyp listet die erste Spalte der Tabelle die zulässigen Eingabewerte des *Parameters Parameter Type* in **SQLBindParameter**auf. In der zweiten Spalte werden die Ergebnisse eines Tests aufgelistet, den der Treiber durchführt, um zu bestimmen, ob die Daten konvertiert werden können. In der dritten Spalte wird der für jedes Ergebnis von **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**oder **SQLPutData**zurückgegebene SQLSTATE aufgelistet. Daten werden nur dann an die Datenquelle gesendet, wenn SQL_SUCCESS zurückgegeben wird.  
  
 Wenn das *ParameterType* -Argument in **SQLBindParameter** den Bezeichner eines ODBC SQL-Datentyps enthält, der in der Tabelle für einen bestimmten C-Datentyp nicht angezeigt wird, gibt **SQLBindParameter** SQLSTATE 07006 (eingeschränkte Datentyp-Attribut Verletzung) zurück. Wenn das *Parameter Type* -Argument einen treiberspezifischen Bezeichner enthält und der Treiber die Konvertierung des bestimmten ODBC C-Datentyps in diesen treiberspezifischen SQL-Datentyp nicht unterstützt, gibt **SQLBindParameter** SQLSTATE HYC00 (optionales Feature nicht implementiert) zurück.  
  
 Wenn die in **SQLBindParameter** angegebenen Argumente *ParameterValuePtr* und *StrLen_or_IndPtr* beide NULL-Zeiger sind, gibt diese Funktion SQLSTATE HY009 (Ungültige Verwendung des NULL-Zeigers) zurück. Obwohl Sie in den Tabellen nicht angezeigt wird, legt eine Anwendung den Wert des Längen-/Indikatorpuffers fest, auf den das *StrLen_or_IndPtr* -Argument von **SQLBindParameter** oder den Wert des *StrLen_or_IndPtr* -Arguments von **SQLPutData** SQL_NULL_DATA, um einen Null-SQL-Datenwert anzugeben. (Das *StrLen_or_IndPtr* -Argument entspricht dem SQL_DESC_OCTET_LENGTH_PTR-Feld der APD.) Diese Werte werden von der Anwendung auf SQL_NTS festgelegt, um anzugeben \*, dass der Wert in *ParameterValuePtr* in **SQLBindParameter** oder \* *DataPtr* in **SQLPutData** (auf das das SQL_DESC_DATA_PTR-Feld der APD zeigt) eine NULL-terminierte Zeichenfolge ist.  
  
 Die folgenden Begriffe werden in den Tabellen verwendet:  
  
-   **Byte Länge der Daten** : die Anzahl von Bytes an SQL-Daten, die an die Datenquelle gesendet werden können, unabhängig davon, ob die Daten abgeschnitten werden, bevor Sie an die Datenquelle gesendet werden. Bei Zeichen folgen Daten enthält dies keinen Platz für das NULL-Terminierungs Zeichen.  
  
-   **Spalten Byte Länge** : die Anzahl von Bytes, die zum Speichern der Daten in der Datenquelle erforderlich sind.  
  
-   **Zeichen Byte Länge** : maximale Anzahl von Bytes, die zum Anzeigen von Daten im Zeichenformat erforderlich sind. Dies ist für jeden SQL-Datentyp in der [Anzeige Größe](../../../odbc/reference/appendixes/display-size.md)definiert, mit der Ausnahme, dass die Länge des Zeichen Bytes in Bytes liegt, während die Anzeige Größe in Zeichen angegeben ist.  
  
-   **Anzahl der Ziffern** -Anzahl der Zeichen, die zur Darstellung einer Zahl verwendet werden, einschließlich Minuszeichen, Dezimaltrennzeichen und Exponent (falls erforderlich).  
  
-   **Wörter in**   
     ***kursiv*** -Elemente der SQL-Grammatik. Die Syntax von Grammatik Elementen finden Sie in [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [C to SQL: Character (C zu SQL: Zeichen)](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [C to SQL: Numeric (C zu SQL: Numerisch)](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [C to SQL: Bit (C zu SQL: Bit)](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [C to SQL: Binary (C zu SQL: Binär)](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [C to SQL: Date (C zu SQL: Datum)](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [C to SQL: GUID (C zu SQL: GUID)](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [C to SQL: Time (C zu SQL: Zeit)](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [C to SQL: Timestamp (C zu SQL: Zeitstempel)](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [C to SQL: Year-Month Intervals (C zu SQL: Jahr-Monat-Intervalle)](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [C to SQL: Day-Time Intervals (C zu SQL: Taginvervalle)](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [C to SQL Data Conversion Examples (Beispiele für die Datenkonvertierung von C zu SQL)](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
