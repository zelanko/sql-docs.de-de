---
title: API-Funktionen der Kernebene (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cc95ec17dc221cb77bd94fc3378af483aeee92dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081971"
---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der Kernebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Zu den Funktionen auf dieser Ebene gehören die minimale Ebene der Schnittstellen Konformität für ODBC-Treiber.  
  
|API-Funktion|Notizen|  
|------------------|-----------|  
|**SQLAllocConnect**|Belegt Speicher für ein Verbindungs Handle, *hdbc*, in der durch *HENV*identifizierten Umgebung. Der Treiber-Manager verarbeitet diesen Aufruf und ruft die **sqlverbincconnect** -Funktion des Treibers immer dann auf, wenn **SQLCONNECT**, **sqlbrowseconnetct**oder **SQLDriverConnect** aufgerufen wird.|  
|**SQLAllocEnv**|Zeigt ein Dialogfeld an, in dem die Anforderung der Oracle-Client Software angegeben ist, und gibt SQL_NULL_HANDLE zurück. Wenn die Oracle-Client Software nicht installiert ist, ordnet diese Funktion Arbeitsspeicher für ein Umgebungs Handle, *HENV*, zu und initialisiert die ODBC-Schnittstelle auf Aufrufebene für die Verwendung durch eine Anwendung.|  
|**SQLAllocStmt**|Ordnet Speicher für ein Anweisungs Handle zu und ordnet das Anweisungs Handle der von hdbc angegebenen Verbindung zu. Der Treiber-Manager übergibt diesen Befehl an den Treiber, der den Arbeitsspeicher für die hstmt-Struktur zugeordnet.|  
|**SQLBindCol**|Weist Speicherplatz für eine Ergebnisspalte zu und gibt den Typ des Ergebnisses an.|  
|**SQLCancel**|Bricht die Verarbeitung für ein Anweisungs Handle (hstmt) ab. In einigen Fällen lässt Oracle den Abbruch einer laufenden Anweisung nicht zu. Dies bedeutet, dass eine laufende Anweisung fortgesetzt wird, bis Oracle den Prozess abschließt. zu diesem Zeitpunkt werden die Ergebnisse der Anweisungen vom ODBC-Treiber für Oracle abgebrochen.|  
|**SQLColAttributes**|Gibt Deskriptorinformationen für eine Spalte in einem Resultset zurück. Deskriptorinformationen werden als Zeichenfolge, als 32-Bit-deskriptorabhängige Werte oder als ganzzahliger Wert zurückgegeben.|  
|**SQLConnect**|Stellt eine Verbindung mit einer Datenquelle her. Um die Oracle-Betriebs System Authentifizierung zu verwenden, geben Sie "/" als *szuid* -Parameter und "" als *szauthstr* -Parameter an.|  
|**SQLDescribeCol**|Gibt den Namen, den Typ, die Genauigkeit, die Dezimal Größe und die NULL-Zulässigkeit der angegebenen Ergebnisspalte zurück. **Hinweis: SQLDescribeCol** meldet berechnete Spalten als SQL_VARCHAR.|  
|**SQLDisconnect**|Schließt eine Verbindung Wenn das Verbindungspooling für eine freigegebene Umgebung aktiviert ist und eine Anwendung **SQLDisconnect** für eine Verbindung in dieser Umgebung aufruft, wird die Verbindung an den Verbindungspool zurückgegeben und ist weiterhin für andere Komponenten verfügbar, die dieselbe freigegebene Umgebung verwenden.|  
|**SQLError**|Gibt Fehler-oder Statusinformationen zum letzten Fehler zurück. Der Treiber verwaltet einen Stapel oder eine Liste von Fehlern, die für die Argumente *hstmt*, *hdbc*und *HENV* zurückgegeben werden können. Dies hängt davon ab, wie der **SQLError** -Befehl durchgeführt wird. Die Fehler Warteschlange wird nach jeder Anweisung geleert. Ruft in der Regel eine Oracle-Fehlermeldung ab, die andernfalls leer ist.|  
|**SQLExecDirect**|Führt eine neue, nicht vorbereitete SQL-Anweisung aus. Der Treiber verwendet die aktuellen Werte der parametermarkervariablen, wenn in der Anweisung Parameter vorhanden sind. Wenn Ihre Tabellen-, Ansichts-oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen in die rückanführungs Zeichen ein. Wenn Ihre Datenbank z. b. eine Tabelle mit dem Namen " *My Table* " und das Feld " *My*" enthält, schließen Sie jedes Element des Bezeichners wie folgt ein:<br /><br /> Wählen \`Sie meine\`Tabelle aus. \`Meine field1\`,; \`Meine Tabelle\`. \`Meine field2\` aus \`meiner Tabelle\`|  
|**SQLExecute**|Führt eine vorbereitete SQL-Anweisung aus (eine bereits von **SQLPrepare**vorbereitete-Anweisung). Der Treiber verwendet die aktuellen Werte der parametermarkervariablen, wenn in der Anweisung Parameter vorhanden sind.|  
|**SQLFetch**|Ruft eine Zeile aus einem Resultset in die Speicherorte ab, die von den vorherigen Aufrufen von **SQLBindCol**angegeben wurden. Bereitet den Treiber für einen **SQLGetData** -aufrufswert für die ungebundenen Spalten vor.|  
|**SQLFreeConnect**|Gibt ein Verbindungs Handle frei und gibt den für das Handle zugeordneten Arbeitsspeicher frei.|  
|**SQLFreeEnv**|Schließt den ODBC-Treiber für Oracle und gibt den dem Treiber zugeordneten Arbeitsspeicher frei.|  
|**'SQLFreeStmt'**|Beendet die Verarbeitung eines bestimmten hstmt, schließt alle geöffneten Cursor, die dem hstmt zugeordnet sind, verwirft ausstehende Ergebnisse und gibt optional alle dem Anweisungs Handle zugeordneten Ressourcen frei.|  
|**SQLGetCursorName**|Gibt den Namen des Cursors zurück, der dem angegebenen hstmt zugeordnet ist.|  
|**SQLNumResultCols**|Gibt die Anzahl der Spalten in einem resultsetcursor zurück.|  
|**SQLPrepare**|Bereitet eine SQL-Anweisung vor, indem geplant wird, wie die-Anweisung optimiert und ausgeführt wird. Die SQL-Anweisung wird für die Ausführung von **SQLExecDirect**kompiliert.<br /><br /> Wenn Ihre Tabellen-, Ansichts-oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen in die rückanführungs Zeichen ein. Wenn Ihre Datenbank z. b. eine Tabelle mit dem Namen " *My Table* " und das Feld " *My*" enthält, schließen Sie jedes Element des Bezeichners wie folgt ein:<br /><br /> Wählen \`Sie meine\`Tabelle aus. \`Mein Feld\` aus \`meiner Tabelle\`<br /><br /> Informationen zur Verwendung von Resultsets mit Arrays als formale Parameter finden Sie unter [zurückgeben von Array Parametern aus gespeicherten Prozeduren](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLRowCount**|Oracle bietet keine Möglichkeit, die Anzahl der Zeilen in einem Resultset zu ermitteln, bis Sie die letzte Zeile abgerufen haben. Daher wird-1 zurückgegeben.|  
|**SQLSetCursorName**|Ordnet einem aktiven Anweisungs Handle ( *hstmt*) einen Cursor Namen zu.|  
|**SQLSetParam**|Ersetzt durch SQLBindParameter in ODBC 2. *x*.|  
|**SQLtransact**|Fordert einen Commit-oder Rollback-Vorgang für alle aktiven Vorgänge für alle Anweisungs Handles (hstmts) an, die einer Verbindung zugeordnet sind, oder für alle Verbindungen, die dem Umgebungs Handle, *HENV*, zugeordnet sind. Wenn ein Commit im manuellen Modus fehlschlägt, bleibt die Transaktion aktiv. Sie können für die Transaktion ein Rollback ausführen oder den Commit-Vorgang wiederholen. Wenn ein Commitvorgang im automatischen Transaktionsmodus fehlschlägt, wird für die Transaktion automatisch ein Rollback ausgeführt. die Transaktion kann nicht inaktiv sein.|
