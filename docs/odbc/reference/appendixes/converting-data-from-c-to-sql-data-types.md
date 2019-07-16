---
title: Konvertieren von Daten von C-in SQL-Datentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aca333a6f3006b1f12cf44d1670e38556027e476
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019120"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Konvertieren von Daten von C- zu SQL-Datentypen
Wenn eine Anwendung ruft **SQLExecute** oder **SQLExecDirect**, ruft der Treiber die Daten für alle Parameter gebunden **SQLBindParameter** von Speicherorten die Anwendung. Wenn eine Anwendung ruft **SQLSetPos**, der Treiber Ruft ab, die Daten für ein Update oder Hinzufügen von Spalten mit gebunden **SQLBindCol**. Für Data-at-Execution-Parameter, die Anwendung sendet die Parameterdaten mit **SQLPutData**. Wenn erforderlich, der Treiber die Daten aus den angegebenen Datentyp konvertiert die *ValueType* -Argument in **SQLBindParameter** in den Datentyp, der gemäß der *ParameterType*-Argument in **SQLBindParameter**, und klicken Sie dann die Daten an die Datenquelle sendet.  
  
 Die folgende Tabelle zeigt die unterstützten Konvertierungen von ODBC-C-Datentypen in ODBC-SQL-Datentypen. Ein ausgefüllten Kreis gibt an, die standardkonvertierung für einen SQL-Datentyp (der C-Datentyp, der aus dem die Daten werden, wenn konvertiert werden der Wert des *ValueType* oder das Deskriptorfeld SQL_DESC_CONCISE_TYPE SQL_C_DEFAULT). Ein leerer Kreis gibt an, eine Konvertierung unterstützt wird.  
  
 Das Format der konvertierten Daten ist von der Windows® Land-Einstellung nicht betroffen.  
  
 ![Unterstützte Konvertierungen: ODBC C-in SQL-Datentypen](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 Die Tabellen in den folgenden Abschnitten wird beschrieben, wie die Treiber oder die Datenquelle mit der Datenquelle gesendete Daten konvertiert; Treiber sind erforderlich, um Konvertierungen von alle ODBC C-Datentypen in die ODBC-SQL-Datentypen zu unterstützen, die sie unterstützen. Für einen bestimmten ODBC-C-Datentyp, werden die erste Spalte der Tabelle die zulässige Eingabewerte eines aufgeführt, mit die *ParameterType* -Argument in **SQLBindParameter**. Die zweite Spalte enthält die Ergebnisse eines Tests, die der Treiber ausgeführt werden, um zu bestimmen, ob sie die Daten konvertieren kann. Die dritte Spalte enthält den SQLSTATE zurückgegeben, die für jedes Ergebnis von **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**, oder **SQLPutData**. Daten werden an die Datenquelle gesendet werden, nur dann, wenn SQL_SUCCESS zurückgegeben wird.  
  
 Wenn die *ParameterType* -Argument in **SQLBindParameter** enthält den Bezeichner für eine ODBC-SQL-Datentyp, der in der Tabelle für einen bestimmten C-Datentyp nicht angezeigt wird **SQLBindParameter**SQLSTATE 07006 zurückgibt (geschützte Daten attributverletzung). Wenn die *ParameterType* -Argument enthält einen Treiber-spezifische Bezeichner und der Treiber unterstützt nicht die Konvertierung von der bestimmten ODBC-C-Datentyp in diesen treiberspezifischen SQL-Datentyp, **SQLBindParameter** SQLSTATE HYC00 zurückgibt (optionales Feature nicht implementiert).  
  
 Wenn die *ParameterValuePtr* und *StrLen_or_IndPtr* im angegebenen Argumente **SQLBindParameter** sind null-Zeiger, diese Funktion SQLSTATE HY009 zurückgegeben (ungültige die Verwendung eines null-Zeiger). Auch es nicht in den Tabellen angezeigt wird, wird durch eine Anwendung festlegt, den Wert der Längen-/Indikatorpuffer verweist die *StrLen_or_IndPtr* Argument **SQLBindParameter** oder den Wert des der  *StrLen_or_IndPtr* Argument **SQLPutData** auf SQL_NULL_DATA einen NULL-SQL-Daten-Wert angeben. (Die *StrLen_or_IndPtr* Argument entspricht Feld SQL_DESC_OCTET_LENGTH_PTR in APD.) Die Anwendung diese Werte SQL_NTS an, dass der Wert festgelegt \* *ParameterValuePtr* in **SQLBindParameter** oder \* *DataPtr*in **SQLPutData** (verweist das SQL_DESC_DATA_PTR-Feld der APD) ist eine Null-terminierte Zeichenfolge.  
  
 Die folgenden Begriffe werden in den Tabellen verwendet:  
  
-   **Die Bytelänge der Daten** : Gibt die Anzahl der Bytes der SQL-Daten, die zum Senden an die Datenquelle verfügbar, unabhängig davon, ob die Daten werden abgeschnitten, bevor sie mit der Datenquelle gesendet wird. Für eine Zeichenfolge enthält dieser Speicherplatz für die Null-Terminierungszeichen keine.  
  
-   **Spalte Bytelänge** -Anzahl der Bytes, die zum Speichern der Daten in der Datenquelle erforderlich sind.  
  
-   **Zeichen-Byte-Länge** : maximale Anzahl von Bytes, die zum Anzeigen von Daten in Form von Zeichen erforderlich sind. Dies ist für jeden SQL-Datentyp in gemäß [Größe anzeigen](../../../odbc/reference/appendixes/display-size.md), es sei denn Zeichen-Byte-Länge in Bytes ist, während die Größe der Anzeige in Zeichen ist.  
  
-   **Anzahl der Ziffern** : Gibt die Anzahl von Zeichen verwendet, um eine Zahl darzustellen, z. B. das Minuszeichen (-), Dezimaltrennzeichen und einem Exponenten (falls erforderlich).  
  
-   **Wörter in**   
     ***Kursiv*** -Elemente, die von der SQL-Grammatik. Die Syntax von grammatikelementen, finden Sie unter [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [C to SQL: Zeichen](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [C to SQL: Numerisch](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [C to SQL: Bit](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [C to SQL: Binärdatei](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [C to SQL: Datum](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [C to SQL: GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [C to SQL: Zeit](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [C to SQL: Zeitstempel](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [C to SQL: Jahr-Monat-Intervalle](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [C to SQL: Tag-Zeitintervalle](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [C to SQL Data Conversion Examples (Beispiele für die Datenkonvertierung von C zu SQL)](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
