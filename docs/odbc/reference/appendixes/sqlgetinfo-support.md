---
title: SQLGetInfo-Support | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a21c035a14814f51d4344894ef253b2cc844f4c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307801"
---
# <a name="sqlgetinfo-support"></a>SQLGetInfo-Unterstützung
Wenn ein ODBC 2. *x-Anwendung* ruft **SQLGetInfo** auf einen ODBC 3 *.x-Treiber* auf, die *InfoType-Argumente* in der folgenden Tabelle müssen unterstützt werden.  
  
|*Infotyp*|Rückgabe|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **Hinweis:** Dieser Informationstyp ist nicht veraltet; die Bitmasken in der Spalte rechts sind veraltet.|Eine SQLINTEGER-Bitmaske, die die Klauseln in der **ALTER TABLE-Anweisung** aufgibt, die von der Datenquelle unterstützt wird.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:<br /><br /> SQL_AT_DROP_COLUMN = Die Möglichkeit, Spalten zu löschen, wird unterstützt. Ob dies zu Kaskaden- oder Einschränkungsverhalten führt, ist treiberdefiniert. (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN = Die Möglichkeit, mehrere Spalten in einer einzelnen ALTER TABLE-Anweisung hinzuzufügen, wird unterstützt. Dieses Bit wird nicht mit anderen SQL_AT_ADD_COLUMN_XXX Bits oder SQL_AT_CONSTRAINT_XXX Bits kombiniert. (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Der Informationstyp wurde in ODBC 1.0 eingeführt; jede Bitmaske wird mit der Version beschriftet, in der sie eingeführt wurde.|Eine SQLINTEGER-Bitmaske, die die unterstützten Abrufrichtungsoptionen aufgibt.<br /><br /> Die folgenden Bitmasken werden in Verbindung mit dem Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_FIRST (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|Eine SQLINTEGER-Bitmaske, die die unterstützten Sperrtypen für das *fLock-Argument* in **SQLSetPos**aufgibt.<br /><br /> Die folgenden Bitmasken werden in Verbindung mit dem Flag verwendet, um zu bestimmen, welche Sperrtypen unterstützt werden:<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|Ein SQLSMALLINT-Wert, der den Grad der ODBC-Konformität angibt.<br /><br /> SQL_OAC_NONE = Keine<br /><br /> SQL_OAC_LEVEL1 = Stufe 1 unterstützt<br /><br /> SQL_OAC_LEVEL2 = Stufe 2 unterstützt|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|Ein SQLSMALLINT-Wert, der die vom Treiber unterstützte SQL-Grammatik angibt. Eine Definition von SQL-Konformitätsstufen finden Sie in [Anhang C: SQL-Grammatik.](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)<br /><br /> SQL_OSC_MINIMUM = Minimale Grammatik unterstützt<br /><br /> SQL_OSC_CORE = Kerngrammatik unterstützt<br /><br /> SQL_OSC_EXTENDED = Erweiterte Grammatik unterstützt|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Eine SQLINTEGER-Bitmaske, die die unterstützten Vorgänge in **SQLSetPos**aufgibt.<br /><br /> Die folgenden Bitmasken werden in Verbindung mit dem Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Eine SQLINTEGER-Bitmaske, die die unterstützten positionierten SQL-Anweisungen aufgibt.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Anweisungen unterstützt werden:<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Eine SQLINTEGER-Bitmaske, die die für den Cursor unterstützten Parallelitätssteuerungsoptionen aufgibt.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_SCCO_READ_ONLY = Cursor ist schreibgeschützt. Aktualisierungen sind nicht zulässig.<br /><br /> SQL_SCCO_LOCK = Cursor verwendet die niedrigste Sperrebene, die ausreicht, um sicherzustellen, dass die Zeile aktualisiert werden kann.<br /><br /> SQL_SCCO_OPT_ROWVER = Cursor verwendet eine optimistische Parallelitätssteuerung und vergleicht Zeilenversionen wie SQLBase ROWID oder Sybase TIMESTAMP.<br /><br /> SQL_SCCO_OPT_VALUES = Cursor verwendet eine optimistische Parallelitätssteuerung, um Werte zu vergleichen.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|Eine SQLINTEGER-Bitmaske, die aufschlüsselt, ob Änderungen, die eine Anwendung an einem statischen oder Keyset-gesteuerten Cursor über **SQLSetPos** oder positionierte Aktualisierungs- oder Löschanweisungen vorgenommen hat, von dieser Anwendung erkannt werden können.<br /><br /> SQL_SS_ADDITIONS = Hinzugefügte Zeilen sind für den Cursor sichtbar. Der Cursor kann zu diesen Zeilen scrollen. Wo diese Zeilen dem Cursor hinzugefügt werden, ist treiberabhängig.<br /><br /> SQL_SS_DELETIONS = Gelöschte Zeilen sind für den Cursor nicht mehr verfügbar und hinterlassen keine "Bohrung" im Resultset; nachdem der Cursor aus einer gelöschten Zeile gescrollt hat, kann er nicht zu dieser Zeile zurückkehren.<br /><br /> SQL_SS_UPDATES = Aktualisierungen von Zeilen sind für den Cursor sichtbar. Wenn der Cursor von einer aktualisierten Zeile aus scrollt und zu einer aktualisierten Zeile zurückkehrt, sind die vom Cursor zurückgegebenen Daten die aktualisierten Daten und nicht die ursprünglichen Daten. Diese Option gilt nur für statische Cursor oder Aktualisierungen von Keyset-gesteuerten Cursorn, die den Schlüssel nicht aktualisieren. Diese Option gilt nicht für einen dynamischen Cursor oder für den Fall, dass ein Schlüssel in einem gemischten Cursor geändert wird.<br /><br /> Ob eine Anwendung Änderungen erkennen kann, die von anderen Benutzern an der Ergebnismenge vorgenommen wurden, einschließlich anderer Cursor in derselben Anwendung, hängt vom Cursortyp ab.|  
  
 Eine ODBC 3 *.x-Anwendung,* die mit einem ODBC 3 *.x-Treiber* arbeitet, sollte **SQLGetInfo** nicht mit den in der obigen Tabelle beschriebenen *InfoType-Argumenten* aufrufen, sondern die im folgenden Absatz aufgeführten ODBC 3 *.x* *InfoType-Argumente* verwenden. Es gibt keine 1:1-Entsprechung zwischen *InfoType-Argumenten,* die in ODBC 2 verwendet werden. *x* und die in ODBC 3 *.x*verwendeten . Eine ODBC 3 *.x-Anwendung,* die mit einem ODBC 2 arbeitet. *der x-Treiber* hingegen sollte die zuvor beschriebenen *InfoType-Argumente* verwenden.  
  
 Einige der Informationstypen in der vorherigen Tabelle sind zugunsten der Cursorattribut-Informationstypen veraltet. Diese veralteten Informationstypen sind SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY und SQL_STATIC_SENSITIVITY. Die neuen Cursorattributtypen sind SQL_XXX_CURSOR_ATTRIBUTES1and SQL_XXX_CURSOR_ATTRIBUTES2, wobei XXX DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN oder STATIC entspricht. Jeder der neuen Typen gibt die Treiberfunktionen für einen einzelnen Cursortyp an. Weitere Informationen zu diesen Optionen finden Sie in der [SQLGetInfo-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
