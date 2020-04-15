---
title: SQLMoreResults-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78bbb277e4b783eb46c79f59939a1080feae2b60
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304741"
---
# <a name="sqlmoreresults-function"></a>SQLMoreResults-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ODBC  
  
 **Zusammenfassung**  
 **SQLMoreResults** bestimmt, ob weitere Ergebnisse für eine Anweisung verfügbar sind, die **SELECT-,** **UPDATE-,** **INSERT-** oder **DELETE-Anweisungen** enthält, und initialisiert, falls dies der Fall ist, die Verarbeitung für diese Ergebnisse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE, ODER SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLMoreResults** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLMoreResults** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert hat sich geändert|Der Wert eines Anweisungsattributs wurde geändert, als der Batch verarbeitet wurde. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|40001|Serialisierungsfehler|Die Transaktion wurde aufgrund eines Ressourcenstillstands mit einer anderen Transaktion zurückgesetzt.|  
|40003|Anweisungsvervollständigung unbekannt|Die zugeordnete Verbindung ist während der Ausführung dieser Funktion fehlgeschlagen, und der Status der Transaktion kann nicht bestimmt werden.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die **SQLMoreResults-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die **SQLMoreResults-Funktion** erneut für den *StatementHandle*aufgerufen.<br /><br /> Die **SQLMoreResults-Funktion** wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLMoreResults-Funktion** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
## <a name="comments"></a>Kommentare  
 **SELECT-Anweisungen** geben Ergebnissätze zurück. **UPDATE**-, **INSERT-** und **DELETE-Anweisungen** geben eine Anzahl der betroffenen Zeilen zurück. Wenn eine dieser Anweisungen mit Arrays von Parametern (in steigender Parameterreihenfolge in der Reihenfolge, in der sie im Batch angezeigt werden) oder in Prozeduren gestapelt, mehrere Resultsets oder Zeilenanzahlen zurückgegeben werden, können sie mehrere Resultsets oder Zeilenanzahlen zurückgeben. Informationen zu Batches von Anweisungen und Arrays von Parametern finden Sie unter [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md) and [Arrays of Parameter Values](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 Nach dem Ausführen des Batches wird die Anwendung auf dem ersten Resultset positioniert. Die Anwendung kann **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, **SQLSetPos**und alle Metadatenfunktionen auf dem ersten oder allen nachfolgenden Resultsets aufrufen, so wie es wäre, wenn es nur ein einzelnes Resultset gäbe. Sobald dies mit dem ersten Resultset geschehen ist, ruft die Anwendung **SQLMoreResults** auf, um zum nächsten Resultset zu wechseln. Wenn ein anderes Resultset oder eine andere Anzahl verfügbar ist, gibt **SQLMoreResults** SQL_SUCCESS zurück und initialisiert das Resultset oder die Anzahl für die zusätzliche Verarbeitung. Wenn Zeilenzähl-generierende Anweisungen zwischen Ergebnissatzgenerierungsanweisungen angezeigt werden, können sie durch Aufrufen von **SQLMoreResults**überschritt werden. Nach dem Aufrufen von **SQLMoreResults** für **UPDATE**-, **INSERT**- oder **DELETE-Anweisungen** kann eine Anwendung **SQLRowCount**aufrufen.  
  
 Wenn ein aktuelles Resultset mit nicht abgerufenen Zeilen vorhanden war, verwirft **SQLMoreResults** dieses Resultset und stellt das nächste Resultset oder die nächste Anzahl zur Verfügung. Wenn alle Ergebnisse verarbeitet wurden, gibt **SQLMoreResults** SQL_NO_DATA zurück. Bei einigen Treibern sind Ausgabeparameter und Rückgabewerte erst verfügbar, wenn alle Resultsets und Zeilenanzahlen verarbeitet wurden. Für solche Treiber werden Ausgabeparameter und Rückgabewerte verfügbar, wenn **SQLMoreResults** SQL_NO_DATA zurückgibt.  
  
 Alle Bindungen, die für das vorherige Resultset festgelegt wurden, bleiben weiterhin gültig. Wenn die Spaltenstrukturen für dieses Resultset unterschiedlich sind, kann das Aufrufen von **SQLFetch** oder **SQLFetchScroll** zu einem Fehler oder Abschneiden führen. Um dies zu verhindern, muss die Anwendung **SQLBindCol** aufrufen, um die Stellanforderungen entsprechend explizit neu zu binden (oder dies durch Festlegen von Deskriptorfeldern) zu tun. Alternativ kann die Anwendung **SQLFreeStmt** mit der *Option* der SQL_UNBIND aufrufen, um die Bindung aller Spaltenpuffer aufzukleben.  
  
 Die Werte von Anweisungsattributen, z. B. Cursortyp, Cursorparallelität, Keysetgröße oder maximale Länge, können sich ändern, wenn die Anwendung durch den Batch durch Aufrufe von **SQLMoreResults**navigiert. In diesem Fall gibt **SQLMoreResults** SQL_SUCCESS_WITH_INFO und SQLSTATE 01S02 (Optionswert wurde geändert) zurück.  
  
 Wenn Sie **SQLCloseCursor**oder **SQLFreeStmt** mit der *Option* SQL_CLOSE aufrufen, werden alle Resultsets und Zeilenanzahlen verworfen, die als Ergebnis der Ausführung des Batches verfügbar waren. Das Anweisungshandle gibt entweder den zugewiesenen oder vorbereiteten Zustand zurück. Aufrufen von **SQLCancel** zum Abbrechen einer asynchron ausgeführten Funktion, wenn ein Batch ausgeführt wurde und sich das Anweisungshandle im ausgeführten, cursorpositionierten oder asynchronen Zustand befindet, ergeben sich alle Ergebnissätze und Zeilenanzahlen, die durch den verworfenen Batch generiert werden, wenn der Abbruchaufruf erfolgreich war. Die Anweisung kehrt dann in den vorbereiteten oder zugewiesenen Zustand zurück.  
  
 Wenn ein Batch von Anweisungen oder eine Prozedur andere SQL-Anweisungen mit **SELECT-,** **UPDATE-,** **INSERT-** und **DELETE-Anweisungen** mischt, wirken sich diese anderen Anweisungen nicht auf **SQLMoreResults**aus.  
  
 Weitere Informationen finden Sie unter [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Wenn sich eine durchsuchte Aktualisierungs-, Einfüge- oder Löschanweisung in einem Batch von Anweisungen nicht auf Zeilen in der Datenquelle auswirkt, gibt **SQLMoreResults** SQL_SUCCESS zurück. Dies unterscheidet sich von der Abfrage einer durchsuchten Update-, Insert- oder Delete-Anweisung, die über **SQLExecDirect**, **SQLExecute**oder **SQLParamData**ausgeführt wird, die SQL_NO_DATA zurückgibt, wenn sie keine Zeilen in der Datenquelle beeinflusst. Wenn eine Anwendung **SQLRowCount** aufruft, um die Zeilenanzahl abzurufen, nachdem ein Aufruf von **SQLMoreResults** keine Zeilen betroffen hat, gibt **SQLRowCount** SQL_NO_DATA zurück.  
  
 Weitere Informationen zur gültigen Sequenzierung von Ergebnisverarbeitungsfunktionen finden Sie in [Anhang B: ODBC-Zustandsübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Weitere Informationen zu SQL_PARAM_DATA_AVAILABLE und gestreamten Ausgabeparametern finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Verfügbarkeit von Zeilenzählungen  
 Wenn ein Batch mehrere aufeinander folgende Zeilenzähl-generierungsanweisungen enthält, ist es möglich, dass diese Zeilenanzahlen in nur einer Zeilenanzahl zusammengefasst werden. Wenn ein Batch beispielsweise fünf Insert-Anweisungen enthält, können bestimmte Datenquellen fünf einzelne Zeilenanzahlen zurückgeben. Bestimmte andere Datenquellen geben nur eine Zeilenanzahl zurück, die die Summe der fünf einzelnen Zeilenzählungen darstellt.  
  
 Wenn ein Batch eine Kombination aus ergebnissatzgenerierenden und zeilenzahlenden Anweisungen enthält, sind zeilenzahlende Anweisungen möglicherweise überhaupt verfügbar. Das Verhalten des Treibers in Bezug auf die Verfügbarkeit von Zeilenanzahlen wird im SQL_BATCH_ROW_COUNT Informationstyp aufgezählt, der durch einen Aufruf von **SQLGetInfo**verfügbar ist. Angenommen, der Stapel enthält eine **SELECT**, gefolgt von zwei **INSERT**s und einem weiteren **SELECT**. Dann sind folgende Fälle möglich:  
  
-   Die Zeilenanzahl, die den beiden **INSERT-Anweisungen** entspricht, ist überhaupt nicht verfügbar. Beim ersten Aufruf von **SQLMoreResults** werden Sie auf dem Resultset der zweiten **SELECT-Anweisung** positioniert.  
  
-   Die Zeilenanzahl, die den beiden **INSERT-Anweisungen** entspricht, ist einzeln verfügbar. (Ein Aufruf von **SQLGetInfo** gibt das SQL_BRC_ROLLED_UP-Bit für den SQL_BATCH_ROW_COUNT-Informationstyp nicht zurück.) Beim ersten Aufruf von **SQLMoreResults** werden Sie auf der Zeilenanzahl des ersten **INSERT**positioniert, und der zweite Aufruf positioniert Sie auf der Zeilenanzahl des zweiten **INSERT**. Beim dritten Aufruf von **SQLMoreResults** werden Sie auf dem Resultset der zweiten **SELECT-Anweisung** positioniert.  
  
-   Die Zeilenanzahl, die den beiden **INSERTs** entspricht, wird in einer einzigen Zeilenanzahl zusammengefasst, die verfügbar ist. (Ein Aufruf von **SQLGetInfo** gibt das SQL_BRC_ROLLED_UP Bit für den SQL_BATCH_ROW_COUNT-Informationstyp zurück.) Beim ersten Aufruf von **SQLMoreResults** werden Sie auf der Anzahl der rollierenden Zeilen positioniert, und der zweite Aufruf von **SQLMoreResults** positioniert Sie auf dem Resultset des zweiten **SELECT**.  
  
 Bestimmte Treiber stellen Zeilenanzahlen nur für explizite Batches und nicht für gespeicherte Prozeduren zur Verfügung.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen einer einzelnen Zeile oder eines Datenblocks in einer vorwärtsgerichteten Richtung|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Abrufen eines Teils oder der gesamten Datenspalte|[SQLGetData-Funktion](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
