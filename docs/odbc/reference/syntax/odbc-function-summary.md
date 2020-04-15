---
title: ODBC-Funktionsübersicht | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298921"
---
# <a name="odbc-function-summary"></a>ODBC – Funktionsübersicht
Die folgende Tabelle listet ODBC-Funktionen auf, gruppiert nach Aufgabentyp, und enthält die Konformitätsbezeichnung und eine kurze Beschreibung des Zwecks jeder Funktion. Weitere Informationen zu Konformitätsbezeichnungen finden Sie unter [ODBC und die Standard CLI](../../../odbc/reference/odbc-and-the-standard-cli.md). Weitere Informationen zur Syntax und Semantik für jede Funktion finden Sie unter [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Eine Anwendung kann die **SQLGetInfo-Funktion** aufrufen, um Konformitätsinformationen zu einem Treiber abzurufen. Um Informationen zur Unterstützung für eine bestimmte Funktion in einem Treiber zu erhalten, kann eine Anwendung **SQLGetFunctions**aufrufen.  
  
|Aufgabe|Funktionsname|Konformität|Zweck|  
|----------|-------------------|-----------------|-------------|  
|Herstellen einer Verbindung mit einer Datenquelle|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|Ruft ein Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptor-Handle ab.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|Stellt eine Verbindung mit einem bestimmten Treiber nach Datenquellenname, Benutzer-ID und Kennwort her.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|Stellt eine Verbindung mit einem bestimmten Treiber über eine Verbindungszeichenfolge her oder fordert an, dass der Treiber-Manager und der Treiber verbindungsdialogfelder für den Benutzer anzeigen.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|Gibt aufeinanderfolgende Ebenen von Verbindungsattributen und gültigen Attributwerten zurück. Wenn für jedes Verbindungsattribut ein Wert angegeben wurde, stellt eine Verbindung mit der Datenquelle her.|  
|Abrufen von Informationen zu einem Treiber und einer Datenquelle|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|Gibt die Liste der verfügbaren Datenquellen zurück.<br /><br /> Gibt die Liste der installierten Treiber und deren Attribute zurück.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|Gibt Informationen zu einem bestimmten Treiber und einer bestimmten Datenquelle zurück.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|Gibt unterstützte Treiberfunktionen zurück.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|Gibt Informationen zu unterstützten Datentypen zurück.|  
|Festlegen und Abrufen von Treiberattributen|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|Legt ein Verbindungsattribut fest.<br /><br /> Gibt den Wert eines Verbindungsattributs zurück.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|Legt ein Umgebungsattribut fest.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|Gibt den Wert eines Umgebungsattributs zurück.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|Legt ein Anweisungsattribut fest.|  
||['SQLGetStmtAttr'](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|Gibt den Wert eines Anweisungsattributs zurück.|  
|Festlegen und Abrufen von Deskriptorfeldern|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|Gibt den Wert eines einzelnen Deskriptorfelds zurück.<br /><br /> Gibt die Werte mehrerer Deskriptorfelder zurück.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|Legt ein einzelnes Deskriptorfeld fest.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|Legt mehrere Deskriptorfelder fest.|  
||[SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|Kopiert Deskriptorinformationen von einem Deskriptorhandle in ein anderes.|  
|Vorbereiten von SQL-Anforderungen|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|Bereitet eine SQL-Anweisung für die spätere Ausführung vor.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|Weist Speicher für einen Parameter in einer SQL-Anweisung zu.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|Gibt den Cursornamen zurück, der einem Anweisungshandle zugeordnet ist.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|Gibt einen Cursornamen an.|  
||[SQLSetScrollOptionen](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|Legt Optionen fest, die das Cursorverhalten steuern.|  
|Einreichen von Anfragen|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|Führt eine vorbereitete Anweisung aus<br /><br /> Führt eine Anweisung aus.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|Gibt den Text einer SQL-Anweisung zurück, wie vom Treiber übersetzt.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|Gibt die Beschreibung für einen bestimmten Parameter in einer Anweisung zurück.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|Gibt die Anzahl der Parameter in einer Anweisung zurück.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|Wird in Verbindung mit **SQLPutData** verwendet, um Parameterdaten zur Ausführungszeit anzugeben. (Nützlich für lange Datenwerte.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|Sendet einen Teil oder den gesamten Datenwert für einen Parameter. (Nützlich für lange Datenwerte.)|  
|Abrufen von Ergebnissen und Informationen zu Ergebnissen|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Gibt die Anzahl der Zeilen zurück, die von einer Einfüge-, Aktualisierungs- oder Löschanforderung betroffen sind.<br /><br /> Gibt die Anzahl von Spalten im Resultset zurück.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|Beschreibt eine Spalte im Resultset.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|Beschreibt Attribute einer Spalte im Resultset.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|Weist Speicher für eine Ergebnisspalte zu und gibt den Datentyp an.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|Gibt mehrere Ergebniszeilen zurück.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|Gibt scrollbare Ergebniszeilen zurück.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|Gibt einen Teil oder die gesamte Spalte einer Zeile eines Resultsets zurück. (Nützlich für lange Datenwerte.)|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|Positioniert einen Cursor innerhalb eines abgerufenen Datenblocks und ermöglicht es einer Anwendung, Daten im Rowset zu aktualisieren oder Daten im Resultset zu aktualisieren oder zu löschen.|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|Führt Masseneinfügungen und Massentextmarkenvorgänge aus, einschließlich Aktualisieren, Löschen und Abrufen nach Lesezeichen.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|Legt fest, ob weitere Resultsets verfügbar sind, und initialisiert, falls ja, die Verarbeitung für das nächste Resultset.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|Gibt zusätzliche Diagnoseinformationen zurück (ein einzelnes Feld der Diagnosedatenstruktur).|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|Gibt zusätzliche Diagnoseinformationen zurück (mehrere Felder der Diagnosedatenstruktur).|  
|Abrufen von Informationen zu den Systemtabellen der Datenquelle (Katalogfunktionen)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> Gruppe öffnen|Gibt eine Liste von Spalten und zugeordneten Berechtigungen für eine oder mehrere Tabellen zurück.<br /><br /> Gibt die Liste der Spaltennamen in angegebenen Tabellen zurück.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|Gibt eine Liste von Spaltennamen zurück, aus denen Fremdschlüssel bestehen, sofern sie für eine angegebene Tabelle vorhanden sind.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|Gibt die Liste der Spaltennamen zurück, aus denen der Primärschlüssel für eine Tabelle besteht.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|Gibt die Liste der Eingabe- und Ausgabeparameter sowie die Spalten zurück, aus denen das Resultset für die angegebenen Prozeduren besteht.|  
||['SQLProcedures'](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|Gibt die Liste der Prozedurnamen zurück, die in einer bestimmten Datenquelle gespeichert sind.|  
||['SQLSpecialColumns'](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Gruppe öffnen|Gibt Informationen über den optimalen Satz von Spalten zurück, der eine Zeile in einer angegebenen Tabelle eindeutig identifiziert, oder die Spalten, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird.|  
||['SQLStatistics'](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|Gibt Statistiken zu einer einzelnen Tabelle und die Liste der Der Tabelle zugeordneten Indizes zurück.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|Gibt eine Liste der Tabellen und die Berechtigungen zurück, die jeder Tabelle zugeordnet sind.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Gruppe öffnen|Gibt die Liste der Tabellennamen zurück, die in einer bestimmten Datenquelle gespeichert sind.|  
|Beenden einer Erklärung|['SQLFreeStmt'](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|Beendet die Anweisungsverarbeitung, verwirft ausstehende Ergebnisse und gibt optional alle Ressourcen frei, die dem Anweisungshandle zugeordnet sind.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|Schließt einen Cursor, der für ein Anweisungshandle geöffnet wurde.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|Bricht die Verarbeitung für eine Anweisung ab.|  
||[SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|Bricht die Verarbeitung für eine Anweisung oder Verbindung ab.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|Überträgt oder führt einen Rollback einer Transaktion durch.|  
|Beenden einer Verbindung|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|Schließen der Verbindung.<br /><br /> Gibt ein Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptor-Handle frei.|
