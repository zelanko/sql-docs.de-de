---
title: Konvertieren von Daten aus SQL in C-Datentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6819b28ba57f1e6314535a6a90ad13de39b4842c
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793198"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>Konvertieren von Daten von SQL- zu C-Datentypen
Wenn eine Anwendung ruft **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData**, ruft der Treiber die Daten aus der Datenquelle. Bei Bedarf die Daten aus dem Datentyp konvertiert sie in dem der Treiber, die den angegebenen Datentyp abgerufen die *TargetType* -Argument in **SQLBindCol** oder **SQLGetData.** Zum Schluss speichert die Daten in den Speicherort verweist die *TargetValuePtr* -Argument in **SQLBindCol** oder **SQLGetData** (und das SQL_DESC_DATA_PTR-Feld, der die ARD).  
  
 Die folgende Tabelle zeigt die unterstützten Konvertierungen von ODBC-SQL-Datentypen in ODBC-C-Datentypen. Ein ausgefüllten Kreis gibt an, die standardkonvertierung für einen SQL-Datentyp (der C-Datentyp, der die Daten werden, wenn konvertiert werden, der Wert des *TargetType* SQL_C_DEFAULT ist). Ein leerer Kreis gibt an, eine Konvertierung unterstützt wird.  
  
 Für eine ODBC *3.x* arbeiten mit einer ODBC-Anwendung *2.x* Treiber, die Konvertierung vom Treiber-spezifische Typen möglicherweise nicht unterstützt.  
  
 Das Format der konvertierten Daten ist von der Windows® Land-Einstellung nicht betroffen.  
  
 Die Tabellen in den folgenden Abschnitten wird beschrieben, wie die Treiber oder die Datenquelle aus der Datenquelle abgerufene Daten konvertiert; Treiber müssen zur Unterstützung von Konvertierungen in alle ODBC C-Datentypen aus den ODBC-SQL-Datentypen, die sie unterstützen. Für einen bestimmten ODBC-SQL-Datentyp, werden die erste Spalte der Tabelle die zulässige Eingabewerte eines aufgeführt, mit die *TargetType* -Argument in **SQLBindCol** und **SQLGetData**. Die zweite Spalte enthält die Ergebnisse eines Tests, die häufig mit der *Pufferlänge* angegebene Argument in **SQLBindCol** oder **SQLGetData**, der der Treiber ausgeführt werden, Bestimmen Sie, ob sie die Daten konvertieren kann. Für jedes Ergebnis Auflisten der dritten und vierten Spalte die Werte in den Puffern, die anhand des platziert die *TargetValuePtr* und *StrLen_or_IndPtr* im angegebenen Argumente **SQLBindCol** oder **SQLGetData** nach dem der Treiber versucht hat, um Daten zu konvertieren. (Die *StrLen_or_IndPtr* Argument entspricht dem Feld SQL_DESC_OCTET_LENGTH_PTR, der die ARD.) Die letzte Spalte enthält den SQLSTATE zurückgegeben, die für jedes Ergebnis von **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData**.  
  
 Wenn die *TargetType* -Argument in **SQLBindCol** oder **SQLGetData** enthält einen Bezeichner für einen ODBC-C-Datentyp nicht angezeigt, in der Tabelle für einen bestimmten ODBC-SQL-Datentyp,  **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData** SQLSTATE 07006 zurückgibt (geschützte Daten attributverletzung). Wenn die *TargetType* -Argument enthält einen Bezeichner, der eine Konvertierung von einem treiberspezifischen SQL-Datentyp in einen ODBC-C-Datentyp gibt an, und diese Konvertierung wird nicht vom Treiber unterstützt **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData** SQLSTATE HYC00 zurückgibt (optionales Feature nicht implementiert).  
  
 Obwohl es nicht in den Tabellen angezeigt wird, gibt der Treiber SQL_NULL_DATA im Puffer anhand der *StrLen_or_IndPtr* Argument, wenn der SQL-Daten-Wert NULL ist. Eine Erläuterung zur Verwendung von *StrLen_or_IndPtr* Wenn mehrere Aufrufe zum Abrufen von Daten vorgenommen werden, finden Sie unter den [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)funktionsbeschreibung. Wenn SQL-Daten in C-Zeichendaten konvertiert werden, wird die Anzahl der Zeichen in zurückgegeben \* *StrLen_or_IndPtr* schließt nicht das Byte Null-Terminierung vorliegt. Wenn *TargetValuePtr* ist ein null-Zeiger **SQLGetData** SQLSTATE HY009 zurückgegeben (Ungültige Verwendung von null-Zeiger), in **SQLBindCol**, dies hebt die Bindung der Spalte.  
  
 Die folgenden Begriffe und Konventionen werden in den Tabellen verwendet:  
  
-   **Die Bytelänge der Daten** ist die Anzahl der Datenbytes C zur Verfügung, die in zurückgegeben **TargetValuePtr*, unabhängig davon, ob Daten abgeschnitten werden, bevor er an die Anwendung zurückgegeben wird. Für Zeichenfolgendaten schließt dies nicht den Speicherplatz für das Null-Abschlusszeichen.  
  
-   **Zeichen-Byte-Länge** ist die Gesamtzahl der Bytes, die zum Anzeigen der Daten im Zeichenformat benötigt. Dies ist für jede C-Datentyp im Abschnitt definiert [Größe anzeigen](../../../odbc/reference/appendixes/display-size.md), außer dass Zeichen-Byte-Länge in Byte ist, während die Größe der Anzeige in Zeichen ist.  
  
-   Wörter im *Kursiv* stellen die Argumente der Funktion oder Elemente an die SQL-Grammatik dar. Die Syntax von grammatikelementen, finden Sie unter [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [SQL zu C: Zeichen](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL zu C: Numerisch](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL zu C: Bit](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL zu C: Binary](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL zu C: Datum](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL zu C: GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL zu C: Zeit](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL zu C: Timestamp](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL zu C: Jahr-Monat-Intervalle](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL zu C: Tag-Zeitintervalle](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [SQL to C Data Conversion Examples (Beispiele für die Datenkonvertierung von SQL zu C)](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
