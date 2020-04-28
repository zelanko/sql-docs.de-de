---
title: ODBC-Funktions Zusammenfassung | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c10cc7880cf941a1490f963e21e8b44bc91db215
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298921"
---
# <a name="odbc-function-summary"></a>ODBC – Funktionsübersicht
In der folgenden Tabelle werden die ODBC-Funktionen aufgelistet, die nach Typ der Aufgabe gruppiert sind, und die Konformitäts Bezeichnung und eine kurze Beschreibung des Zwecks der einzelnen Funktionen enthalten. Weitere Informationen zu Konformitäts Bezeichnungen finden Sie unter [ODBC und die Standard-CLI](../../../odbc/reference/odbc-and-the-standard-cli.md). Weitere Informationen zur Syntax und Semantik für jede Funktion finden Sie in der [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Eine Anwendung kann die **SQLGetInfo** -Funktion aufrufen, um Konformitäts Informationen zu einem Treiber zu erhalten. Um Informationen über die Unterstützung einer bestimmten Funktion in einem Treiber zu erhalten, kann eine Anwendung **SQLGetFunctions**aufrufen.  
  
|Aufgabe|Funktionsname|Konformitäts|Zweck|  
|----------|-------------------|-----------------|-------------|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|Ruft eine Umgebung, eine Verbindung, eine Anweisung oder ein Deskriptorhandle ab.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|Stellt eine Verbindung mit einem bestimmten Treiber über den Datenquellen Namen, die Benutzer-ID und das Kennwort her.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|Stellt eine Verbindung mit einem bestimmten Treiber mithilfe der Verbindungs Zeichenfolge her oder fordert die Verbindungs Dialogfelder des Treiber-Managers und Treibers für den Benutzer an.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|Gibt aufeinander folgende Ebenen von Verbindungs Attributen und gültigen Attributwerten zurück. Wenn ein Wert für jedes Verbindungs Attribut angegeben wurde, stellt eine Verbindung mit der Datenquelle her.|  
|Abrufen von Informationen über einen Treiber und eine Datenquelle|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|Gibt die Liste der verfügbaren Datenquellen zurück.<br /><br /> Gibt die Liste der installierten Treiber und ihrer Attribute zurück.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|Gibt Informationen über einen bestimmten Treiber und eine bestimmte Datenquelle zurück.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|Gibt unterstützte Treiberfunktionen zurück.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|Gibt Informationen zu unterstützten Datentypen zurück.|  
|Festlegen und Abrufen von Treiber Attributen|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|Legt ein Verbindungs Attribut fest.<br /><br /> Gibt den Wert eines Verbindungs Attributs zurück.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|Legt ein Umgebungs Attribut fest.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|Gibt den Wert eines Umgebungs Attributs zurück.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|Legt ein Anweisungs Attribut fest.|  
||['SQLGetStmtAttr'](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|Gibt den Wert eines Anweisungs Attributs zurück.|  
|Festlegen und Abrufen von Deskriptorfeldern|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|Gibt den Wert eines einzelnen deskriptorfelds zurück.<br /><br /> Gibt die Werte mehrerer Deskriptorfelder zurück.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|Legt ein einzelnes Deskriptorfeld fest.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|Legt mehrere Deskriptorfelder fest.|  
||[Sqlcopyde SC](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|Kopiert Deskriptorinformationen von einem Deskriptorhandle in ein anderes.|  
|Vorbereiten von SQL-Anforderungen|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|Bereitet eine SQL-Anweisung für die spätere Ausführung vor.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|Weist Speicher für einen Parameter in einer SQL-Anweisung zu.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|Gibt den einem Anweisungs Handle zugeordneten Cursor Namen zurück.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|Gibt einen Cursor Namen an.|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|Legt Optionen fest, die das Cursor Verhalten steuern.|  
|Senden von Anforderungen|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|Führt eine vorbereitete Anweisung aus<br /><br /> Führt eine Anweisung aus.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|Gibt den Text einer SQL-Anweisung zurück, die vom Treiber übersetzt wurde.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|Gibt die Beschreibung für einen bestimmten Parameter in einer-Anweisung zurück.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|Gibt die Anzahl der Parameter in einer-Anweisung zurück.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|Wird in Verbindung mit **SQLPutData** verwendet, um Parameterdaten zur Ausführungszeit bereitzustellen. (Nützlich für Long-Datenwerte.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|Sendet einen Teil oder einen gesamten Datenwert für einen Parameter. (Nützlich für Long-Datenwerte.)|  
|Abrufen von Ergebnissen und Informationen zu Ergebnissen|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Gibt die Anzahl der Zeilen zurück, die von einer INSERT-, Update-oder DELETE-Anforderung betroffen sind.<br /><br /> Gibt die Anzahl von Spalten im Resultset zurück.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|Beschreibt eine Spalte im Resultset.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|Beschreibt die Attribute einer Spalte im Resultset.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|Weist Speicher für eine Ergebnisspalte zu und gibt den Datentyp an.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|Gibt mehrere Ergebniszeilen zurück.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|Gibt scrollbare Ergebniszeilen zurück.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|Gibt einen Teil oder alle einer Spalte einer Zeile eines Resultsets zurück. (Nützlich für Long-Datenwerte.)|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|Positioniert einen Cursor innerhalb eines abgerufenen Datenblocks und ermöglicht es einer Anwendung, Daten im Rowset zu aktualisieren oder Daten im Resultset zu aktualisieren oder zu löschen.|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|Führt Massen Einfügungen und Massen Lesezeichen Vorgänge aus, einschließlich aktualisieren, löschen und Abrufen von Lesezeichen.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|Bestimmt, ob weitere Resultsets verfügbar sind, und initialisiert, wenn dies der Fall ist, die Verarbeitung für das nächste Resultset.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|Gibt zusätzliche Diagnoseinformationen zurück (ein einzelnes Feld der Diagnosedaten Struktur).|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|Gibt zusätzliche Diagnoseinformationen (mehrere Felder der Diagnosedaten Struktur) zurück.|  
|Abrufen von Informationen zu den Systemtabellen der Datenquelle (Katalog Funktionen)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> Gruppe öffnen|Gibt eine Liste von Spalten und zugeordneten Berechtigungen für eine oder mehrere Tabellen zurück.<br /><br /> Gibt die Liste der Spaltennamen in angegebenen Tabellen zurück.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|Gibt eine Liste mit Spaltennamen zurück, die Fremdschlüssel bilden, sofern Sie für eine angegebene Tabelle vorhanden sind.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|Gibt die Liste der Spaltennamen zurück, die den Primärschlüssel für eine Tabelle bilden.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|Gibt die Liste der Eingabe-und Ausgabeparameter sowie die Spalten zurück, die das Resultset für die angegebenen Prozeduren bilden.|  
||['SQLProcedures'](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|Gibt die Liste der in einer bestimmten Datenquelle gespeicherten Prozedur Namen zurück.|  
||['SQLSpecialColumns'](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Gruppe öffnen|Gibt Informationen über den optimalen Satz von Spalten zurück, die eine Zeile in einer angegebenen Tabelle eindeutig identifizieren, oder die Spalten, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird.|  
||['SQLStatistics'](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|Gibt Statistiken zu einer einzelnen Tabelle und der Liste der Indizes zurück, die der Tabelle zugeordnet sind.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|Gibt eine Liste von Tabellen und den Berechtigungen zurück, die den einzelnen Tabellen zugeordnet sind.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Gruppe öffnen|Gibt die Liste der in einer bestimmten Datenquelle gespeicherten Tabellennamen zurück.|  
|Beenden einer Anweisung|['SQLFreeStmt'](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|Beendet die Verarbeitung der Anweisung, verwirft ausstehende Ergebnisse und gibt optional alle dem Anweisungs Handle zugeordneten Ressourcen frei.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|Schließt einen Cursor, der für ein Anweisungs Handle geöffnet wurde.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|Bricht die Verarbeitung einer-Anweisung ab.|  
||[Sqlcancelhandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|Bricht die Verarbeitung einer-Anweisung oder-Verbindung ab.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|Führt einen Commit oder Rollback für eine Transaktion aus.|  
|Beenden einer Verbindung|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|Schließen der Verbindung.<br /><br /> Gibt eine Umgebung, eine Verbindung, eine Anweisung oder ein Deskriptorhandle frei.|
