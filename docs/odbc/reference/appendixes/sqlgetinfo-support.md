---
description: SQLGetInfo-Unterstützung
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cff18a23c7d8c4526fc86904d75375ed5aaaf5a7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471231"
---
# <a name="sqlgetinfo-support"></a>SQLGetInfo-Unterstützung
Bei ODBC 2. die *x* -Anwendung ruft **SQLGetInfo** für einen ODBC 3 *. x* -Treiber auf. die *InfoType* -Argumente in der folgenden Tabelle müssen unterstützt werden.  
  
|*Infotype*|Rückgabe|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2,0) **Hinweis:**  dieser Informationstyp ist nicht veraltet. die Bitmasken in der Spalte auf der rechten Seite sind veraltet.|Eine SQLINTEGER-Bitmaske, die die-Klauseln in der **ALTER TABLE** -Anweisung auflistet, die von der Datenquelle unterstützt wird.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Klauseln unterstützt werden:<br /><br /> SQL_AT_DROP_COLUMN = die Möglichkeit zum Löschen von Spalten wird unterstützt. Ob dies zur Folge hat, dass das Verhalten kaskadiert oder eingeschränkt wird, ist Treiber definiert (ODBC 2,0)<br /><br /> SQL_AT_ADD_COLUMN = die Möglichkeit, mehrere Spalten in einer einzelnen ALTER TABLE-Anweisung hinzuzufügen, wird unterstützt. Dieses Bit wird nicht mit anderen SQL_AT_ADD_COLUMN_XXX Bits oder SQL_AT_CONSTRAINT_XXX Bits kombiniert. (ODBC 2,0)|  
|SQL_FETCH_DIRECTION (ODBC 1,0)<br /><br /> Der Informationstyp wurde in ODBC 1,0 eingeführt. jede Bitmaske ist mit der Version gekennzeichnet, in der Sie eingeführt wurde.|Eine SQLINTEGER-Bitmaske, die die unterstützten Optionen für die Abruf Richtung auflistet.<br /><br /> Die folgenden Bitmasken werden zusammen mit dem-Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1,0) SQL_FD_FETCH_FIRST (ODBC 1,0) SQL_FD_FETCH_LAST (ODBC 1,0) SQL_FD_FETCH_PRIOR (ODBC 1,0) SQL_FD_FETCH_ABSOLUTE (ODBC 1,0) SQL_FD_FETCH_RELATIVE (ODBC 1,0) SQL_FD_FETCH_BOOKMARK (ODBC 2,0)|  
|SQL_LOCK_TYPES (ODBC 2,0)|Eine SQLINTEGER-Bitmaske, die die unterstützten Sperr Typen für das *fLock* -Argument in **SQLSetPos**auflistet.<br /><br /> Die folgenden Bitmasken werden zusammen mit dem-Flag verwendet, um zu bestimmen, welche Sperr Typen unterstützt werden:<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1,0)|Ein SQLSMALLINT-Wert, der die Ebene der ODBC-Konformität angibt.<br /><br /> SQL_OAC_NONE = None<br /><br /> SQL_OAC_LEVEL1 = Ebene 1 wird unterstützt.<br /><br /> SQL_OAC_LEVEL2 = Ebene 2 unterstützt|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1,0)|Ein SQLSMALLINT-Wert, der die vom Treiber unterstützte SQL-Grammatik angibt. Eine Definition der SQL-Konformitätsstufen finden Sie in [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) .<br /><br /> SQL_OSC_MINIMUM = minimale Grammatik unterstützt<br /><br /> SQL_OSC_CORE = Kern Grammatik unterstützt<br /><br /> SQL_OSC_EXTENDED = erweiterte Grammatik unterstützt|  
|SQL_POS_OPERATIONS (ODBC 2,0)|Eine SQLINTEGER-Bitmaske, die die unterstützten Vorgänge in **SQLSetPos**auflistet.<br /><br /> Die folgenden Bitmasken werden zusammen mit dem-Flag verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_POS_POSITION (ODBC 2,0) SQL_POS_REFRESH (ODBC 2,0) SQL_POS_UPDATE (ODBC 2,0) SQL_POS_DELETE (ODBC 2,0) SQL_POS_ADD (ODBC-2,0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2,0)|Eine SQLINTEGER-Bitmaske, die die unterstützten positionierten SQL-Anweisungen auflistet.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche-Anweisungen unterstützt werden:<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1,0)|Eine SQLINTEGER-Bitmaske, die die für den Cursor unterstützten Parallelitäts kontrollenoptionen auflistet.<br /><br /> Die folgenden Bitmasken werden verwendet, um zu bestimmen, welche Optionen unterstützt werden:<br /><br /> SQL_SCCO_READ_ONLY = Cursor ist schreibgeschützt. Es sind keine Updates zulässig.<br /><br /> SQL_SCCO_LOCK = Cursor verwendet die niedrigste Sperr Ebene, um sicherzustellen, dass die Zeile aktualisiert werden kann.<br /><br /> SQL_SCCO_OPT_ROWVER = Cursor verwendet die Steuerung der vollständigen Parallelität und vergleicht Zeilen Versionen, wie z. b. SQLBase ROWID oder den Sybase-Zeitstempel.<br /><br /> SQL_SCCO_OPT_VALUES = Cursor verwendet die Steuerung der vollständigen Parallelität, wobei Werte verglichen werden.|  
|SQL_STATIC_SENSITIVITY (ODBC 2,0)|Eine SQLINTEGER-Bitmaske, die auflistet, ob von der Anwendung Änderungen, die von einer Anwendung an einem statischen oder keysetgesteuerten Cursor über **SQLSetPos** oder positionierte UPDATE-oder DELETE-Anweisungen vorgenommen werden, erkannt werden können.<br /><br /> SQL_SS_ADDITIONS = hinzugefügte Zeilen sind für den Cursor sichtbar. der Cursor kann einen Bildlauf zu diesen Zeilen durchführen. Wo diese Zeilen dem Cursor hinzugefügt werden, ist Treiber abhängig.<br /><br /> SQL_SS_DELETIONS = gelöschte Zeilen sind nicht mehr für den Cursor verfügbar und lassen kein "Loch" im Resultset aus. Nachdem der Cursor einen Bildlauf aus einer gelöschten Zeile durchgeführt hat, kann er nicht zu dieser Zeile zurückkehren<br /><br /> SQL_SS_UPDATES = Aktualisierungen von Zeilen sind für den Cursor sichtbar. Wenn der Cursor einen Bildlauf durchführt und zu einer aktualisierten Zeile zurückkehrt, sind die vom Cursor zurückgegebenen Daten die aktualisierten Daten, nicht die ursprünglichen Daten. Diese Option gilt nur für statische Cursor oder Aktualisierungen von keysetgesteuerten Cursorn, die den Schlüssel nicht aktualisieren. Diese Option gilt nicht für einen dynamischen Cursor oder in dem Fall, in dem eine Taste in einem gemischten Cursor geändert wird.<br /><br /> Ob eine Anwendung Änderungen erkennen kann, die von anderen Benutzern an dem Resultset vorgenommen wurden, einschließlich anderer Cursor in derselben Anwendung, hängt vom Cursortyp ab.|  
  
 Eine ODBC 3 *. x* -Anwendung, die mit einem ODBC 3 *. x* -Treiber arbeitet, sollte **SQLGetInfo** nicht mit den *InfoType* -Argumenten aufrufen, die in der obigen Tabelle beschrieben sind, aber die im folgenden Absatz aufgeführten ODBC 3 *. x* - *InfoType* -Argumente verwenden sollten. Es gibt keine eins-zu-eins-Entsprechung zwischen den *InfoType* -Argumenten, die in ODBC 2 verwendet werden. *x* und die in ODBC 3 *. x*verwendeten. Eine ODBC 3 *. x* -Anwendung, die mit ODBC 2 arbeitet. der *x* -Treiber hingegen sollte die zuvor beschriebenen *InfoType* -Argumente verwenden.  
  
 Einige der Informationstypen in der vorherigen Tabelle sind zugunsten der Informationen zu den Cursor Attributen veraltet. Diese veralteten Informationstypen sind SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY und SQL_STATIC_SENSITIVITY. Die neuen Cursor Attributtypen sind SQL_XXX_CURSOR_ATTRIBUTES1and SQL_XXX_CURSOR_ATTRIBUTES2, wobei xxx dem dynamischen, FORWARD_ONLY, KEYSET_DRIVEN oder Static-Attribut gleicht. Jeder der neuen Typen gibt die Treiberfunktionen für einen einzelnen Cursortyp an. Weitere Informationen zu diesen Optionen finden Sie in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.
