---
title: Sqlsetdebug-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b29879ff7635d6eb7d5a0f7489ff3994758d4a35
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299530"
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 Die **SQLSetDescRec** -Funktion legt mehrere Deskriptorfelder fest, die den Datentyp und den Puffer beeinflussen, die an eine Spalten-oder Parameterdaten gebunden sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetDescRec(  
      SQLHDESC      DescriptorHandle,  
      SQLSMALLINT   RecNumber,  
      SQLSMALLINT   Type,  
      SQLSMALLINT   SubType,  
      SQLLEN        Length,  
      SQLSMALLINT   Precision,  
      SQLSMALLINT   Scale,  
      SQLPOINTER    DataPtr,  
      SQLLEN *      StringLengthPtr,  
      SQLLEN *      IndicatorPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *DescriptorHandle*  
 Der Deskriptorhandle. Dabei darf es sich nicht um einen IRD-handle handeln.  
  
 *RecNumber*  
 Der Gibt den Deskriptordatensatz an, der die festzulegenden Felder enthält. Deskriptordatensätze werden von 0 nummeriert, wobei die Datensatznummer 0 der Lesezeichen-Datensatz ist. Dieses Argument muss größer oder gleich 0 sein. Wenn " *RecNumber* " größer als der Wert von "SQL_DESC_COUNT" ist, SQL_DESC_COUNTis auf den Wert von " *RecNumber*" geändert.  
  
 *Typ*  
 Der Der Wert, auf den das SQL_DESC_TYPE Feld für den Deskriptordatensatz festgelegt werden soll.  
  
 *Untertyp*  
 Der Bei Datensätzen, deren Typ SQL_DATETIME oder SQL_INTERVAL ist, ist dies der Wert, auf den das SQL_DESC_DATETIME_INTERVAL_CODE Feld festgelegt werden soll.  
  
 *Länge*  
 Der Der Wert, auf den das SQL_DESC_OCTET_LENGTH Feld für den Deskriptordatensatz festgelegt werden soll.  
  
 *Genauigkeit*  
 Der Der Wert, auf den das SQL_DESC_PRECISION Feld für den Deskriptordatensatz festgelegt werden soll.  
  
 *Skalieren*  
 Der Der Wert, auf den das SQL_DESC_SCALE Feld für den Deskriptordatensatz festgelegt werden soll.  
  
 *DataPtr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, auf den das SQL_DESC_DATA_PTR Feld für den Deskriptordatensatz festgelegt werden soll. *DataPtr* kann auf einen NULL-Zeiger festgelegt werden.  
  
 Das *DataPtr* -Argument kann auf einen NULL-Zeiger festgelegt werden, um das SQL_DESC_DATA_PTR Feld auf einen NULL-Zeiger festzulegen. Wenn das Handle im *Deskriptorhandle* -Argument einem ARD zugeordnet ist, wird die Bindung der Spalte dadurch nicht mehr gebunden.  
  
 *Stringlengthptr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, auf den das SQL_DESC_OCTET_LENGTH_PTR Feld für den Deskriptordatensatz festgelegt werden soll. *Stringlengthptr* kann auf einen NULL-Zeiger festgelegt werden, um das SQL_DESC_OCTET_LENGTH_PTR Feld auf einen NULL-Zeiger festzulegen.  
  
 *"Indikatorptr"*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, auf den das SQL_DESC_INDICATOR_PTR Feld für den Deskriptordatensatz festgelegt werden soll. " *Indikator orptr* " kann auf einen NULL-Zeiger festgelegt werden, um das SQL_DESC_INDICATOR_PTR Feld auf einen NULL-Zeiger festzulegen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetDescRec** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_DESC und einem *handle* von *descriptorhandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLSetDescRec** häufig zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger deskriptorindex.|Das *RecNumber* -Argument wurde auf 0 festgelegt, und das *Deskriptorhandle* verweist auf ein IPD-handle.<br /><br /> Das *RecNumber* -Argument war kleiner als 0 (null).<br /><br /> Das *RecNumber* -Argument war größer als die maximale Anzahl von Spalten oder Parametern, die von der Datenquelle unterstützt werden können, und das *Deskriptorhandle* -Argument war eine APD, IPD oder ARD.<br /><br /> Das *RecNumber* -Argument war gleich 0, und das *Deskriptorhandle* -Argument hat auf eine implizit zugeordnete APD verwiesen. (Dieser Fehler tritt nicht bei einem explizit zugewiesenen Anwendungs Deskriptor auf, da nicht bekannt ist, ob es sich bei einem explizit zugeordneten Anwendungs Deskriptor um eine APD oder einen ARD handelt, bis die Ausführungszeit erfolgt ist.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) das *Deskriptorhandle* wurde mit einem *StatementHandle* verknüpft, für das eine asynchron ausgeführte Funktion (nicht diese) aufgerufen wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen, dem das *Deskriptorhandle* zugeordnet und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das dem *Deskriptorhandle*zugeordnet ist. Diese aynchronous-Funktion wurde noch ausgeführt, als die **sqlsetdebug** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungs Handles aufgerufen, die dem *Deskriptorhandle* zugeordnet sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY016|Ein Implementierungs Zeilen Deskriptor kann nicht geändert werden.|Das *Deskriptorhandle* -Argument wurde einem IRD zugeordnet.|  
|HY021|Inkonsistente Deskriptorinformationen|Das *typanfeld* oder ein beliebiges anderes Feld, das dem SQL_DESC_TYPE Feld im Deskriptor zugeordnet ist, war ungültig oder nicht konsistent.<br /><br /> Während einer Konsistenzprüfung überprüfte Deskriptorinformationen waren nicht konsistent. (Weitere Informationen finden Sie unter "Konsistenzprüfungen" weiter unten in diesem Abschnitt.)|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) der Treiber war ein ODBC *2. x* -Treiber, der Deskriptor war eine ARD, das *ColumnNumber* -Argument wurde auf 0 festgelegt, und der für das Argument *BufferLength* angegebene Wert war nicht gleich 4.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *Deskriptorhandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **sqlsetdebug** aufrufen, um die folgenden Felder für eine einzelne Spalte oder einen Parameter festzulegen:  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze, deren Typ SQL_DATETIME oder SQL_INTERVAL ist)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Wenn ein **SQLSetDescRec** -Befehl fehlschlägt, ist der Inhalt des deskriptordaten Satzes, der durch das *RecNumber* -Argument identifiziert wird, nicht definiert.  
  
 Wenn Sie eine Spalte oder einen Parameter binden, können Sie mithilfe von **SQLSetDescRec** mehrere Felder ändern, die sich auf die Bindung auswirken, ohne **SQLBindCol** oder **SQLBindParameter** aufzurufen oder mehrere Aufrufe von **SQLSetDescField**durchführen zu müssen. **Sqlsetdebug** kann Felder für einen Deskriptor festlegen, der derzeit keiner-Anweisung zugeordnet ist. Beachten Sie, dass **SQLBindParameter** mehr Felder als **sqlsetdebug**festlegt, Felder sowohl für eine APD als auch für eine IPD in einem einzigen-Befehl festlegen kann und kein Deskriptorhandle erfordert.  
  
> [!NOTE]  
>  Das Anweisungs Attribut SQL_ATTR_USE_BOOKMARKS sollte immer vor dem Aufrufen von **SQLSetDescRec** mit dem *RecNumber* -Argument 0 festgelegt werden, um Lesezeichen Felder festzulegen. Dies ist zwar nicht zwingend erforderlich, wird jedoch dringend empfohlen.  
  
## <a name="consistency-checks"></a>Konsistenzprüfungen  
 Vom Treiber wird automatisch eine Konsistenzprüfung durchgeführt, wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld eines APD-, ARD-oder IPD-Werts festlegt. Wenn eines der Felder nicht mit anderen Feldern konsistent ist, gibt **SQLSetDescRec** SQLSTATE HY021 (inkonsistente Deskriptorinformationen) zurück.  
  
 Wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld von APD, ARD oder IPD festlegt, überprüft der Treiber, ob der Wert des SQL_DESC_TYPE Felds und die für dieses SQL_DESC_TYPE Feld anwendbaren Werte gültig und konsistent sind. Diese Überprüfung wird immer ausgeführt, wenn **SQLBindParameter** oder **SQLBindCol** aufgerufen wird oder wenn **sqlsetdebug** für eine APD, eine ARD oder eine IPD aufgerufen wird. Diese Konsistenzprüfung schließt die folgenden Überprüfungen für Deskriptorfelder ein:  
  
-   Das SQL_DESC_TYPE Feld muss einer der gültigen ODBC-C-oder SQL-Typen oder ein Treiber spezifischer SQL-Typ sein. Das SQL_DESC_CONCISE_TYPE Feld muss einer der gültigen ODBC-c-oder SQL-Typen oder ein Treiber spezifischer c-oder SQL-Typ sein, einschließlich der präzisen DateTime-und Interval-Typen.  
  
-   Wenn das Feld SQL_DESC_TYPE Datensatz SQL_DATETIME oder SQL_INTERVAL ist, muss das SQL_DESC_DATETIME_INTERVAL_CODE Feld einer der gültigen DateTime-oder Interval-Codes sein. (Weitere Informationen finden Sie in der Beschreibung des SQL_DESC_DATETIME_INTERVAL_CODE Felds in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Wenn das SQL_DESC_TYPE Feld einen numerischen Typ anzeigt, werden die Felder SQL_DESC_PRECISION und SQL_DESC_SCALE als gültig überprüft.  
  
-   Wenn das SQL_DESC_CONCISE_TYPE Feld ein Zeit-oder Zeitstempel-Datentyp, ein Intervalltyp mit einer Sekunden Komponente oder einer der Intervall Datentypen mit einer Zeitkomponente ist, wird das SQL_DESC_PRECISION Feld als gültige Sekunden Genauigkeit überprüft.  
  
-   Wenn die SQL_DESC_CONCISE_TYPE ein Intervall Datentyp ist, wird das SQL_DESC_DATETIME_INTERVAL_PRECISION Feld als gültiger Wert für die Genauigkeit von Intervallen überprüft.  
  
 Das SQL_DESC_DATA_PTR-Feld einer IPD wird normalerweise nicht festgelegt. Allerdings kann eine Anwendung dies tun, um eine Konsistenzprüfung von IPD-Feldern zu erzwingen. Eine Konsistenzprüfung kann nicht für einen IRD ausgeführt werden. Der Wert, auf den das SQL_DESC_DATA_PTR-Feld der IPD festgelegt ist, wird nicht tatsächlich gespeichert und kann nicht durch einen **SQLGetDescField** -oder **SQLGetDescRec**-Befehl abgerufen werden. die Einstellung wird nur zum Erzwingen der Konsistenzprüfung durchgeführt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Binden einer Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Parameters|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Ein einzelnes Deskriptorfeld wird abgerufen.|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Mehrere Deskriptorfelder werden abgerufen.|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen von einzelnen Deskriptorfeldern|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
