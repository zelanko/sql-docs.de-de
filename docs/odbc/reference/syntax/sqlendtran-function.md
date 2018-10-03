---
title: SQLEndTran-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLEndTran
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLEndTran
helpviewer_keywords:
- SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59199461d6a0d827cad043f0b6bdbe35d425815f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855918"
---
# <a name="sqlendtran-function"></a>SQLEndTran-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC 3.0 Standardkompatibilität: ISO-92  
  
 **Zusammenfassung**  
 **SQLEndTran** fordert eine Commit- oder Rollback für alle aktiven Vorgänge für alle Anweisungen, die mit einer Verbindung verknüpft sind. **SQLEndTran** können auch anfordern, dass ein Commit oder Rollback-Vorgang ausgeführt werden, für alle Verbindungen, die einer Umgebung zugewiesen sind.  
  
> [!NOTE]  
>  Weitere Informationen über welche des Treiber-Managers ordnet diese Funktion zu, wenn eine ODBC-3. *x* Anwendung arbeitet mit einer ODBC 2. *X* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für Abwärtskompatibilität-Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Typ-ID zu behandeln. Enthält entweder SQL_HANDLE_ENV auf (Wenn *behandeln* ist ein Umgebungshandle) oder SQL_HANDLE_DBC auf (Wenn *behandeln* ist ein Verbindungshandle).  
  
 *Handle*  
 [Eingabe] Das Handle, das vom angegebenen Typ *HandleType*, der angibt, der des Bereichs der Transaktion. Weitere Informationen finden Sie unter "Kommentare".  
  
 *' CompletionType '*  
 [Eingabe] Eine der beiden folgenden Werte:  
  
 SQL_COMMIT-OPTION SQL_ROLLBACK  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLEndTran** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit dem entsprechenden *HandleType*und *behandeln*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLEndTran** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) die *HandleType* wurde SQL_HANDLE_DBC auf, und die *behandeln* war nicht verbunden.|  
|08007|Verbindungsfehler während der Transaktion|Die *HandleType* SQL_HANDLE_DBC auf wurde und die Verbindung zugeordnet ist die *behandeln* Fehler während der Ausführung der Funktion, und kann nicht bestimmt, ob die angeforderte  **COMMIT** oder **ROLLBACK** vor dem Fehler aufgetreten ist.|  
|25S01|Transaktionsstatus unbekannt|Eine oder mehrere Verbindungen im *behandeln* Fehler bei der Transaktion mit dem angegebenen Ergebnis abgeschlossen wird, und das Ergebnis ist unbekannt.|  
|25S02|Transaktion ist noch aktiv|Der Treiber konnte nicht aus, um sicherzustellen, dass alle Arbeiten in der globalen Transaktion automatisch abgeschlossen werden konnte, und die Transaktion noch aktiv ist.|  
|25S03|Transaktion wird ein Rollback ausgeführt.|Der Treiber konnte nicht garantieren, dass alle Arbeiten in der globalen Transaktion automatisch abgeschlossen werden konnte, und alle in der Transaktion, die in aktiv arbeiten *behandeln* zurückgesetzt wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40002|Verletzung der integritätseinschränkung|Die *' CompletionType '* sql_commit-Option wurde und dem Commit der Änderungen verursacht Verletzung der integritätseinschränkung. Daher wurde die Transaktion ein Rollback ausgeführt.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*SzMessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *ConnectionHandle*. Die Funktion aufgerufen wurde und bevor sie die Ausführung beendet [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) aufgerufen wurde, auf die *ConnectionHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *ConnectionHandle*.<br /><br /> Die Funktion aufgerufen wurde und bevor sie die Ausführung beendet **SQLCancelHandle** aufgerufen wurde, auf die *ConnectionHandle* von einem anderen Thread in einer multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) für ein Anweisungshandle zugeordnet wurde eine asynchrone Funktion aufgerufen der *ConnectionHandle* und wurde noch ausgeführt, wenn **SQLEndTran** aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *ConnectionHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** aufgerufen wurde, für ein Anweisungshandle zugeordneten der *ConnectionHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *behandeln* mit *HandleType* auf SQL_HANDLE_DBC festgelegt wird, und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, für eine von der zugeordneten Anweisungshandles *behandeln* und zurückgegebene SQL_PARAM_DATA_AVAILABLE. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY012|Ungültiger Transaktionsvorgangscode|(DM) der Wert für das Argument angegebene *' CompletionType '* wurde weder SQL_COMMIT oder SQL_ROLLBACK.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) der Wert für das Argument angegebene *HandleType* war weder SQL_HANDLE_ENV noch SQL_HANDLE_DBC auf.|  
|HY115|SQLEndTran ist für eine Umgebung, die eine Verbindung mit der asynchronen Ausführung aktiviert enthält, nicht zulässig|(DM) *HandleType* kann nicht auf SQL_HANDLE_ENV festgelegt werden, wenn die asynchrone Ausführung der Verbindungsfunktionen für eine Verbindung in der Umgebung aktiviert ist.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, in den Abschnitt "Kommentare" dieses Themas.|  
|HYC00|Optionales Feature nicht implementiert.|Die Treiber oder die Datenquelle unterstützt nicht die **ROLLBACK** Vorgang.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *ConnectionHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 Für eine ODBC-3. *x* -Treiber verwenden, wenn *HandleType* ist SQL_HANDLE_ENV und *behandeln* ist der Treiber-Manager aufrufen, wird ein Handle gültige Umgebung **SQLEndTran**in einzelnen Treiber, die der Umgebung zugeordnet. Die *behandeln* Argument für den Aufruf eines Treibers werden Umgebungshandle des Treibers. Für eine ODBC-2. *x* -Treiber verwenden, wenn *HandleType* ist SQL_HANDLE_ENV und *behandeln* ist ein Handle gültige Umgebung, und es gibt mehrere Verbindungen in einem verbundenen Zustand in dieser Umgebung der Treiber-Manager aufrufen wird **SQLTransact** im Treiber einmal für jede Verbindung in einem verbundenen Zustand in der Umgebung. Die *behandeln* Argument bei jedem Aufruf werden ein Handle für die Verbindung. In beiden Fällen versucht, einen commit oder Rollback für Transaktionen, abhängig vom Wert der Treiber *' CompletionType '*, für alle Verbindungen, die für diese Umgebung verbunden sind. Verbindungen, die nicht aktiv sind wirken sich nicht auf die Transaktion aus.  
  
> [!NOTE]  
>  **SQLEndTran** kann nicht verwendet werden, um einen commit oder Rollback für Transaktionen aus, auf einer freigegebenen Umgebung. SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) wird zurückgegeben, wenn **SQLEndTran** aufgerufen wird und *behandeln* legen Sie entweder das Handle einer freigegebenen Umgebung oder das Handle für eine Verbindung auf eine freigegebene Umgebung.  
  
 Der Treiber-Manager gibt SQL_SUCCESS zurück, nur dann, wenn sie für jede Verbindung SQL_SUCCESS empfängt. Wenn der Treiber-Manager SQL_ERROR auf eine oder mehrere Verbindungen empfängt, wird SQL_ERROR zurückgegeben, für die Anwendung, und die Diagnoseinformationen befindet sich in der Struktur diagnostische Daten der Umgebung. Um zu bestimmen, welche Verbindung oder Verbindungen während der Commit- oder Rollback-Vorgang ist fehlgeschlagen, die Anwendung aufrufen kann **SQLGetDiagRec** für jede Verbindung.  
  
> [!NOTE]  
>  Der Treiber-Manager eine globale Transaktion wird nicht in allen Programmen simuliert und daher nicht Zweiphasen-Commit-Protokolle verwendet.  
  
 Wenn *' CompletionType '* ist der sql_commit-Option, **SQLEndTran** gibt die Anforderung für ein Commit für alle aktiven Vorgänge für jede Anweisung mit einer betroffenen Verbindung verknüpft sind. Wenn *' CompletionType '* ist SQL_ROLLBACK, **SQLEndTran** gibt eine rollbackanforderung für alle aktiven Vorgänge für jede Anweisung mit einer betroffenen Verbindung verknüpft sind. Wenn es aktiv ist, keine Transaktionen sind **SQLEndTran** gibt SQL_SUCCESS zurück, ohne Auswirkungen auf alle Datenquellen. Weitere Informationen finden Sie unter [Committing und parallele Transaktionen](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md).  
  
 Wenn der Treiber im Manualcommit Modus ist (durch Aufrufen von **SQLSetConnectAttr** -Attribut Sie mit der SQL_ATTR_AUTOCOMMIT auf SQL_AUTOCOMMIT_OFF festgelegt), eine neue Transaktion wird implizit gestartet, wenn eine SQL-Anweisung, die im enthalten sein kann eine Transaktion wird für die aktuelle Datenquelle ausgeführt. Weitere Informationen finden Sie unter [Commit-Modus](../../../odbc/reference/develop-app/commit-mode.md).  
  
 Um zu bestimmen, wie der Transaktionsvorgänge Cursor auswirken, eine Anwendung ruft **SQLGetInfo** mit den Optionen SQL_CURSOR_ROLLBACK_BEHAVIOR und SQL_CURSOR_COMMIT_BEHAVIOR. Weitere Informationen finden Sie unter den folgenden Abschnitten sowie unter [Auswirkung von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
 Wenn der SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR SQL_CB_DELETE, Wert **SQLEndTran** schließt und löscht alle geöffneten Cursor für alle Anweisungen der Verbindung zugeordnet und verwirft alle ausstehenden Ergebnisse. **SQLEndTran** lässt jede Anweisung, die im zugeordneten Zustand (Vorbereitung) vorhanden. die Anwendung können sie für nachfolgende SQL-Anforderungen wieder verwenden, oder rufen **SQLFreeStmt** oder **SQLFreeHandle** mit eine *HandleType* von SQL_HANDLE_STMT auf, um sie freizugeben.  
  
 Wenn der SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR SQL_CB_CLOSE, Wert **SQLEndTran** schließt alle geöffneten Cursor für alle Anweisungen der Verbindung zugeordnet. **SQLEndTran** lässt jede Anweisung vorhanden ist, einen Status ' vorbereitet '; die Anwendung kann Aufrufen **SQLExecute** für eine Anweisung mit der die Verbindung erst nach Aufrufen von verknüpften **SQLPrepare**.  
  
 Wenn der SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR SQL_CB_PRESERVE, Wert **SQLEndTran** wirkt sich nicht auf die geöffnete Cursor, die der Verbindung zugeordnet. Cursor bleiben in der Zeile, die sie vor dem Aufruf von verweist **SQLEndTran**.  
  
 Für die Treiber und Datenquellen, die Unterstützung von Transaktionen, Aufrufen von **SQLEndTran** mit entweder auf SQL_COMMIT oder sql_rollback fest, wenn keine Transaktion aktiv ist. gibt SQL_SUCCESS zurück (gibt an, dass keine Arbeit ein Commit oder Rollback) und hat keine Auswirkungen auf die Datenquelle.  
  
 Wenn Sie ein Treiber in den Autocommit-Modus ist, wird der Treiber-Manager wird nicht aufgerufen **SQLEndTran** im Treiber. **SQLEndTran** immer gibt SQL_SUCCESS zurück, unabhängig davon, ob sie aufgerufen wird, mit einem *' CompletionType '* der SQL_COMMIT oder sql_rollback fest.  
  
 Treiber oder Datenquellen, die keine Transaktionen unterstützen (**SQLGetInfo** *Option* SQL_TXN_CAPABLE ist SQL_TC_NONE) effektiv immer im Autocommit-Modus und daher jederzeit SQL_SUCCESS für **SQLEndTran** davon, ob sie aufgerufen werden, mit einem *' CompletionType '* der SQL_COMMIT oder sql_rollback fest. Diese Treiber und die Datenquellen werden nicht tatsächlich Transaktionen, wenn die Anforderung zurückgesetzt.  
  
## <a name="suspended-state"></a>Angehaltenen Zustand  
 Im Treiber-Manager, die vor Windows 7 veröffentlicht wurden, war eine Transaktion aktiv Wenn **SQLEndTran** SQL_ERROR zurückgegeben, aus dem Treiber. Allerdings war es möglich, dass die Transaktion wurde erfolgreich ein auf dem Server Commit hatte, doch der Treiber auf dem Client nicht benachrichtigt wurde, hatte (z. B. weil ein Fehler aufgetreten ist). Dies würden Sie die Verbindung in einem fehlerhaften Zustand lassen. Ab Windows 7, wenn **SQLEndTran** gibt SQL_ERROR zurück, die Verbindung möglicherweise in einem angehaltenen Zustand. In einem angehaltenen Zustand ist ist es möglich, nur-Lese Funktionen aufrufen. Schließlich die Anwendung sollte Aufrufen **SQLDisconnect** für eine unterbrochene Verbindung, um Ressourcen freizugeben.  
  
 Wenn alle der folgenden Bedingungen erfüllt sind, werden die Verbindung in einem angehaltenen Zustand platziert:  
  
-   Der Treiber gibt SQL_ERROR zurück aus **SQLEndTran**.  
  
-   Der Treiber ist ODBC 3.8 oder höher.  
  
-   Die Version der Anwendung ist 3.8 oder höher. oder die erneut kompilierten ODBC 2.x oder 3.x-Anwendung wurde erfolgreich abgebrochen. die **SQLEndTran** funktionieren über **SQLCancelHandle**.  
  
-   Der Treiber nicht die folgenden Meldungen zurück zum bestätigen, dass die Transaktion nicht abgeschlossen wurde:  
  
    -   25S03: Transaktion ein Rollback  
  
    -   40001: Serialisierungsfehler  
  
    -   40002: integritätseinschränkung  
  
    -   HYC00: Optionales Feature nicht implementiert.  
  
 Wenn **SQLEndTran** wurde aufgerufen, in einer Umgebung-Handle und die Verbindungen der oben genannten Bedingungen erfüllt, werden alle Verbindungen, die mit denselben Treiber Zustand "angehalten" abgelegt.  
  
 Nachdem eine Anwendung ruft **SQLDisconnect** in eine angehaltene Verbindung kann die Verbindung für die Verbindung zu einer anderen Datenquelle oder die gleiche Datenquelle verwendet werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Wird eine Funktion, die für ein Verbindungshandle asynchrone Ausführung abgebrochen.|[SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Zurückgeben von Informationen zu einer Datenquelle oder Treiber|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Ein Handle freigeben|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Freigeben eines Anweisungshandles|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
