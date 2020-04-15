---
title: Core Level API-Funktionen (ODBC-Treiber für Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- core level API functions [ODBC]
- ODBC core level API functions [ODBC]
ms.assetid: 8596eed7-bda6-4cac-ae1f-efde1aab785f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19751bb6d0556b117d0a73967d4db00c408733ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281020"
---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der Kernebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Funktionen auf dieser Ebene umfassen die minimale Schnittstellenkonformität für ODBC-Treiber.  
  
|API-Funktion|Notizen|  
|------------------|-----------|  
|**SQLAllocConnect**|Ordnet Speicher für ein Verbindungshandle *hdbc*in der von *henv*identifizierten Umgebung zu. Der Treiber-Manager verarbeitet diesen Aufruf und ruft die **SQLAllocConnect-Funktion** des Treibers auf, wenn **SQLConnect**, **SQLBrowseConnect**oder **SQLDriverConnect** aufgerufen wird.|  
|**SQLAllocEnv**|Zeigt ein Dialogfeld an, in dem die Anforderung für Oracle Client-Software angegeben wird, und gibt dann SQL_NULL_HANDLE zurück. Wenn die Oracle Client-Software nicht installiert ist, weist diese Funktion Speicher für ein Umgebungshandle, *henv,* und initialisiert die ODBC-Schnittstelle auf Aufrufebene für die Verwendung durch eine Anwendung.|  
|**SQLAllocStmt**|Ordnet Speicher für ein Anweisungshandle zu und ordnet das Anweisungshandle der von hdbc angegebenen Verbindung zu. Der Treiber-Manager übergibt diesen Aufruf an den Treiber, der den Speicher für die hstmt-Struktur reserviert.|  
|**SQLBindCol**|Weist Speicherplatz für eine Ergebnisspalte zu und gibt den Typ des Ergebnisses an.|  
|**SQLCancel**|Bricht die Verarbeitung für ein Anweisungshandle, hstmt ab. In einigen Fällen lässt Oracle keine Stornierung einer ausgeführten Anweisung zu. Dies bedeutet, dass eine ausgeführte Anweisung so lange fortgesetzt wird, bis Oracle den Prozess abgeschlossen hat.|  
|**SQLColAttributes**|Gibt Deskriptorinformationen für eine Spalte in einem Resultset zurück. Deskriptorinformationen werden als Zeichenfolge, als 32-Bit-Deskriptor-abhängiger Wert oder als Ganzzahlwert zurückgegeben.|  
|**SQLConnect**|Stellt eine Verbindung zu einer Datenquelle her. Um die Oracle Operating System Authentication zu verwenden, geben Sie "/" als *szUID-Parameter* und "" als *szAuthStr-Parameter* an.|  
|**SQLDescribeCol**|Gibt den Namen, den Typ, die Genauigkeit, den Maßstab und die NULL-Fähigkeit der angegebenen Ergebnisspalte zurück. **Hinweis: SQLDescribeCol** meldet berechnete Spalten als SQL_VARCHAR.|  
|**SQLDisconnect**|Schließt eine Verbindung Wenn das Verbindungspooling für eine freigegebene Umgebung aktiviert ist und eine Anwendung **SQLDisconnect** für eine Verbindung in dieser Umgebung aufruft, wird die Verbindung an den Verbindungspool zurückgegeben und ist weiterhin für andere Komponenten verfügbar, die dieselbe freigegebene Umgebung verwenden.|  
|**Sqlerror**|Gibt Fehler- oder Statusinformationen zum letzten Fehler zurück. Der Treiber verwaltet einen Stapel oder eine Liste von Fehlern, die für die Argumente *hstmt*, *hdbc*und *henv* zurückgegeben werden können, je nachdem, wie der Aufruf von **SQLError** erfolgt. Die Fehlerwarteschlange wird nach jeder Anweisung geleert. Ruft in der Regel eine Oracle-Fehlermeldung ab und ist ansonsten leer.|  
|**SQLExecDirect**|Führt eine neue, unvorbereitete SQL-Anweisung aus. Der Treiber verwendet die aktuellen Werte der Parametermarkervariablen, wenn Parameter in der Anweisung vorhanden sind. Wenn Ihre Tabellen-, Ansichts- oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen in hintere Anführungszeichen ein. Wenn Ihre Datenbank z. B. eine Tabelle mit dem Namen *Meine Tabelle* und das Feld *"Mein Feld"* enthält, schließen Sie jedes Element des Bezeichners wie folgt ein:<br /><br /> SELECT \`Meine\`Tabelle . \`Mein Feld1\`,; \`Mein\`Tisch . \`Mein\` Feld2 \`VON meinem Tisch\`|  
|**SQLExecute**|Führt eine vorbereitete SQL-Anweisung aus (eine Anweisung, die bereits von **SQLPrepare**vorbereitet wurde). Der Treiber verwendet die aktuellen Werte der Parametermarkervariablen, wenn Parameter in der Anweisung vorhanden sind.|  
|**SQLFetch**|Ruft eine Zeile aus einem Resultset in die Speicherorte ab, die durch die vorherigen Aufrufe von **SQLBindCol**angegeben wurden. Bereitet den Treiber für einen Aufruf von **SQLGetData** für die ungebundenen Spalten vor.|  
|**SQLFreeConnect**|Gibt ein Verbindungshandle frei und gibt den gesamten für das Handle reservierten Speicher frei.|  
|**SQLFreeEnv**|Schließt den ODBC-Treiber für Oracle und gibt den gesamten Speicher frei, der dem Treiber zugeordnet ist.|  
|**'SQLFreeStmt'**|Beendet die Verarbeitung, die einem bestimmten hstmt zugeordnet ist, schließt alle geöffneten Cursor, die dem hstmt zugeordnet sind, verwirft ausstehende Ergebnisse und gibt optional alle Ressourcen frei, die dem Anweisungshandle zugeordnet sind.|  
|**SQLGetCursorName**|Gibt den Namen des Cursors zurück, der dem angegebenen hstmt zugeordnet ist.|  
|**SQLNumResultCols**|Gibt die Anzahl der Spalten in einem Resultsetcursor zurück.|  
|**SQLPrepare**|Bereitet eine SQL-Anweisung vor, indem geplant wird, wie die Anweisung optimiert und ausgeführt wird. Die SQL-Anweisung wird für die Ausführung durch **SQLExecDirect**kompiliert.<br /><br /> Wenn Ihre Tabellen-, Ansichts- oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen in hintere Anführungszeichen ein. Wenn Ihre Datenbank beispielsweise eine Tabelle mit dem Namen *Meine Tabelle* und das Feld *"Mein Feld"* enthält, schließen Sie jedes Element des Bezeichners wie folgt ein:<br /><br /> SELECT \`Meine\`Tabelle . \`Mein\` Feld \`VON meinem Tisch\`<br /><br /> Informationen zur Verwendung von Resultsets, die Arrays als formale Parameter enthalten, finden Sie unter [Zurückgeben von Arrayparametern aus gespeicherten Prozeduren](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLRowCount**|Oracle bietet erst nach dem Abrufen der letzten Zeile eine Möglichkeit, die Anzahl der Zeilen in einem Resultset zu bestimmen.|  
|**SQLSetCursorName**|Ordnet einen Cursornamen einem aktiven Anweisungshandle *zu, hstmt*.|  
|**SQLSetParam**|Ersetzt durch SQLBindParameter in ODBC 2. *x*.|  
|**SQLTransact**|Fordert einen Commit- oder Rollbackvorgang für alle aktiven Vorgänge für alle Anweisungshandles (hstmts) an, die einer Verbindung zugeordnet sind, oder für alle Verbindungen, die mit dem Umgebungshandle, *henv*, verknüpft sind. Wenn ein Commit im manuellen Modus fehlschlägt, bleibt die Transaktion aktiv. Sie können einen Rollback für die Transaktion oder einen erneuten Vorgang des Commits auswählen. Wenn ein Commit-Vorgang im automatischen Transaktionsmodus fehlschlägt, wird ein automatischer Rollback für die Transaktion ausgeführt. Die Transaktion kann nicht inaktiv sein.|
