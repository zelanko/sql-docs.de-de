---
title: Core-Level-API-Funktionen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: c2e77ffd4fe892bc2f3d9a944c79d6b702d5e671
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66354586"
---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>API-Funktionen der Kernebene (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Funktionen, die auf dieser Ebene umfassen die Mindestebene von schnittstellenübereinstimmung für ODBC-Treiber.  
  
|API-Funktion|Hinweise|  
|------------------|-----------|  
|**SQLAllocConnect**|Belegt Speicher für ein Verbindungshandle *Hdbc*, in der Umgebung identifizierte *Henv*. Der Treiber-Manager verarbeitet diesen Aufruf und Aufrufe des Treibers **SQLAllocConnect** Funktion jedes Mal, wenn **SQLConnect**, **SQLBrowseConnect**, oder  **SQLDriverConnect** aufgerufen wird.|  
|**SQLAllocEnv**|Zeigt ein Dialogfeld, das die Anforderung für die Oracle-Clientsoftware angeben, und gibt dann SQL_NULL_HANDLE zurück. Wenn die Oracle-Clientsoftware nicht installiert ist, diese Funktion weist Speicher für ein Umgebungshandle *Henv*, und der ODBC-Aufruf-Level-Schnittstelle für die Verwendung von einer Anwendung initialisiert.|  
|**SQLAllocStmt**|Belegt Speicher für ein Anweisungshandle, und ordnet das Anweisungshandle von Hdbc angegebene Verbindung. Der Treiber-Manager übergibt diesen Aufruf an den Treiber, der den Speicher für die Struktur des Befehls beschäftigt reserviert.|  
|**SQLBindCol**|Speicherplatz für eine Ergebnisspalte zugewiesen und gibt den Typ des Ergebnisses.|  
|**SQLCancel**|Bricht die Verarbeitung für ein Anweisungshandle Befehls beschäftigt ab. In einigen Fällen lässt Oracle nicht Abbrechen einer ausgeführten Anweisung. Dies bedeutet, dass eine ausgeführte Anweisung weiterhin Oracle Abschluss des Prozesses, zu diesem Zeitpunkt die Ergebnisse von den Anweisungen, die vom ODBC-Treiber für Oracle abgebrochen werden.|  
|**SQLColAttributes**|Gibt Informationen der Sicherheitsbeschreibung für eine Spalte in einem Resultset zurück. Informationen der Sicherheitsbeschreibung wird als eine Zeichenfolge, eine 32-Bit-Deskriptor-abhängige Wert oder ein ganzzahliger Wert zurückgegeben.|  
|**SQLConnect**|Eine Verbindung mit einer Datenquelle. Um Oracle-Operating System-Authentifizierung verwenden, geben Sie "/" als die *SzUID* Parameter und "" als die *SzAuthStr* Parameter.|  
|**SQLDescribeCol**|Gibt den Namen, Typ, Genauigkeit, Dezimalstellen und NULL-Zulässigkeit der angegebenen Ergebnisspalte. **Hinweis:  SQLDescribeCol** meldet berechnete Spalten als SQL_VARCHAR.|  
|**SQLDisconnect**|Schließt eine Verbindung Wenn Verbindungspooling, für die einer freigegebenen Umgebung aktiviert ist aus, und eine Anwendung ruft **SQLDisconnect** für eine Verbindung in der Umgebung, die Verbindung an den Verbindungspool zurückgegeben werden soll, und ist weiterhin verfügbar, mit anderen Komponenten, die mithilfe von die gleichen freigegebenen Umgebung.|  
|**SQLError**|Fehler oder Status Informationen zu den letzten Fehler zurückgegeben. Der Treiber verwaltet einen Stapel oder eine Liste von Fehlern, die für die zurückgegeben werden, können die *Befehls beschäftigt*, *Hdbc*, und *Henv* Argumente, je nachdem, wie der Aufruf von **SQLError**  erfolgt. Die Fehlerwarteschlange wird nach jeder Anweisung geleert. In der Regel ruft Sie eine Oracle-Fehlermeldung ab, und andernfalls leer ist.|  
|**SQLExecDirect**|Führt eine neue, nicht vorbereiteter SQL­Anweisung. Der Treiber verwendet die aktuellen Werte der Variablen Marker Parameter auf, wenn alle Parameter in der Anweisung vorhanden sind. Wenn Ihre Tabelle, Sicht oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen wieder in Anführungszeichen ein. Wenn Ihre Datenbank eine Tabelle namens enthält z. B. *Meine Tabelle* und das Feld *mein Feld*, schließen Sie jedes Element des Bezeichners wie folgt:<br /><br /> Wählen Sie \`meiner Tabelle\`. \`My Field1\`,; \`My Table\`.\`My Field2\` FROM \`My Table\`|  
|**SQLExecute**|Führt eine vorbereitete SQL­Anweisung (eine Anweisung, die bereits vorbereitet, indem **SQLPrepare**). Der Treiber verwendet die aktuellen Werte der Variablen Marker Parameter auf, wenn alle Parameter in der Anweisung vorhanden sind.|  
|**SQLFetch**|Ruft eine Zeile aus einem Resultset in die Speicherorte, die durch den vorherigen Aufrufen zum angegebenen **SQLBindCol**. Bereitet den Treiber für einen Aufruf von **SQLGetData** für ungebundenen Spalten.|  
|**SQLFreeConnect**|Gibt ein Verbindungshandle frei und gibt alle für das Handle zugeordneten Arbeitsspeicher frei.|  
|**SQLFreeEnv**|Schließt den ODBC-Treiber für Oracle und alle mit der Treiber verbundene Speicher frei.|  
|**SQLFreeStmt**|Beendet die Verarbeitung im Zusammenhang mit einer bestimmten Befehls beschäftigt, schließt alle geöffneten Cursor verknüpft ist, mit der Befehls beschäftigt, ausstehende Ergebnisse verworfen und gibt optional das Anweisungshandle zugeordnete Ressourcen frei.|  
|**SQLGetCursorName**|Gibt den Namen des Cursors Zusammenhang mit der angegebenen Befehls beschäftigt.|  
|**SQLNumResultCols**|Gibt die Anzahl der Spalten in ein resultsetcursor zurück.|  
|**SQLPrepare**|Bereitet eine SQL-Anweisung durch die Planung So optimieren, und führen Sie die Anweisung vor. Die SQL-Anweisung kompiliert wird, für die Ausführung von **SQLExecDirect**.<br /><br /> Wenn Ihre Tabelle, Sicht oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen wieder in Anführungszeichen ein. Wenn Ihre Datenbank eine Tabelle namens enthält z. B. *Meine Tabelle* und das Feld *mein Feld*, schließen Sie jedes Element des Bezeichners wie folgt:<br /><br /> Wählen Sie \`meiner Tabelle\`.\` Mein Feld\` FROM \`meiner Tabelle\`<br /><br /> Weitere Informationen zur Verwendung von Resultsets, die Arrays als formale Parameter enthält, finden Sie unter [Zurückgeben von Arrayparametern aus gespeicherten Prozeduren](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLRowCount**|Oracle bietet keine Möglichkeit zum Bestimmen der Anzahl von Zeilen in einem Resultset erst, nachdem Sie die letzte Zeile abrufen, sodass es-1 zurück.|  
|**SQLSetCursorName**|Ein Handle aktive Anweisung ordnet einen Cursornamen *Befehls beschäftigt*.|  
|**SQLSetParam**|Ersetzt durch SQLBindParameter in ODBC 2. *x*.|  
|**SQLTransact**|Fordert einen Commit oder Rollback-Vorgang für alle aktiven Vorgänge für alle Anweisungshandles (Hstmts), der eine Verbindung zugeordnet oder für alle Verbindungen, die das Umgebungshandle zugeordnet *Henv*. Die Transaktion bleibt aktiv, wenn ein Commit im manuellen Modus fehlschlägt, Sie können auch ein Rollback der Transaktion oder wiederholen den Commitvorgang. Wenn ein Commitvorgang im Transaktionsmodus für automatische fehlschlägt, wird die Transaktion automatisch zurückgesetzt; die Transaktion darf nicht inaktiv sein.|
