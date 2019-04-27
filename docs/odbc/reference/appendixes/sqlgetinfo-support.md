---
title: SQLGetInfo-Unterstützung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLGetInfo
- backward compatibility [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], support
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6eb6bedb20e1f61c48776d03df59aa6865cfb2a3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62751210"
---
# <a name="sqlgetinfo-support"></a>SQLGetInfo-Unterstützung
Wenn eine ODBC-2. *x* Anwendungsaufrufe **SQLGetInfo** auf eine ODBC 3.*.x* -Treiber die *Informationsart* Argumente in der folgenden Tabelle unterstützt werden müssen.  
  
|*InfoType*|Rückgabewert|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **beachten:**  Dieses Typs wird nicht als veraltet markiert; die Bitmasken in der Spalte rechts sind veraltet.|Eine SQLINTEGER-Bitmaske, die die Klauseln in Aufzählen der **ALTER TABLE** -Anweisung von der Datenquelle unterstützt.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:<br /><br /> SQL_AT_DROP_COLUMN = die Möglichkeit zum Löschen von Spalten wird unterstützt. Ob dies führt zu Cascade oder Einschränken von Verhalten werden-Treiber definiert. (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN = die Möglichkeit zum Hinzufügen mehrerer Spalten in einer einzelnen ALTER TABLE-Anweisung wird unterstützt. Dieses Bit ist nicht mit anderen SQL_AT_ADD_COLUMN_XXX Bits oder SQL_AT_CONSTRAINT_XXX Bits kombiniert werden. (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Der Informationstyp wurde in ODBC-1.0 eingeführt. Jede Bitmaske ist mit der Version mit der Bezeichnung in der sie eingeführt wurde.|Eine SQLINTEGER-Bitmaske, die die unterstützte Richtung Abrufoptionen auflisten.<br /><br /> Die folgenden Bitmasken werden in Verbindung mit dem Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_FIRST (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|Eine SQLINTEGER-Bitmaske, die die unterstützten Sperre aufzählen-Typen für die *Bestand* -Argument in **SQLSetPos**.<br /><br /> Die folgenden Bitmasken werden in Verbindung mit dem Flag verwendet, um zu bestimmen, welche Typen von Sperren unterstützt werden:<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|Ein SQLSMALLINT-Wert, der die ODBC-Übereinstimmung angibt.<br /><br /> SQL_OAC_NONE = None<br /><br /> SQL_OAC_LEVEL1 = Ebene-1 unterstützt<br /><br /> SQL_OAC_LEVEL2 = Ebene-2 unterstützt|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|Ein SQLSMALLINT-Wert, der angibt, die vom Treiber unterstützt SQL-Grammatik. Finden Sie unter [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) eine Definition der SQL-Übereinstimmungsebenen.<br /><br /> SQL_OSC_MINIMUM = Minimum-Grammatik unterstützt<br /><br /> SQL_OSC_CORE = Core-Grammatik unterstützt<br /><br /> SQL_OSC_EXTENDED = erweiterte-Grammatik unterstützt|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Eine SQLINTEGER-Bitmaske, die in die unterstützten Vorgänge auflisten **SQLSetPos**.<br /><br /> Die folgenden Bitmasken werden verwendet, in Verbindung mit dem Flag um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH   (ODBC 2.0) SQL_POS_UPDATE     (ODBC 2.0) SQL_POS_DELETE     (ODBC 2.0) SQL_POS_ADD          (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Eine SQLINTEGER-Bitmaske Auflisten von unterstützten positioniert SQL-Anweisungen.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Anweisungen werden unterstützt:<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Eine SQLINTEGER-Bitmaske, die die Steuerelement-Parallelitätsoptionen für den Cursor unterstützt auflisten.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_SCCO_READ_ONLY = Cursor ist schreibgeschützt. Es sind keine Updates zulässig.<br /><br /> SQL_SCCO_LOCK = Cursor verwendet die niedrigste Ebene von Sperren ausreichen, um sicherzustellen, dass die Zeile aktualisiert werden kann.<br /><br /> SQL_SCCO_OPT_ROWVER = Cursor verwendet Steuerung durch vollständige Parallelität, Vergleichen von Zeilenversionen, z. B. SQLBase ROWID oder Sybase-TIMESTAMP.<br /><br /> SQL_SCCO_OPT_VALUES = Cursor verwendet Steuerung durch vollständige Parallelität, Vergleichen von Werten.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|Eine SQLINTEGER Bitmaske Auflisten von, ob eine Anwendung in eine statische oder keysetgesteuerte Cursor über Änderungen **SQLSetPos** oder positionierte Update- oder Delete-Anweisungen von dieser Anwendung erkannt werden können.<br /><br /> SQL_SS_ADDITIONS = hinzugefügte Zeilen sind sichtbar, bis zum Cursor; der Cursor kann auf diese Spalten scrollen. In denen diese Zeilen hinzugefügt werden, bis des Cursors ist treiberabhängig.<br /><br /> SQL_SS_DELETIONS = der gelöschte Zeilen sind nicht mehr verfügbar, bis zum Cursor und lassen sich nicht auf eine "Lücke" im Resultset; Nachdem Sie der Cursor aus einer gelöschten Zeile einen Bildlauf durchführt, können keine Zeile zurückgegeben werden.<br /><br /> SQL_SS_UPDATES = Updates von Zeilen sind sichtbar, bis zum Cursor; Wenn der Cursor führt einen Bildlauf aus, und es auf eine aktualisierte Zeile zurückgibt, ist die vom Cursor zurückgegebenen Daten die aktualisierten Daten, nicht die ursprünglichen Daten. Diese Option gilt nur statische Cursor oder Updates auf keysetgesteuerte Cursor, die den Schlüssel nicht aktualisieren. Diese Option gilt nicht für einen dynamischen Cursor oder in der Fall, in dem ein Schlüssel in einem gemischten Cursor geändert wird.<br /><br /> Ob eine Anwendung Änderungen an das Resultset nach anderen Benutzern, einschließlich anderer Cursor in der gleichen Anwendung erkennen kann, hängt von der Cursortyp ab.|  
  
 Eine ODBC 3.*.x* Anwendung mit einer ODBC 3.*.x* Treiber sollte nicht aufrufen **SQLGetInfo** mit der *Informationsart* Argumente beschriebene die obige Tabelle sollten jedoch verwenden, die ODBC 3.*.x* *Informationsart* Argumente, die im folgenden Abschnitt aufgeführt. Es ist nicht zwischen *Informationsart* in ODBC 2. verwendeten Argumente. *X* auch solche, die in ODBC 3. verwendet *.x*. Eine ODBC 3.*.x* Anwendung mit einer ODBC 2. *X* , auf der anderen Seite sollte Treiber verwenden, die *Informationsart* Argumente zuvor beschrieben.  
  
 Einige der Informationstypen in der vorherigen Tabelle werden durch die Cursortypen für Attribute Informationen ersetzt. Diese als Informationen, die Typen SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY und SQL_STATIC_SENSITIVITY sind veraltet. Die neuen Attribute-Cursortypen sind SQL_XXX_CURSOR_ATTRIBUTES1and SQL_XXX_CURSOR_ATTRIBUTES2, wobei XXX DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN oder statischen gleich ist. Jedes neue Typen gibt die Treiber-Funktionen für eine einmalige Cursor-Datentyp an. Weitere Informationen zu diesen Optionen finden Sie unter den [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.
