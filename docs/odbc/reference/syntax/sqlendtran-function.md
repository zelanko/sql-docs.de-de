---
title: SQLEndTran-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cce7792e52fce4984f3da41e11d79c34b6b79e53
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302741"
---
# <a name="sqlendtran-function"></a>SQLEndTran-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLEndTran** fordert einen Commit- oder Rollbackvorgang für alle aktiven Vorgänge für alle Anweisungen an, die einer Verbindung zugeordnet sind. **SQLEndTran** kann auch anfordern, dass ein Commit- oder Rollbackvorgang für alle Verbindungen ausgeführt wird, die einer Umgebung zugeordnet sind.  
  
> [!NOTE]  
>  Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn ein ODBC 3. *x-Anwendung* arbeitet mit einem ODBC 2. *x-Treiber,* siehe [Mapping-Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Handle-Typ-Id. Enthält entweder SQL_HANDLE_ENV (wenn *Handle* ein Umgebungshandle ist) oder SQL_HANDLE_DBC (wenn *Handle* ein Verbindungshandle ist).  
  
 *Handle*  
 [Eingabe] Das Handle des von *HandleType*angegebenen Typs, der den Umfang der Transaktion angibt. Weitere Informationen finden Sie unter "Kommentare".  
  
 *CompletionType*  
 [Eingabe] Einer der beiden folgenden Werte:  
  
 SQL_COMMIT SQL_ROLLBACK  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLEndTran** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem entsprechenden *HandleType* und *Handle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLEndTran** zurückgegeben werden, und es werden die sqlSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) Der *HandleType* wurde SQL_HANDLE_DBC, und der *Handle* befand sich nicht in einem verbundenen Zustand.|  
|08007|Verbindungsfehler während der Transaktion|Der *HandleType* wurde SQL_HANDLE_DBC, und die verbindung, die dem *Handle* zugeordnet ist, ist während der Ausführung der Funktion fehlgeschlagen, und es kann nicht festgestellt werden, ob das angeforderte **COMMIT** oder **ROLLBACK** vor dem Fehler aufgetreten ist.|  
|25S01|Transaktionsstatus unbekannt|Mindestens eine der Verbindungen in *Handle* konnte die Transaktion nicht mit dem angegebenen Ergebnis abschließen, und das Ergebnis ist unbekannt.|  
|25S02|Transaktion ist noch aktiv|Der Treiber konnte nicht garantieren, dass alle Arbeiten in der globalen Transaktion atomar abgeschlossen werden konnten, und die Transaktion ist weiterhin aktiv.|  
|25S03|Transaktion wird zurückgesetzt|Der Treiber konnte nicht garantieren, dass alle Arbeiten in der globalen Transaktion atomar abgeschlossen werden konnten, und alle Arbeiten in der Transaktion, die in *Handle* aktiv ist, wurden zurückgesetzt.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40002|Verletzung der Integritätseinschränkung|*Der CompletionType* wurde SQL_COMMIT, und die Verpflichtung von Änderungen verursachte eine Verletzung von Integritätseinschränkungen. Daher wurde für die Transaktion ein Rollback ausgeführt.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*szMessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *den ConnectionHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor sie die Ausführung der [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) abgeschlossen hat, wurde sie auf dem *ConnectionHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *ConnectionHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung von SQLCancelHandle abgeschlossen wurde, wurde **sqlCancelHandle** von einem anderen Thread in einer Multithreadanwendung auf den *ConnectionHandle* aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Eine asynchron ausführende Funktion wurde für ein Anweisungshandle aufgerufen, das dem *ConnectionHandle* zugeordnet war, und wurde noch ausgeführt, als **SQLEndTran** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausführende Funktion (nicht diese) wurde für den *ConnectionHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für ein Anweisungshandle aufgerufen, das dem *ConnectionHandle* zugeordnet ist, und zurückgegebenSQL_NEED_DATA. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde aufgerufen, damit *handle* with *HandleType* auf SQL_HANDLE_DBC festgelegt wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungshandles aufgerufen, die *Handle* zugeordnet sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY012|Ungültiger Transaktionsvorgangscode|(DM) Der für das Argument *CompletionType* angegebene Wert war weder SQL_COMMIT noch SQL_ROLLBACK.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|(DM) Der für das Argument *HandleType* angegebene Wert war weder SQL_HANDLE_ENV noch SQL_HANDLE_DBC.|  
|HY115|SQLEndTran ist für eine Umgebung, die eine Verbindung mit aktivierter asynchroner Funktion enthält, nicht zulässig.|(DM) *HandleType* kann nicht auf SQL_HANDLE_ENV festgelegt werden, wenn die asynchrone Ausführung von Verbindungsfunktionen für eine Verbindung in der Umgebung aktiviert ist.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie im Abschnitt Kommentare zu diesem Thema.|  
|HYC00|Optionale Funktion nicht implementiert|Der Treiber oder die Datenquelle unterstützt den **ROLLBACK-Vorgang** nicht.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *ConnectionHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 Für eine ODBC 3. *x-Treiber,* wenn *HandleType* SQL_HANDLE_ENV und *Handle* ein gültiges Umgebungshandle ist, ruft der Treiber-Manager **SQLEndTran** in jedem Treiber auf, der der Umgebung zugeordnet ist. Das *Handle-Argument* für den Aufruf an einen Treiber ist das Umgebungshandle des Treibers. Für eine ODBC 2. *x-Treiber,* wenn *HandleType* SQL_HANDLE_ENV und *Handle* ein gültiges Umgebungshandle ist und mehrere Verbindungen in einem verbundenen Zustand in dieser Umgebung vorhanden sind, ruft der Treiber-Manager **SQLTransact** einmal für jede Verbindung in einem verbundenen Zustand in dieser Umgebung auf. Das *Handle-Argument* in jedem Aufruf ist das Handle der Verbindung. In beiden Fällen versucht der Treiber, Transaktionen für alle Verbindungen, die sich in einem verbundenen Zustand in dieser Umgebung befinden, festzuschreiben oder zurückzusetzen, abhängig vom Wert von *CompletionType.* Verbindungen, die nicht aktiv sind, wirken sich nicht auf die Transaktion aus.  
  
> [!NOTE]  
>  **SQLEndTran** kann nicht zum Commit oder Rollback von Transaktionen in einer freigegebenen Umgebung verwendet werden. SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) wird zurückgegeben, wenn **SQLEndTran** aufgerufen wird, wobei *Handle* entweder auf das Handle einer freigegebenen Umgebung oder das Handle einer Verbindung in einer freigegebenen Umgebung festgelegt ist.  
  
 Der Treiber-Manager gibt SQL_SUCCESS nur zurück, wenn er für jede Verbindung SQL_SUCCESS erhält. Wenn der Treiber-Manager SQL_ERROR für eine oder mehrere Verbindungen erhält, gibt er SQL_ERROR an die Anwendung zurück, und die Diagnoseinformationen werden in der Diagnosedatenstruktur der Umgebung platziert. Um zu ermitteln, welche Verbindung oder Verbindungen während des Commit- oder Rollbackvorgangs fehlgeschlagen sind, kann die Anwendung **SQLGetDiagRec** für jede Verbindung aufrufen.  
  
> [!NOTE]  
>  Der Treiber-Manager simuliert keine globale Transaktion über alle Verbindungen hinweg und verwendet daher keine zweiphasigen Commitprotokolle.  
  
 Wenn *CompletionType* SQL_COMMIT ist, gibt **SQLEndTran** eine Commitanforderung für alle aktiven Vorgänge für jede Anweisung aus, die einer betroffenen Verbindung zugeordnet ist. Wenn *CompletionType* SQL_ROLLBACK ist, gibt **SQLEndTran** eine Rollbackanforderung für alle aktiven Vorgänge für jede Anweisung aus, die einer betroffenen Verbindung zugeordnet ist. Wenn keine Transaktionen aktiv sind, gibt **SQLEndTran** SQL_SUCCESS ohne Auswirkungen auf Datenquellen zurück. Weitere Informationen finden Sie unter [Commiting and Rolling Back Transactions](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md).  
  
 Wenn sich der Treiber im manuellen Commit-Modus befindet (durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_AUTOCOMMIT Attribut auf SQL_AUTOCOMMIT_OFF festgelegt), wird implizit eine neue Transaktion gestartet, wenn eine SQL-Anweisung, die in einer Transaktion enthalten sein kann, für die aktuelle Datenquelle ausgeführt wird. Weitere Informationen finden Sie unter [Commit-Modus](../../../odbc/reference/develop-app/commit-mode.md).  
  
 Um zu bestimmen, wie sich Transaktionsvorgänge auf Cursor auswirken, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CURSOR_ROLLBACK_BEHAVIOR und SQL_CURSOR_COMMIT_BEHAVIOR auf. Weitere Informationen finden Sie in den folgenden Absätzen und auch unter [Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).  
  
 Wenn der wert SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR SQL_CB_DELETE entspricht, schließt und löscht **SQLEndTran** alle geöffneten Cursor für alle Anweisungen, die der Verbindung zugeordnet sind, und verwirft alle ausstehenden Ergebnisse. **SQLEndTran** belässt jede Anweisung in einem zugewiesenen (unvorbereiteten) Zustand; Die Anwendung kann sie für nachfolgende SQL-Anforderungen wiederverwenden oder **SQLFreeStmt** oder **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_STMT aufrufen, um sie zuzuweisen.  
  
 Wenn der wert SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR SQL_CB_CLOSE entspricht, schließt **SQLEndTran** alle geöffneten Cursor für alle Anweisungen, die der Verbindung zugeordnet sind. **SQLEndTran** belässt jede Anweisung in einem vorbereiteten Zustand. Die Anwendung kann **SQLExecute** für eine Anweisung aufrufen, die der Verbindung zugeordnet ist, ohne zuerst **SQLPrepare**aufzurufen.  
  
 Wenn der wert SQL_CURSOR_ROLLBACK_BEHAVIOR oder SQL_CURSOR_COMMIT_BEHAVIOR SQL_CB_PRESERVE entspricht, wirkt sich **SQLEndTran** nicht auf die der Verbindung zugeordneten geöffneten Cursor aus. Cursor bleiben in der Zeile, auf die sie vor dem Aufruf von **SQLEndTran**gezeigt haben.  
  
 Bei Treibern und Datenquellen, die Transaktionen unterstützen, gibt der Aufruf von **SQLEndTran** mit SQL_COMMIT oder SQL_ROLLBACK, wenn keine Transaktion aktiv ist, SQL_SUCCESS zurück (was darauf hinweist, dass keine Arbeit zum Festizieren oder Zurücksetzen ausgeführt werden kann) und hat keine Auswirkungen auf die Datenquelle.  
  
 Wenn sich ein Treiber im Autocommit-Modus befindet, ruft der Treiber-Manager **SQLEndTran** im Treiber nicht auf. **SQLEndTran** gibt immer SQL_SUCCESS zurück, unabhängig davon, ob es mit einem *CompletionType* von SQL_COMMIT oder SQL_ROLLBACK aufgerufen wird.  
  
 Treiber oder Datenquellen, die keine Transaktionen unterstützen **(SQLGetInfo-Option** *option* SQL_TXN_CAPABLE ist SQL_TC_NONE), befinden sich effektiv immer im Autocommit-Modus und geben daher immer SQL_SUCCESS für **SQLEndTran** zurück, unabhängig davon, ob sie mit einem *CompletionType* von SQL_COMMIT oder SQL_ROLLBACK aufgerufen werden oder nicht. Solche Treiber und Datenquellen setzen Transaktionen nicht zurück, wenn sie dazu aufgefordert werden.  
  
## <a name="suspended-state"></a>Suspended State  
 In Treiber-Managern, die vor Windows 7 veröffentlicht wurden, war eine Transaktion aktiv, wenn **SQLEndTran** SQL_ERROR vom Treiber zurückgegeben hat. Es war jedoch möglich, dass die Transaktion erfolgreich auf dem Server ausgeführt wurde, aber der Treiber auf dem Client wurde nicht benachrichtigt (z. B. weil ein Netzwerkfehler aufgetreten ist). Dies würde die Verbindung in einem schlechten Zustand lassen. Ab Windows 7, wenn **SQLEndTran** SQL_ERROR zurückgibt, befindet sich die Verbindung möglicherweise in einem angehaltenen Zustand. In einem angehaltenen Zustand ist es möglich, schreibgeschützte Funktionen aufzurufen. Schließlich sollte die Anwendung **SQLDisconnect** für eine angehaltene Verbindung aufrufen, um Ressourcen freizugeben.  
  
 Wenn alle der folgenden Bedingungen erfüllt sind, wird die Verbindung in einen angehaltenen Zustand versetzt:  
  
-   Der Treiber gibt SQL_ERROR aus **SQLEndTran**zurück.  
  
-   Der Treiber ist ODBC Version 3.8 oder höher.  
  
-   Die Anwendungsversion ist 3.8 oder höher; oder die neu kompilierte ODBC 2.x- oder 3.x-Anwendung bricht die **SQLEndTran-Funktion** erfolgreich über **SQLCancelHandle**ab.  
  
-   Der Treiber hat keine der folgenden Meldungen zurückgegeben, die bestätigen, dass die Transaktion nicht abgeschlossen wurde:  
  
    -   25S03: Transaktion wird zurückgesetzt  
  
    -   40001: Serialisierungsfehler  
  
    -   40002: Integritätseinschränkung  
  
    -   HYC00: Optionale Funktion nicht implementiert  
  
 Wenn **SQLEndTran** für ein Umgebungshandle aufgerufen wurde und eine seiner Verbindungen die oben genannten Bedingungen erfüllt, werden alle Verbindungen, die eine Verbindung mit demselben Treiber herstellen, in den angehaltenen Zustand versetzt.  
  
 Nachdem eine Anwendung **SQLDisconnect** für eine angehaltene Verbindung aufruft, kann die Verbindung zum erneuten Herstellen einer Verbindung mit einer anderen Datenquelle oder derselben Datenquelle verwendet werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen einer Funktion, die asynchron auf einem Verbindungshandle ausgeführt wird.|[SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|Zurückgeben von Informationen zu einem Treiber oder einer Datenquelle|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Befreien eines Griffs|[SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Befreien eines Anweisungshandles|[SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
