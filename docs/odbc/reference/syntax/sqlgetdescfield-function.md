---
title: SQLGetDescField-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescField
helpviewer_keywords:
- SQLGetDescField function [ODBC]
ms.assetid: f09ff660-1e4a-4370-be85-90d4da0487d3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89972d7f36b436868cc8e243b03827f095b90492
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285475"
---
# <a name="sqlgetdescfield-function"></a>SQLGetDescField-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDescField** gibt die aktuelle Einstellung oder den Wert eines einzelnen Felds eines deskriptordaten Satzes zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *DescriptorHandle*  
 Der Deskriptorhandle.  
  
 *RecNumber*  
 Der Gibt den Deskriptordatensatz an, von dem die Anwendung Informationen sucht. Deskriptordatensätze werden von 0 nummeriert, wobei die Datensatznummer 0 der Lesezeichen-Datensatz ist. Wenn das *fieldidentifier* -Argument ein Header Feld angibt, wird " *RecNumber* " ignoriert. Wenn " *RecNumber* " kleiner oder gleich SQL_DESC_COUNT ist, die Zeile jedoch keine Daten für eine Spalte oder einen Parameter enthält, gibt ein **SQLGetDescField** -Befehl die Standardwerte der Felder zurück. (Weitere Informationen finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *FieldIdentifier*  
 Der Gibt das Feld des Deskriptors an, dessen Wert zurückgegeben werden soll. Weitere Informationen finden Sie im Abschnitt "*fieldidentifier* -Argument" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 *ValuePtr*  
 Ausgeben Zeiger auf einen Puffer, in den die Deskriptorinformationen zurückgegeben werden sollen. Der Datentyp hängt vom Wert von *fieldidentifier*ab.  
  
 Wenn *ValuePtr* ein ganzzahliger Typ ist, sollten Anwendungen einen Puffer von SQLULEN verwenden und den Wert auf 0 initialisieren, bevor Sie diese Funktion aufrufen, da einige Treiber möglicherweise nur den unteren 32-Bit-oder 16-Bit-Wert eines Puffers schreiben und das Bit höherer Ordnung unverändert lassen.  
  
 Wenn *ValuePtr* den Wert NULL hat, gibt *stringlengthptr* weiterhin die Gesamtzahl der Bytes (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten) zurück, die im Puffer zurückgegeben werden können, auf den *ValuePtr*zeigt.  
  
 *Pufferlänge*  
 Der Wenn *fieldidentifier* ein ODBC-definiertes Feld ist und *ValuePtr* auf eine Zeichenfolge oder einen binären Puffer verweist, sollte dieses Argument der Länge von \* *ValuePtr*entsprechen. Wenn *fieldidentifier* ein ODBC-definiertes Feld und \* *ValuePtr* eine ganze Zahl ist, wird *BufferLength* ignoriert. Wenn der Wert in * \*ValuePtr* von einem Unicode-Datentyp ist (beim Aufrufen von **sqlgetdescfieldw**), muss das *BufferLength* -Argument eine gerade Zahl sein.  
  
 Wenn *fieldidentifier* ein Treiber definiertes Feld ist, gibt die Anwendung die Art des Felds für den Treiber-Manager an, indem das *BufferLength* -Argument festgelegt wird. *BufferLength* kann die folgenden Werte aufweisen:  
  
-   Wenn * \*ValuePtr* ein Zeiger auf eine Zeichenfolge ist, entspricht *BufferLength* der Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen binären Puffer ist, platziert die Anwendung das Ergebnis des Makros SQL_LEN_BINARY_ATTR (*length*) in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER.  
  
-   Wenn * \*ValuePtr* einen Datentyp mit fester Länge enthält, ist *BufferLength* entweder SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT.  
  
 *Stringlengthptr*  
 Ausgeben Ein Zeiger auf den Puffer, in dem die Gesamtzahl der Bytes (ausgenommen der Anzahl der Bytes, die für das NULL-Beendigungs Zeichen erforderlich sind) zurückgegeben werden soll, die in **ValuePtr*zurückgegeben werden können.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA oder SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA wird zurückgegeben, wenn " *RecNumber* " größer als die aktuelle Anzahl der Deskriptordatensätze ist.  
  
 SQL_NO_DATA wird zurückgegeben, wenn *descriptorhandle* ein IRD-Handle ist und die Anweisung den Zustand "vorbereitet" oder "ausgeführt" aufweist, dem aber kein offener Cursor zugeordnet ist.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetDescField** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLGetDescField** häufig zurückgegeben und im Kontext dieser Funktion erläutert werden. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der Puffer \* *ValuePtr* war nicht groß genug, um das gesamte Deskriptorfeld zurückzugeben, sodass das Feld abgeschnitten wurde. Die Länge des nicht abgeschnittene deskriptorfelds wird in "**stringlengthptr*" zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger deskriptorindex.|(DM) das *RecNumber* -Argument war gleich 0, das SQL_ATTR_USE_BOOKMARK-Anweisungs Attribut war SQL_UB_OFF, und das *Deskriptorhandle* -Argument war ein IRD-handle. (Dieser Fehler kann nur für einen explizit zugewiesenen Deskriptor zurückgegeben werden, wenn der Deskriptor einem Anweisungs Handle zugeordnet ist.)<br /><br /> Das *fieldidentifier* -Argument war ein Daten Satz Feld, das " *RecNumber* "-Argument war "0", und das *Deskriptorhandle* -Argument war ein IPD-handle.<br /><br /> Das *RecNumber* -Argument war kleiner als 0 (null).|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte den erforderlichen Arbeitsspeicher nicht zuordnen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY007|Die zugehörige Anweisung ist nicht vorbereitet.|*Descriptorhandle* wurde einem *StatementHandle* als IRD zugeordnet, und das zugehörige Anweisungs Handle wurde nicht vorbereitet oder ausgeführt.|  
|HY010|Funktions Sequenz Fehler|(DM) *descriptorhandle* wurde einem *StatementHandle* zugeordnet, für das eine asynchron ausgeführte Funktion (nicht diese) aufgerufen wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) *descriptorhandle* wurde einem *StatementHandle* zugeordnet, für das **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** aufgerufen und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das dem *Deskriptorhandle*zugeordnet ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLGetDescField** -Funktion aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY021|Inkonsistente Deskriptorinformationen|Die Felder "SQL_DESC_TYPE" und "SQL_DESC_DATETIME_INTERVAL_CODE" bilden keinen gültigen ODBC-SQL-Typ, einen gültigen treiberspezifischen SQL-Typ (für IPDS) oder einen gültigen ODBC-C-Typ (für APDS oder ARDs).|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) * \*ValuePtr* war eine Zeichenfolge, und *BufferLength* war kleiner als 0 (null).|  
|HY091|Ungültiger Deskriptorfeldbezeichner.|*Fieldidentifier* war kein ODBC-definiertes Feld und kein von der Implementierung definierter Wert.<br /><br /> *Fieldidentifier* war für das *Deskriptorhandle*nicht definiert.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *Deskriptorhandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLGetDescField** aufrufen, um den Wert eines einzelnen Felds eines deskriptordaten Satzes zurückzugeben. Ein **SQLGetDescField** -Befehl kann die Einstellung eines beliebigen Felds in einem beliebigen Deskriptortyp, einschließlich Header Felder, Datensatz-Felder und Lesezeichen Felder, zurückgeben. Eine Anwendung kann die Einstellungen mehrerer Felder in der gleichen oder in anderen Deskriptoren in beliebiger Reihenfolge abrufen, indem wiederholte Aufrufe von **SQLGetDescField**durchführen werden. **SQLGetDescField** kann auch aufgerufen werden, um Treiber definierte Deskriptorfelder zurückzugeben.  
  
 Aus Leistungsgründen sollte eine Anwendung **SQLGetDescField** nicht für einen IRD aufrufen, bevor eine-Anweisung ausgeführt wird.  
  
 Die Einstellungen mehrerer Felder, die den Namen, den Datentyp und die Speicherung von Spalten-oder Parameterdaten beschreiben, können auch in einem einzelnen **SQLGetDescRec**-Befehl abgerufen werden. **SQLGetStmtAttr** kann aufgerufen werden, um die Einstellung eines einzelnen Felds im deskriptorheader zurückzugeben, bei dem es sich auch um ein Anweisungs Attribut handelt. **SQLColAttribute**, **SQLDescribeCol**und **SQLDescribeParam** geben Daten Satz-oder Lesezeichen Felder zurück.  
  
 Wenn eine Anwendung **SQLGetDescField** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp nicht definiert ist, gibt die Funktion SQL_SUCCESS zurück, der für das Feld zurückgegebene Wert ist jedoch nicht definiert. Beispielsweise gibt das Aufrufen von **SQLGetDescField** für das SQL_DESC_NAME oder SQL_DESC_NULLABLE Feld eines APD oder einer ARD SQL_SUCCESS, aber einen nicht definierten Wert für das Feld zurück.  
  
 Wenn eine Anwendung **SQLGetDescField** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp definiert ist, aber keinen Standardwert hat und noch nicht festgelegt wurde, gibt die Funktion SQL_SUCCESS zurück, aber der für das Feld zurückgegebene Wert ist nicht definiert. Weitere Informationen zur Initialisierung von Deskriptorfeldern und Beschreibungen der Felder finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Mehrere Deskriptorfelder werden abgerufen.|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen deskriptorfelds|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
