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
ms.openlocfilehash: 3ca7ed4f6bbcd31b8f67b95dc14a2c6c301b5a59
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138832"
---
# <a name="sqlmoreresults-function"></a>SQLMoreResults-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLMoreResults** bestimmt, ob weitere Ergebnisse für eine Anweisung verfügbar sind, die **Select**-, **Update**-, **Insert**-oder **Delete** -Anweisungen enthält. wenn dies der Fall ist, wird die Verarbeitung für diese Ergebnisse initialisiert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLMoreResults** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLMoreResults** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Der Optionswert wurde geändert.|Der Wert eines Anweisungs Attributs wurde bei der Verarbeitung des Batches geändert. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|40001|Serialisierungsfehler|Für die Transaktion wurde aufgrund eines Ressourcen Deadlocks mit einer anderen Transaktion ein Rollback ausgeführt.|  
|40003|Anweisungs Vervollständigung unbekannt|Die zugeordnete Verbindung konnte während der Ausführung dieser Funktion nicht hergestellt werden, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die **SQLMoreResults** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die **SQLMoreResults** -Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die **SQLMoreResults** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLMoreResults** -Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **Select** -Anweisungen geben Resultsets zurück. Durch **Update**-, **Insert**-und **Delete** -Anweisungen wird die Anzahl der betroffenen Zeilen zurückgegeben. Wenn eine dieser Anweisungen in einem Batch verarbeitet und mit Arrays von Parametern übermittelt wird (in steigender Reihenfolge der Parameter in der Reihenfolge, in der Sie im Batch angezeigt werden), oder in Prozeduren, können Sie mehrere Resultsets oder Zeilen Anzahlen zurückgeben. Weitere Informationen zu Batches von Anweisungen und Arrays von Parametern finden Sie unter [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md) und [Arrays von Parameterwerten](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Nach dem Ausführen des Batches wird die Anwendung auf dem ersten Resultset positioniert. Die Anwendung kann **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, **SQLSetPos**und alle Metadatenfunktionen auf dem ersten oder allen nachfolgenden Resultsets aufrufen, genauso als wäre es nur ein einzelnes Resultset. Sobald das erste Resultset abgeschlossen ist, ruft die Anwendung **SQLMoreResults** auf, um zum nächsten Resultset zu wechseln. Wenn ein anderes Resultset oder eine andere Anzahl verfügbar ist, gibt **SQLMoreResults** SQL_SUCCESS zurück und initialisiert das Resultset oder die Anzahl für die weitere Verarbeitung. Wenn eine der Zeilen Anzahl generierende Anweisungen zwischen Resultset-generierten-Anweisungen angezeigt werden, können Sie durch den Aufruf von **SQLMoreResults durch den Aufruf von sqlmoreres** Nach dem Aufruf von **SQLMoreResults** für **Update**-, **Insert**-oder **Delete** -Anweisungen kann eine Anwendung **SQLRowCount**aufrufen.  
  
 Wenn ein Aktuelles Resultset mit nicht abgerufenen Zeilen vorhanden ist, verwirft **SQLMoreResults** das Resultset und macht das nächste Resultset oder die nächste Anzahl verfügbar. Wenn alle Ergebnisse verarbeitet wurden, gibt **SQLMoreResults** SQL_NO_DATA zurück. Bei manchen Treibern sind Ausgabeparameter und Rückgabewerte erst verfügbar, wenn alle Resultsets und Zeilenzähler verarbeitet wurden. Bei solchen Treibern werden Ausgabeparameter und Rückgabewerte verfügbar, wenn **SQLMoreResults** SQL_NO_DATA zurückgibt.  
  
 Alle Bindungen, die für das vorherige Resultset festgelegt wurden, sind weiterhin gültig. Wenn sich die Spalten Strukturen für dieses Resultset unterscheiden, kann das Aufrufen von **SQLFetch** oder **SQLFetchScroll** zu einem Fehler oder einem Abschneiden führen. Um dies zu verhindern, muss die Anwendung **SQLBindCol** aufrufen, um nach Bedarf explizit erneut zu binden (oder durch Festlegen von Deskriptorfeldern). Alternativ kann die Anwendung **SQLFreeStmt** mit der *Option* SQL_UNBIND zum Aufheben der Bindung aller Spalten Puffer aufzurufen.  
  
 Die Werte von Anweisungs Attributen, z. b. Cursortyp, Cursor Parallelität, Keysetgröße oder maximale Länge, können sich ändern, wenn die Anwendung durch Aufrufe von **SQLMoreResults**durch den Batch navigiert. In diesem Fall gibt **SQLMoreResults** SQL_SUCCESS_WITH_INFO und SQLSTATE 01s02 (Optionswert wurde geändert) zurück.  
  
 Durch den Aufruf von **SQLCloseCursor**oder **SQLFreeStmt** mit der *Option* SQL_CLOSE werden alle Resultsets und Zeilenzähler verworfen, die als Ergebnis der Ausführung des Batches verfügbar waren. Das Anweisungs Handle kehrt entweder in den zugeordneten oder vorbereiteten Zustand zurück. Wenn Sie **SQLCancel** aufrufen, um eine asynchron ausgeführte Funktion abzubrechen, wenn ein Batch ausgeführt wurde und das Anweisungs Handle sich im Ausführungs-, Cursor-oder asynchronen Zustand befindet, führt dies dazu, dass alle Resultsets und Zeilen Anzahlen, die von dem Batch generiert werden, bei erfolgreicher Ausführung des Cancel-Aufrufs Die Anweisung kehrt dann in den vorbereiteten oder zugewiesenen Zustand zurück.  
  
 Wenn ein Batch von Anweisungen oder eine Prozedur andere SQL-Anweisungen mit **Select**-, **Update**-, **Insert**-und **Delete** -Anweisungen vermischt, wirken sich diese anderen Anweisungen nicht auf **SQLMoreResults**aus.  
  
 Weitere Informationen finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Wenn eine gesuchte Update-, INSERT-oder DELETE-Anweisung in einem Batch von-Anweisungen keine Auswirkungen auf Zeilen in der Datenquelle hat, gibt **SQLMoreResults** SQL_SUCCESS zurück. Dies unterscheidet sich von der Groß-/Kleinschreibung einer durchsuchten Update-, INSERT-oder DELETE-Anweisung, die über **SQLExecDirect**, **SQLExecute**oder **SQLParamData**ausgeführt wird, die SQL_NO_DATA zurückgibt, wenn Sie keine Auswirkungen auf Zeilen in der Datenquelle hat. Wenn eine Anwendung **SQLRowCount** aufruft, um die Zeilen Anzahl nach einem Aufruf von **SQLMoreResults** nicht zu beeinflussen, gibt **SQLRowCount** SQL_NO_DATA zurück.  
  
 Weitere Informationen zur gültigen Sequenzierung von Funktionen zur Ergebnis Verarbeitung finden Sie unter [Anhang B: ODBC-Status Übergangs Tabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Weitere Informationen zu SQL_PARAM_DATA_AVAILABLE und gestreamt-Ausgabeparametern finden [Sie unter Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Verfügbarkeit der Zeilen Anzahl  
 Wenn ein Batch mehrere aufeinander folgende, Zeilen zählungs generierende Anweisungen enthält, wird es möglich sein, dass diese Zeilenzähler in nur eine Zeilen Anzahl aufgerundet werden. Wenn ein Batch z. b. fünf INSERT-Anweisungen enthält, können bestimmte Datenquellen fünf einzelne Zeilen Anzahlen zurückgeben. Bestimmte andere Datenquellen geben nur eine Zeilen Anzahl zurück, die die Summe der fünf einzelnen Zeilen Zählungen darstellt.  
  
 Wenn ein Batch eine Kombination aus Resultset-Generierungs-und Zeilen Anzahl Generierungs Anweisungen enthält, ist die Zeilen Anzahl möglicherweise überhaupt nicht verfügbar. Das Verhalten des Treibers in Bezug auf die Verfügbarkeit von Zeilen Anzahlen wird im SQL_BATCH_ROW_COUNT Informationstyp aufgelistet, der durch einen **SQLGetInfo-Befehl**verfügbar ist. Nehmen wir beispielsweise an, dass der Batch eine **Select**-, gefolgt von zwei **Insert**s und eine andere **Select**-Option enthält. Dann sind die folgenden Fälle möglich:  
  
-   Die Zeilen Anzahl, die den beiden **Insert** -Anweisungen entspricht, ist überhaupt nicht verfügbar. Der erste Befehl von **SQLMoreResults** positioniert Sie im Resultset der zweiten **Select** -Anweisung.  
  
-   Die Zeilen Anzahl, die den beiden **Insert** -Anweisungen entspricht, ist einzeln verfügbar. (Ein **SQLGetInfo-Befehl** gibt nicht das SQL_BRC_ROLLED_UP Bit für den SQL_BATCH_ROW_COUNT Informationstyp zurück.) Der erste **SQLMoreResults** -Befehl positioniert Sie nach der Zeilen Anzahl der ersten **Einfügung**, und der zweite-Befehl positioniert Sie auf der Zeilen Anzahl der zweiten **Einfügung**. Der dritte **SQLMoreResults** -Befehl positioniert Sie im Resultset der zweiten **Select** -Anweisung.  
  
-   Die Zeilen Anzahl, die den beiden **Einfügungen** entspricht, wird in eine einzelne Zeilen Anzahl hochgefahren, die verfügbar ist. (Ein Aufrufen von **SQLGetInfo** gibt das SQL_BRC_ROLLED_UP Bit für den SQL_BATCH_ROW_COUNT Informationstyp zurück.) Der erste **SQLMoreResults** -Befehl positioniert Sie an der Anzahl der Aufzählungs Zeilen, und der zweite **SQLMoreResults** -Befehl positioniert Sie im Resultset der zweiten **Select**-Option.  
  
 Bestimmte Treiber stellen Zeilen Anzahlen nur für explizite Batches und nicht für gespeicherte Prozeduren zur Verfügung.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Datenblocks oder Scrollen durch ein Resultset|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in Vorwärtsrichtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Teils oder aller Datenspalten|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
