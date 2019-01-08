---
title: SQLMoreResults-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLMoreResults
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLMoreResults
helpviewer_keywords:
- SQLMoreResults function [ODBC]
ms.assetid: bf169ed5-4d55-412c-b184-12065a726e89
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a680f5579b241f6b279f5ecc994d32c8fad784f
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53205359"
---
# <a name="sqlmoreresults-function"></a>SQLMoreResults-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLMoreResults** bestimmt, ob weitere Ergebnisse anzeigt, die sich auf eine Anweisung mit verfügbaren **wählen**, **UPDATE**, **einfügen**, oder  **Löschen Sie** Anweisungen und, wenn dies der Fall ist, initialisiert verarbeiten, um diese Ergebnisse zu erzielen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA ZURÜCKGIBT, WIRD SQL_ERROR, SQL_INVALID_HANDLE ODER SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLMoreResults** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* SQL _HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLMoreResults** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert wurde geändert.|Der Wert einer Anweisung-Attributs als Batches geändert wurde verarbeitet. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Deadlocks Ressource mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Unbekannter Anweisungsabschluss|Fehler bei der zugeordnete Verbindung während der Ausführung dieser Funktion und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die **SQLMoreResults** Funktion aufgerufen wurde und, bevor es ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* . Die **SQLMoreResults** Funktion wurde erneut aufgerufen, auf die *StatementHandle*.<br /><br /> Die **SQLMoreResults** Funktion aufgerufen wurde und, bevor es ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*  von einem anderen Thread in einer multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLMoreResults** Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
## <a name="comments"></a>Kommentare  
 **Wählen Sie** Anweisungen Resultsets zurückgeben. **UPDATE**, **einfügen**, und **löschen** Anweisungen die Anzahl der betroffenen Zeilen zurückgegeben. Wenn eine dieser Anweisungen zusammengefasst werden, mit Arrays von Parametern (nummeriert in aufsteigender Reihenfolge der Parameter in der Reihenfolge, die sie in den Batch angezeigt werden) oder in Prozeduren gesendet, sie können mehrere Resultsets zurückgeben oder Zeilenanzahl. Weitere Informationen zu Batches von Anweisungen und Arrays von Parametern, finden Sie unter [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md) und [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Nach dem Ausführen des Batches, wird die Anwendung auf das erste Resultset positioniert. Die Anwendung kann Aufrufen **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll** , **SQLSetPos**, und alle Metadatenfunktionen, auf das erste oder alle nachfolgenden Resultset mit Vorwärtscursor, wie es gäbe es nur ein einzelnes Resultset. Wenn sie mit dem ersten Resultset abgeschlossen ist, ruft die Anwendung **SQLMoreResults** , in das nächste Resultset zu verschieben. Wenn ein anderes Resultset oder Count verfügbar ist, **SQLMoreResults** gibt SQL_SUCCESS zurück, und initialisiert die Resultset oder die Anzahl für die weitere Verarbeitung. Zeile Count – Generieren von Anweisungen angezeigt, in der Zwischenzeit generiert Set-Anweisungen führen, sie können ausgeführt werden, durch Aufrufen von **SQLMoreResults**. Nach dem Aufruf **SQLMoreResults** für **UPDATE**, **einfügen**, oder **löschen** -Anweisungen, die eine Anwendung kann eine Aufrufen **SQLRowCount**.  
  
 Wenn es eine aktuelle Resultset mit Zeilen Resultsetzeile wurde, **SQLMoreResults** verwirft das Resultset und das nächste Resultset oder zählen verfügbar macht. Wenn alle Ergebnisse verarbeitet wurden, **SQLMoreResults** SQL_NO_DATA zurückgibt. Für einige Treiber sind Output-Parameter und Rückgabewerte nicht verfügbar, bis alle Resultsets und Zeilen verarbeitet wurden. Für solche Treiber, Ausgabeparameter und Rückgabewerte, die beim verfügbar **SQLMoreResults** SQL_NO_DATA zurückgibt.  
  
 Alle Bindungen, die festgelegt wurden, für das vorherige Resultset immer noch bleiben gültig. Wenn die spaltenstrukturen für dieses Resultset unterschiedlich sind, klicken Sie dann aufrufen **SQLFetch** oder **SQLFetchScroll** verursachen einen Fehler oder abschneiden. Um dies zu verhindern, muss die Anwendung aufrufen **SQLBindCol** explizit nach Bedarf erneut binden (oder durch Festlegen von deskriptorfeldern tun). Sie können auch die Anwendung aufrufen **SQLFreeStmt** mit einer *Option* SQL_UNBIND alle Spaltenpuffer aufzuheben.  
  
 Die Werte der Anweisungsattribute, z. B. Cursortyp, Cursorparallelität, Keysetgröße oder maximale Länge möglicherweise ändern, während die Anwendung über den Batch durch Aufrufe von navigiert **SQLMoreResults**. In diesem Fall **SQLMoreResults** gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01 s 02 (der Optionswert wurde geändert).  
  
 Aufrufen von **SQLCloseCursor**, oder **SQLFreeStmt** mit einer *Option* von SQL_CLOSE, verwirft alle Resultsets und Zeilenanzahl, die als Ergebnis der Ausführung von verfügbar waren der Batch. Gibt zurück, das Anweisungshandle auf den zugeordneten oder vorbereitete Zustand. Aufrufen von **SQLCancel** eine asynchron ausgeführte Funktion abgebrochen, wenn ein Batch ausgeführt wurde und das Anweisungshandle im ausgeführten, Cursor positioniert, oder asynchroner Zustand alle Ergebnisse Mengen führt und Zeilenanzahl generiert, indem der Batch wird verworfen, wenn der Aufruf von "Abbrechen" erfolgreich war. Klicken Sie dann die Anweisung, die auf die vorbereiteten oder zugeordneten Zustand zurückgesetzt werden.  
  
 Wenn ein Batch von Anweisungen oder eine Prozedur mit anderen SQL-Anweisungen kombiniert **wählen**, **UPDATE**, **einfügen**, und **löschen** -Anweisungen Diese anderen Anweisungen wirken sich nicht **SQLMoreResults**.  
  
 Weitere Informationen finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Wenn eine gesuchte aktualisieren, insert oder-Anweisung in DELETE ein Batch von Anweisungen hat keine Auswirkungen auf alle Zeilen in der Datenquelle **SQLMoreResults** gibt SQL_SUCCESS zurück. Dies unterscheidet sich von die Groß-/Kleinschreibung ein gesuchtes Update, insert oder delete-Anweisung, die ausgeführt wird, über **SQLExecDirect**, **SQLExecute**, oder **SQLParamData**, Gibt SQL_NO_DATA zurück, wenn sie alle Zeilen in der Datenquelle nicht beeinträchtigt wird. Wenn eine Anwendung ruft **SQLRowCount** zum Abrufen der Anzahl der Zeilen nach einem Aufruf von **SQLMoreResults** Zeilen hat keine Auswirkungen **SQLRowCount** gibt SQL_NO_DATA zurück.  
  
 Weitere Informationen zu den gültigen Sequenzierung der ergebnisverarbeitung Funktionen, finden Sie unter [Anhang B: ODBC-Übergang Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Weitere Informationen über SQL_PARAM_DATA_AVAILABLE und gestreamte Output-Parameter, finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Verfügbarkeit von Zeilenanzahlen  
 Wenn ein Batch mehrere aufeinander folgende Zeile Count – Generieren von Anweisungen enthält, ist es möglich, dass diese Zeilenanzahl in nur einem Zeilenanzahl Rollup enthalten sind. Beispielsweise verfügt ein Batch einfügen fünf Anweisungen, und dann bestimmte Datenquellen von fünf einzelne Zeilenanzahl zurückgegeben werden. Bestimmte Daten aus anderen Quellen zurückgeben, nur eine Zeilenanzahl, die die Summe der fünf einzelne Zeilenanzahlen darstellt.  
  
 Wenn ein Batch eine Kombination von Set generiertem Ergebnis und Zeile Count – Generieren von Anweisungen enthält, Zeilenanzahl oder möglicherweise nicht zur Verfügung zu. Das Verhalten des Treibers in Bezug auf die Verfügbarkeit der Zeilenanzahl wird aufgelistet, in den Typ der SQL_BATCH_ROW_COUNT-Informationen zur Verfügung, durch einen Aufruf von **SQLGetInfo**. Nehmen wir beispielsweise an, dass der Batch enthält eine **wählen**, gefolgt von zwei **einfügen**s und einen anderen **wählen**. Klicken Sie dann sind die folgenden Fälle möglich:  
  
-   Die Zeilenanzahl, die die beiden entspricht **einfügen** Anweisungen sind überhaupt nicht verfügbar. Der erste Aufruf **SQLMoreResults** positionieren Sie für das Resultset des zweiten **wählen** Anweisung.  
  
-   Die Zeilenanzahl, die die beiden entspricht **einfügen** Anweisungen einzeln verfügbar sind. (Einen Aufruf von **SQLGetInfo** keinen SQL_BRC_ROLLED_UP Bits für den Typ der SQL_BATCH_ROW_COUNT Informationen zurückgibt.) Der erste Aufruf **SQLMoreResults** positionieren Sie auf die Anzahl der Zeilen des ersten **einfügen**, und der zweite Aufruf wird positionieren Sie Sie auf die Anzahl der Zeilen des zweiten **einfügen**. Der dritte Aufruf von **SQLMoreResults** positionieren Sie für das Resultset des zweiten **wählen** Anweisung.  
  
-   Die Zeilenanzahl, die die beiden entspricht **fügt** sammlungsverwaltung in einem einzelnen Zeilenanzahl, die verfügbar ist. (Einen Aufruf von **SQLGetInfo** gibt zurück, das bit für den Informationstyp SQL_BATCH_ROW_COUNT SQL_BRC_ROLLED_UP.) Der erste Aufruf **SQLMoreResults** positionieren Sie die Rollup-Zeilenanzahl und der zweite Aufruf von **SQLMoreResults** positionieren Sie für das Resultset des zweiten **wählen**.  
  
 Bestimmten Treiber stellen die Zeilenanzahl nur für explizite Batches und nicht für gespeicherte Prozeduren verfügbar sind.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Zeile oder einen Block von Daten in eine Richtung Vorwärtscursor|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen von teilweise oder vollständig eine Spalte mit Daten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
