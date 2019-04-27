---
title: ODBC-Funktionszusammenfassung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6829f4f5197fca28944e5bc9d2f636f6624c9d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62653332"
---
# <a name="odbc-function-summary"></a>ODBC – Funktionsübersicht
Die folgende Tabelle listet ODBC-Funktionen, gruppiert nach Typ der Aufgabe, und enthält die Konformität-Bezeichnung und eine kurze Beschreibung des Zwecks der einzelnen Funktionen. Weitere Informationen zu Konformität Bezeichnungen, finden Sie unter [ODBC und die Standard-CLI](../../../odbc/reference/odbc-and-the-standard-cli.md). Weitere Informationen zur Syntax und Semantik für die einzelnen Funktionen finden Sie unter [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Kann eine Anwendung Aufrufen der **SQLGetInfo** Funktion, um Übereinstimmung mit Standards Informationen über einen Treiber zu erhalten. Um Informationen zur Unterstützung für eine bestimmte Funktion in einen Treiber zu erhalten, kann eine Anwendung aufrufen **SQLGetFunctions**.  
  
|Aufgabe|Funktionsname|Übereinstimmung mit Standards|Zweck|  
|----------|-------------------|-----------------|-------------|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|Ruft ein Handle-Umgebung, Verbindung, Anweisung oder Deskriptor ab.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|Stellt eine Verbindung her, um einen bestimmten Treiber vom ODBC-Datenquellenname, Benutzer-ID und Kennwort.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|Verbindung zu einem bestimmten Treiber Verbindungszeichenfolge oder fordert an, dass der Treiber-Manager und Treiber Verbindung-Dialogfelder für den Benutzer angezeigt.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|Gibt die aufeinander folgenden Steuerungsebenen-Verbindungsattributen und die gültigen Attributwerte. Wenn Sie ein Wert für jedes Verbindungsattribut angegeben wurde, verbindet mit der Datenquelle.|  
|Abrufen von Informationen über einen Treiber und der Datenquelle|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|Gibt die Liste der verfügbaren Datenquellen zurück.<br /><br /> Gibt die Liste der installierten Treiber und deren Attribute zurück.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|Gibt Informationen zu einem bestimmten Treiber und einer Datenquelle zurück.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|Gibt unterstützt Treiberfunktionen.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|Gibt Informationen zu unterstützten Datentypen zurück.|  
|Festlegen und Abrufen des Treiber-Attribute|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|Legt ein Verbindungsattribut fest.<br /><br /> Gibt den Wert eines Attributs für die Verbindung.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|Legt ein Umgebungsattribut fest.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|Gibt den Wert eines Attributs für die Umgebung.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|Legt ein Anweisungsattribut fest.|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|Gibt den Wert eines Attributs Anweisung.|  
|Festlegen und Abrufen von deskriptorfelder|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|Gibt den Wert einer einzelnen Deskriptorfeld zurück.<br /><br /> Gibt die Werte von deskriptorfelder für mehrere zurück.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|Legt eine einzelne Deskriptorfeld fest.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|Legt mehrere deskriptorfelder fest.|  
||[SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|Kopiert Informationen der Sicherheitsbeschreibung aus einen Deskriptorhandle.|  
|Vorbereiten von SQL-Anforderungen|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|Bereitet eine SQL-Anweisung für die spätere Ausführung vor.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|Weist Speicher für einen Parameter in einer SQL-Anweisung.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|Gibt zurück, der Name des Cursors ein Anweisungshandle zugeordnet.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|Gibt einen Cursor an.|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|Legt Optionen fest, das Cursorverhalten gesteuert.|  
|Übermittlung von Anforderungen|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|Führt eine vorbereitete Anweisung aus<br /><br /> Führt eine Anweisung aus.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|Gibt den Text der SQL-Anweisung zurück, wie von der Treiber übersetzt.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|Gibt die Beschreibung für einen bestimmten Parameter in einer Anweisung zurück.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|Gibt die Anzahl von Parametern in einer Anweisung zurück.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|Zusammen mit **SQLPutData** Parameterdaten zum Zeitpunkt der Ausführung angeben. (Nützlich für lange Datenwerte.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|Sendet einen Datenwert für einen Parameter ganz oder teilweise an. (Nützlich für lange Datenwerte.)|  
|Abrufen der Ergebnisse und Informationen zu Ergebnissen|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Gibt die Anzahl der Zeilen, die von einer INSERT-, Update- oder Delete-Anforderung betroffen sind.<br /><br /> Gibt die Anzahl von Spalten im Resultset zurück.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|Beschreibt eine Spalte im Resultset.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|Beschreibt die Attribute einer Spalte im Resultset.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|Weist Speicher für eine Ergebnisspalte und gibt den Datentyp an.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|Mehrere Ergebniszeilen zurückgegeben.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|Scrollfähigen Resultsets Zeilen zurückgegeben.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|Gibt teilweise oder vollständig eine Spalte einer Zeile eines Resultsets festgelegt. (Nützlich für lange Datenwerte.)|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|Positioniert einen Cursor in einem Block abgerufenen Daten und ermöglicht es einer Anwendung, um Daten im Rowset zu aktualisieren oder zu aktualisieren oder Löschen von Daten im Resultset.|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|Führt die Bulk-einfügungen und Bulk-Lesezeichen Vorgänge, einschließlich aktualisieren, löschen und durch Lesezeichen abrufen.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|Bestimmt, ob weitere Resultsets verfügbar sind und, wenn dies der Fall ist, initialisiert die Verarbeitung für das nächste Resultset.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|Gibt zusätzliche Diagnoseinformationen (einem einzelnen Feld der Diagnosedaten-Struktur) zurück.|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|Gibt zusätzliche Diagnoseinformationen (mehrere Felder der Struktur Diagnosedaten) zurück.|  
|Abrufen von Informationen zu Systemtabellen für die Datenquelle (Katalogfunktionen)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> Gruppe öffnen|Gibt eine Liste von Spalten und zugeordnete Berechtigungen für eine oder mehrere Tabellen.<br /><br /> Gibt die Liste der Spaltennamen in angegebenen Tabellen zurück.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|Gibt eine Liste der Spaltennamen, die foreign key, bilden zurück, wenn sie für eine angegebene Tabelle vorhanden sind.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|Gibt die Liste der Spaltennamen, die den Primärschlüssel für eine Tabelle bilden.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|Gibt die Liste der Input und Output-Parameter als auch die Spalten, aus denen das Resultset für die angegebenen Prozeduren zurück.|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|Gibt die Liste der Prozedurnamen, die in einer bestimmten Datenquelle gespeichert.|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Gruppe öffnen|Gibt Informationen zu den optimalen Satz von Spalten, die eine Zeile in einer angegebenen Tabelle eindeutig identifiziert, oder die Spalten, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird.|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|Gibt Statistiken zu einer einzelnen Tabelle und die Liste der Indizes der Tabelle zugeordnet.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|Gibt eine Liste von Tabellen und die Berechtigungen, die jeder Tabelle zugeordnet.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Gruppe öffnen|Gibt die Liste mit den Tabellennamen in einer bestimmten Datenquelle gespeichert.|  
|Eine Anweisung beenden|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|Anweisungsverarbeitung endet, ausstehende Ergebnisse verworfen, und gibt optional das Anweisungshandle zugeordnete Ressourcen frei.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|Schließt einen Cursor, der für ein Anweisungshandle geöffnet wurde.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|Bricht die Verarbeitung in einer Anweisung ab.|  
||[SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|Bricht die Verarbeitung auf eine Anweisung oder die Verbindung ab.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|Ein Commit oder Rollback einer Transaktion.|  
|Beenden einer Verbindung|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|Schließt die Verbindung.<br /><br /> Gibt eine Umgebung, Verbindung, Anweisung oder Deskriptor Handle frei.|
