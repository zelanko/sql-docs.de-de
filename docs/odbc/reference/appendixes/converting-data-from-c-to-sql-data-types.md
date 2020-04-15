---
title: Konvertieren von Daten von C in SQL-Datentypen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304659"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Konvertieren von Daten von C- zu SQL-Datentypen
Wenn eine Anwendung **SQLExecute** oder **SQLExecDirect**aufruft, ruft der Treiber die Daten für alle Parameter ab, die mit **SQLBindParameter** von Speicherorten in der Anwendung gebunden sind. Wenn eine Anwendung **SQLSetPos**aufruft, ruft der Treiber die Daten für eine Aktualisierung oder einen Vorgang aus Spalten ab, die mit **SQLBindCol**gebunden sind. Bei Parametern für Data-at-Execution sendet die Anwendung die Parameterdaten mit **SQLPutData**. Bei Bedarf konvertiert der Treiber die Daten aus dem datentyp, der durch das *ValueType-Argument* in **SQLBindParameter** angegeben wird, in den Datentyp, der durch das *ParameterType-Argument* in **SQLBindParameter**angegeben wird, und sendet die Daten dann an die Datenquelle.  
  
 Die folgende Tabelle zeigt die unterstützten Konvertierungen von ODBC C-Datentypen in ODBC SQL-Datentypen. Ein ausgefüllter Kreis gibt die Standardkonvertierung für einen SQL-Datentyp an (der C-Datentyp, aus dem die Daten konvertiert werden, wenn der Wert von *ValueType* oder das SQL_DESC_CONCISE_TYPE Deskriptorfeld SQL_C_DEFAULT ist). Ein hohler Kreis zeigt eine unterstützte Konvertierung an.  
  
 Das Format der konvertierten Daten wird von der Windows®-Ländereinstellung nicht beeinflusst.  
  
 ![Unterstützte Konvertierungen: ODBC C- in SQL-Datentypen](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 In den Tabellen in den folgenden Abschnitten wird beschrieben, wie der Treiber oder die Datenquelle die in die Datenquelle gesendeten Daten konvertiert. Treiber sind erforderlich, um Konvertierungen von allen ODBC C-Datentypen in die von ihnen unterstützten ODBC SQL-Datentypen zu unterstützen. Für einen bestimmten ODBC C-Datentyp listet die erste Spalte der Tabelle die rechtlichen Eingabewerte des *ParametersType-Arguments* in **SQLBindParameter**auf. In der zweiten Spalte werden die Ergebnisse eines Tests aufgeführt, den der Treiber durchführt, um zu bestimmen, ob er die Daten konvertieren kann. In der dritten Spalte werden die SQLSTATE-Werte aufgeführt, die für jedes Ergebnis von **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**oder **SQLPutData**zurückgegeben werden. Daten werden nur dann an die Datenquelle gesendet, wenn SQL_SUCCESS zurückgegeben wird.  
  
 Wenn das *ParameterType-Argument* in **SQLBindParameter** den Bezeichner eines ODBC SQL-Datentyps enthält, der in der Tabelle für einen bestimmten C-Datentyp nicht angezeigt wird, gibt **SQLBindParameter** SQLSTATE 07006 (Einschränkungsdatentypattributverletzung) zurück. Wenn das *ParameterType-Argument* einen treiberspezifischen Bezeichner enthält und der Treiber die Konvertierung vom spezifischen ODBC C-Datentyp in diesen treiberspezifischen SQL-Datentyp nicht unterstützt, gibt **SQLBindParameter** SQLSTATE HYC00 zurück (Optionale Funktion ist nicht implementiert).  
  
 Wenn *ParameterValuePtr* und *StrLen_or_IndPtr* in **SQLBindParameter** angegebenen Argumenten beide NULL-Zeiger sind, gibt diese Funktion SQLSTATE HY009 (Ungültige Verwendung von NULL-Zeiger) zurück. Obwohl sie nicht in den Tabellen angezeigt wird, legt eine Anwendung den Wert des Längen-Indikator-Puffers fest, auf den das *StrLen_or_IndPtr* Argument von **SQLBindParameter** oder den Wert des *StrLen_or_IndPtr-Arguments* von **SQLPutData** zeigt, um SQL_NULL_DATA einen NULL SQL-Datenwert anzugeben. (Das *argument StrLen_or_IndPtr* entspricht dem feld SQL_DESC_OCTET_LENGTH_PTR der APD.) Die Anwendung legt diese Werte auf SQL_NTS, um anzugeben, dass der Wert \*in *ParameterValuePtr* in **SQLBindParameter** \*oder *DataPtr* in **SQLPutData** (auf das SQL_DESC_DATA_PTR Feld der APD) eine null-terminierte Zeichenfolge ist.  
  
 In den Tabellen werden die folgenden Begriffe verwendet:  
  
-   **Byte-Länge der Daten** - Anzahl der Bytes von SQL-Daten, die an die Datenquelle gesendet werden können, unabhängig davon, ob die Daten abgeschnitten werden, bevor sie an die Datenquelle gesendet werden. Bei Zeichenfolgendaten enthält dies keinen Speicherplatz für das Null-Beendigungszeichen.  
  
-   **Spaltenbytelänge** – Anzahl der Bytes, die zum Speichern der Daten in der Datenquelle erforderlich sind.  
  
-   **Zeichenbytelänge** - Maximale Anzahl von Bytes, die zum Anzeigen von Daten in Zeichenform erforderlich sind. Dies ist wie für jeden SQL-Datentyp in [Anzeigegröße](../../../odbc/reference/appendixes/display-size.md)definiert, mit Ausnahme der Zeichenbytelänge in Bytes, während die Anzeigegröße in Zeichen angegeben ist.  
  
-   Anzahl der Ziffern – Anzahl der Zeichen, die verwendet werden, um eine Zahl darzustellen, einschließlich des **Minuszeichens,** des Dezimaltrennzeichens und des Exponenten (falls erforderlich).  
  
-   **Wörter in**   
     ***kursalics*** - Elemente der SQL-Grammatik. Die Syntax von Grammatikelementen finden Sie unter [Anhang C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
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
