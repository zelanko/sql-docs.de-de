---
title: SQLEndTran-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLEndTran
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLEndTran
helpviewer_keywords:
- SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98a0f072af79c2c6e39d0cfc49e72cbeef1c2193
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68344769"
---
# <a name="sqlendtran-function"></a>SQLEndTran-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLEndTran** fordert einen Commit-oder Rollback-Vorgang für alle aktiven Vorgänge für alle Anweisungen an, die einer Verbindung zugeordnet sind. **SQLEndTran** kann auch anfordern, dass ein Commit-oder Rollback-Vorgang für alle Verbindungen durchgeführt wird, die einer Umgebung zugeordnet sind.  
  
> [!NOTE]  
>  Weitere Informationen dazu, wie der Treiber-Manager diese Funktion bei ODBC 3 zuordnet. die *x* -Anwendung arbeitet mit ODBC 2. *x* -Treiber finden Sie unter [Mapping Replace Functions for abwärts Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 Der Handle-Typbezeichner. Enthält entweder SQL_HANDLE_ENV (wenn *handle* ein Umgebungs Handle ist) oder SQL_HANDLE_DBC (wenn *handle* ein Verbindungs Handle ist).  
  
 *Bewältigen*  
 Der Das Handle des Typs, der durch den *Handlertyp*angegeben wird und den Bereich der Transaktion angibt. Weitere Informationen finden Sie unter "Kommentare".  
  
 *CompletionType*  
 Der Einer der folgenden beiden Werte:  
  
 SQL_COMMIT SQL_ROLLBACK  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLEndTran** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem entsprechenden *Handlertyp und handle*abgerufen werden. ** In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLEndTran** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) der *Handlertyp* wurde SQL_HANDLE_DBC, und das *handle* befand sich nicht in einem verbundenen Zustand.|  
|08007|Verbindungsfehler während der Transaktion.|Der *tortype* war SQL_HANDLE_DBC, und die dem *handle* zugeordnete Verbindung konnte während der Ausführung der Funktion nicht ermittelt werden, und es kann nicht bestimmt werden, ob der angeforderte **Commit** oder **Rollback** vor dem Fehler aufgetreten ist.|  
|25s01|Unbekannter Transaktionsstatus.|Mindestens eine der Verbindungen in *handle* konnte die Transaktion mit dem angegebenen Ergebnis nicht vervollständigen, und das Ergebnis ist unbekannt.|  
|25s02|Die Transaktion ist noch aktiv.|Der Treiber war nicht in der Lage, sicherzustellen, dass alle Arbeiten in der globalen Transaktion atomisch abgeschlossen werden konnten, und die Transaktion ist noch aktiv.|  
|25s03|Für Transaktion wird ein Rollback ausgeführt|Der Treiber war nicht in der Lage zu garantieren, dass alle Arbeiten in der globalen Transaktion atomarisch abgeschlossen werden konnten, und für alle Aufgaben in der Transaktion, die im *handle* aktiv war, wurde ein Rollback ausgeführt.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40002|Verletzung der Integritäts Einschränkung|Der *CompletionType* wurde SQL_COMMIT, und die Verpflichtung von Änderungen verursachte eine Verletzung der Integritäts Einschränkung. Folglich wurde für die Transaktion ein Rollback ausgeführt.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*szmessagetext* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *connectionHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung der [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) abgeschlossen wurde, wurde die Funktion " *connectionHandle*" aufgerufen. Anschließend wurde die Funktion für *connectionHandle*erneut aufgerufen.<br /><br /> Die-Funktion wurde aufgerufen, und vor der Ausführung von **sqlcancelhandle** wurde für *connectionHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für ein Anweisungs Handle aufgerufen, das dem *connectionHandle* zugeordnet ist und beim Aufrufen von **SQLEndTran** noch ausgeführt wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für *connectionHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für ein Anweisungs Handle aufgerufen, das dem *connectionHandle* zugeordnet ist, und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *handle* mit dem auf SQL_HANDLE_DBC festgelegten *andlertyp* aufgerufen und beim Aufrufen dieser Funktion noch ausgeführt.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungs Handles aufgerufen, die dem *handle* zugeordnet sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY012|Ungültiger Transaktions Vorgangs Code.|(DM) der für das Argument *CompletionType* angegebene Wert war weder SQL_COMMIT noch SQL_ROLLBACK.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY092|Ungültiger Attribut/Options Bezeichner|(DM) der für den *Argumenttyp* des Arguments angegebene Wert war weder SQL_HANDLE_ENV noch SQL_HANDLE_DBC.|  
|HY115|SQLEndTran ist für Umgebungen, die eine Verbindung mit aktivierter asynchroner Funktions Ausführung enthalten, nicht zulässig.|(DM)- *Handlertyp* kann nicht auf SQL_HANDLE_ENV festgelegt werden, wenn die asynchrone Ausführung von Verbindungsfunktionen für eine Verbindung in der Umgebung aktiviert ist.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie im Abschnitt "Kommentare" in diesem Thema.|  
|HYC00|Optionales Feature nicht implementiert|Der Treiber oder die Datenquelle unterstützt den **Rollback** -Vorgang nicht.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *connectionHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Für ODBC 3. *x* -Treiber: Wenn der *Handlertyp* SQL_HANDLE_ENV und *handle* ein gültiges Umgebungs Handle ist, ruft der Treiber-Manager **SQLEndTran** in jedem Treiber auf, der der Umgebung zugeordnet ist. Das *handle* -Argument für den-Treiber ist das Umgebungs Handle des Treibers. Für ODBC 2. *x* -Treiber: Wenn der *Handlertyp* SQL_HANDLE_ENV und *handle* ein gültiges Umgebungs Handle ist und mehrere Verbindungen in einem verbundenen Zustand in dieser Umgebung vorhanden sind, ruft der Treiber-Manager **SQLTransact** im Treiber einmal für jede Verbindung in einem verbundenen Zustand in dieser Umgebung auf. Das *handle* -Argument in jedem-Rückruf ist das Handle der Verbindung. In jedem Fall versucht der Treiber, einen Commit oder Rollback für Transaktionen auszuführen, abhängig vom Wert von *CompletionType*für alle Verbindungen, die sich in dieser Umgebung in einem verbundenen Zustand befinden. Nicht aktive Verbindungen wirken sich nicht auf die Transaktion aus.  
  
> [!NOTE]  
>  **SQLEndTran** kann nicht zum Commit oder Rollback von Transaktionen in einer freigegebenen Umgebung verwendet werden. SQLState HY092 (Ungültiger Attribut-/Optionsbezeichner) wird zurückgegeben, wenn **SQLEndTran** aufgerufen wird, wobei *handle* entweder auf das Handle einer freigegebenen Umgebung oder auf das Handle einer Verbindung in einer freigegebenen Umgebung festgelegt ist.  
  
 Der Treiber-Manager gibt SQL_SUCCESS nur dann zurück, wenn für jede Verbindung SQL_SUCCESS empfangen wird. Wenn der Treiber-Manager SQL_ERROR für eine oder mehrere Verbindungen empfängt, wird SQL_ERROR an die Anwendung zurückgegeben, und die Diagnoseinformationen werden in der Diagnosedaten Struktur der Umgebung abgelegt. Die Anwendung kann **SQLGetDiagRec** für jede Verbindung aufrufen, um zu bestimmen, welche Verbindung oder welche Verbindungen während des Commit-oder Rollback-Vorgangs fehlgeschlagen sind.  
  
> [!NOTE]  
>  Der Treiber-Manager simuliert keine globale Transaktion über alle Verbindungen und verwendet daher keine Zweiphasencommit-Protokolle.  
  
 Wenn *CompletionType* SQL_COMMIT ist, gibt **SQLEndTran** eine Commit-Anforderung für alle aktiven Vorgänge für jede Anweisung aus, die einer betroffenen Verbindung zugeordnet ist. Wenn *CompletionType* SQL_ROLLBACK ist, gibt **SQLEndTran** eine Rollback-Anforderung für alle aktiven Vorgänge für jede Anweisung aus, die einer betroffenen Verbindung zugeordnet ist. Wenn keine Transaktionen aktiv sind, gibt **SQLEndTran** SQL_SUCCESS ohne Auswirkung auf Datenquellen zurück. Weitere Informationen finden Sie unter [Commit und Rollback von Transaktionen](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md).  
  
 Wenn sich der Treiber im manuellen Commitmodus befindet (durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_AUTOCOMMIT-Attribut auf SQL_AUTOCOMMIT_OFF), wird eine neue Transaktion implizit gestartet, wenn eine SQL-Anweisung, die in einer Transaktion enthalten sein kann, für die aktuelle Datenquelle ausgeführt wird. Weitere Informationen finden Sie unter [Commit-Modus](../../../odbc/reference/develop-app/commit-mode.md).  
  
 Um zu ermitteln, wie sich Transaktions Vorgänge auf Cursor auswirken, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CURSOR_ROLLBACK_BEHAVIOR und SQL_CURSOR_COMMIT_BEHAVIOR auf. Weitere Informationen finden Sie in den folgenden Abschnitten und unter [Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
 Wenn die SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR Wert SQL_CB_DELETE entspricht, werden alle geöffneten Cursor für alle der Verbindung zugeordneten Anweisungen von **SQLEndTran** geschlossen und gelöscht. alle ausstehenden Ergebnisse werden verworfen. **SQLEndTran** verlässt jede Anweisung, die in einem zugeordneten (nicht vorbereiteten) Zustand vorhanden ist. die Anwendung kann Sie für nachfolgende SQL-Anforderungen wieder verwenden oder **SQLFreeStmt** oder **SQLFreeHandle** mit dem *Typ* "SQL_HANDLE_STMT" zum deren zuweisen aufzurufen.  
  
 Wenn die SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR Wert SQL_CB_CLOSE entspricht, schließt **SQLEndTran** alle geöffneten Cursor für alle Anweisungen, die der Verbindung zugeordnet sind. **SQLEndTran** verlässt jede Anweisung, die in einem vorbereiteten Zustand vorhanden ist. die Anwendung kann für eine Anweisung, die der Verbindung zugeordnet ist, **SQLExecute** aufrufen, ohne zuerst **SQLPrepare**aufzurufen.  
  
 Wenn die SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR Wert SQL_CB_PRESERVE entspricht, wirkt sich **SQLEndTran** nicht auf geöffnete Cursor aus, die der Verbindung zugeordnet sind. Cursor verbleiben in der Zeile, auf die Sie vor dem **SQLEndTran**-Befehl verwiesen haben.  
  
 Für Treiber und Datenquellen, die Transaktionen unterstützen, gibt der Aufruf von **SQLEndTran** mit SQL_COMMIT oder SQL_ROLLBACK, wenn keine Transaktion aktiv ist, SQL_SUCCESS zurück (gibt an, dass kein Commit oder Rollback ausgeführt werden kann) und hat keine Auswirkung auf die Datenquelle.  
  
 Wenn sich ein Treiber im Autocommit-Modus befindet, ruft der Treiber-Manager **SQLEndTran** nicht im Treiber auf. **SQLEndTran** gibt immer SQL_SUCCESS zurück, unabhängig davon, ob es mit einem *CompletionType* SQL_COMMIT oder SQL_ROLLBACK aufgerufen wird.  
  
 Treiber oder Datenquellen, die keine Transaktionen unterstützen (**SQLGetInfo** - *Option* SQL_TXN_CAPABLE ist SQL_TC_NONE), befinden sich praktisch immer im Autocommitmodus und geben daher immer SQL_SUCCESS für **SQLEndTran** zurück, unabhängig davon, ob Sie mit einem *CompletionType* SQL_COMMIT oder SQL_ROLLBACK aufgerufen werden. Bei solchen Treibern und Datenquellen wird ein Rollback für Transaktionen nicht ausgeführt, wenn dies angefordert wird.  
  
## <a name="suspended-state"></a>Angehaltene Status  
 In Treiber-Managern, die vor Windows 7 veröffentlicht wurden, war eine Transaktion aktiv, wenn **SQLEndTran** vom Treiber SQL_ERROR zurückgegeben wurde. Es war jedoch möglich, dass für die Transaktion erfolgreich ein Commit auf dem Server ausgeführt wurde, der Treiber auf dem Client jedoch nicht benachrichtigt wurde (z. b. weil ein Netzwerkfehler aufgetreten ist). Dadurch wird die Verbindung in einem fehlerhaften Zustand belassen. Beginnend mit Windows 7, wenn **SQLEndTran** SQL_ERROR zurückgibt, befindet sich die Verbindung möglicherweise im angehaltenen Zustand. Im angehaltenen Zustand ist es möglich, schreibgeschützte Funktionen aufzurufen. Schließlich sollte die Anwendung **SQLDisconnect** bei einer angehaltenen Verbindung zum Freigeben von Ressourcen abrufen.  
  
 Wenn alle der folgenden Bedingungen zutreffen, wird die Verbindung in den Status "angehalten" versetzt:  
  
-   Der Treiber gibt SQL_ERROR aus **SQLEndTran**zurück.  
  
-   Der Treiber ist ODBC, Version 3,8 oder höher.  
  
-   Die Anwendungs Version ist 3,8 oder höher. oder die neu kompilierte ODBC 2. x-oder 3. x-Anwendung bricht die **SQLEndTran** -Funktion erfolgreich über **sqlcancelhandle**ab.  
  
-   Der Treiber hat eine der folgenden Meldungen nicht zurückgegeben, die bestätigen, dass die Transaktion nicht abgeschlossen wurde:  
  
    -   25s03: für die Transaktion wird ein Rollback ausgeführt  
  
    -   40001: Serialisierungsfehler  
  
    -   40002: Integritäts Einschränkung  
  
    -   HYC00: optionales Feature nicht implementiert  
  
 Wenn **SQLEndTran** für ein Umgebungs Handle aufgerufen wurde und eine der Verbindungen die oben genannten Bedingungen erfüllt, werden alle Verbindungen, die eine Verbindung mit dem gleichen Treiber herstellen, in den Zustand "angehalten" versetzt.  
  
 Nachdem eine Anwendung **SQLDisconnect** bei einer angehaltenen Verbindung aufgerufen hat, kann die Verbindung zum erneuten Herstellen der Verbindung mit einer anderen Datenquelle oder derselben Datenquelle verwendet werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen einer Funktion, die asynchron auf einem Verbindungs Handle ausgeführt wird.|[SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Zurückgeben von Informationen zu einem Treiber oder einer Datenquelle|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Freigeben eines Handles|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Freigeben eines Anweisungs Handles|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
