---
title: SQLGetDescField-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285475"
---
# <a name="sqlgetdescfield-function"></a>SQLGetDescField-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDescField** gibt die aktuelle Einstellung oder den Aktuellen Wert eines einzelnen Felds eines Deskriptordatensatzes zurück.  
  
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
 [Eingabe] Deskriptor-Handle.  
  
 *RecNumber*  
 [Eingabe] Gibt den Deskriptordatensatz an, aus dem die Anwendung Informationen sucht. Deskriptordatensätze werden von 0 nummeriert, wobei Datensatznummer 0 der Lesezeichendatensatz ist. Wenn das *FieldIdentifier-Argument* ein Headerfeld angibt, wird *RecNumber* ignoriert. Wenn *RecNumber* kleiner oder gleich SQL_DESC_COUNT ist, die Zeile jedoch keine Daten für eine Spalte oder einen Parameter enthält, gibt ein Aufruf von **SQLGetDescField** die Standardwerte der Felder zurück. (Weitere Informationen finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *FieldIdentifier*  
 [Eingabe] Gibt das Feld des Deskriptors an, dessen Wert zurückgegeben werden soll. Weitere Informationen finden Sie im Abschnitt "*FieldIdentifier* Argument" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 *ValuePtr*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Deskriptorinformationen zurückgegeben werden sollen. Der Datentyp hängt vom Wert von *FieldIdentifier ab.*  
  
 Wenn *ValuePtr* ganzzahliger Typ ist, sollten Anwendungen einen Puffer von SQLULEN verwenden und den Wert auf 0 initialisieren, bevor sie diese Funktion aufrufen, da einige Treiber möglicherweise nur das niedrigere 32-Bit- oder 16-Bit-Bit eines Puffers schreiben und das Bit höherer Ordnung unverändert lassen.  
  
 Wenn *ValuePtr* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten) zurück, auf die im Puffer von *ValuePtr*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Wenn *FieldIdentifier* ein ODBC-definiertes Feld ist und *ValuePtr* auf eine Zeichenfolge oder \*einen Binärpuffer verweist, sollte dieses Argument die Länge von *ValuePtr*sein. Wenn *FieldIdentifier* ein ODBC-definiertes Feld und \* *ValuePtr* eine ganze Zahl ist, wird *BufferLength* ignoriert. Wenn der Wert in * \*ValuePtr* von einem Unicode-Datentyp ist (beim Aufrufen von **SQLGetDescFieldW**), muss das *BufferLength-Argument* eine gerade Zahl sein.  
  
 Wenn *FieldIdentifier* ein vom Treiber definiertes Feld ist, gibt die Anwendung die Art des Felds für den Treiber-Manager an, indem das *Argument BufferLength* festgelegt wird. *BufferLength* kann die folgenden Werte haben:  
  
-   Wenn * \*ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *BufferLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des Makros*SQL_LEN_BINARY_ATTR(Länge*) in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binärzeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn * \*ValuePtr* einen Datentyp fester Länge enthält, wird *BufferLength* entweder SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf den Puffer, in dem die Gesamtzahl der Bytes zurückgegeben werden soll (mit Ausnahme der Anzahl der Bytes, die für das Null-Beendigungszeichen erforderlich sind), die in **ValuePtr*zurückgegeben werden können.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA oder SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA wird zurückgegeben, wenn *RecNumber* größer als die aktuelle Anzahl von Deskriptordatensätzen ist.  
  
 SQL_NO_DATA wird zurückgegeben, wenn *DescriptorHandle* ein IRD-Handle ist und sich die Anweisung im vorbereiteten oder ausgeführten Zustand befindet, ihm jedoch kein offener Cursor zugeordnet war.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetDescField** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLGetDescField** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *ValuePtr* war nicht groß genug, um das gesamte Deskriptorfeld zurückzugeben, sodass das Feld abgeschnitten wurde. Die Länge des nicht abgeschnittenen Deskriptorfelds wird in **StringLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|(DM) Das *RecNumber-Argument* war gleich 0, das SQL_ATTR_USE_BOOKMARK-Anweisungsattribut wurde SQL_UB_OFF, und das *DescriptorHandle-Argument* war ein IRD-Handle. (Dieser Fehler kann für einen explizit zugewiesenen Deskriptor nur zurückgegeben werden, wenn der Deskriptor einem Anweisungshandle zugeordnet ist.)<br /><br /> Das *FieldIdentifier-Argument* war ein Datensatzfeld, das *RecNumber-Argument* war 0, und das *DescriptorHandle-Argument* war ein IPD-Handle.<br /><br /> Das *RecNumber-Argument* war kleiner als 0.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den für die Unterstützung der Ausführung oder den Abschluss der Funktion erforderlichen Speicher nicht zuweisen.|  
|HY007|Zugehörige Anweisung ist nicht vorbereitet|*DescriptorHandle* wurde einem *StatementHandle* als IRD zugeordnet, und das zugeordnete Anweisungshandle wurde nicht vorbereitet oder ausgeführt.|  
|HY010|Funktionssequenzfehler|(DM) *DescriptorHandle* wurde einem *StatementHandle* zugeordnet, für den eine asynchron ausführende Funktion (nicht diese) aufgerufen wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) *DescriptorHandle* wurde einem *StatementHandle* zugeordnet, für das **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** aufgerufen und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Für das Verbindungshandle, das dem *DescriptorHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLGetDescField-Funktion** aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY021|Inkonsistente Deskriptorinformationen|Die Felder SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE bilden keinen gültigen ODBC-SQL-Typ, keinen gültigen treiberspezifischen SQL-Typ (für IPDs) oder einen gültigen ODBC C-Typ (für APDs oder ARDs).|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) * \*ValuePtr* war eine Zeichenfolge, und *BufferLength* war kleiner als Null.|  
|HY091|Ungültiger Deskriptorfeldbezeichner|*FieldIdentifier* war kein ODBC-definiertes Feld und kein implementierungsdefinierter Wert.<br /><br /> *FieldIdentifier* war für *descriptorHandle*nicht definiert.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der treiber, der dem *DescriptorHandle* zugeordnet ist, unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLGetDescField** aufrufen, um den Wert eines einzelnen Felds eines Deskriptordatensatzes zurückzugeben. Ein Aufruf von **SQLGetDescField** kann die Einstellung eines beliebigen Felds in einem beliebigen Deskriptortyp zurückgeben, einschließlich Kopfzeilenfeldern, Datensatzfeldern und Lesezeichenfeldern. Eine Anwendung kann die Einstellungen mehrerer Felder in derselben oder unterschiedlichen Deskriptoren in beliebiger Reihenfolge abrufen, indem sie wiederholte Aufrufe von **SQLGetDescField**ausruft. **SQLGetDescField** kann auch aufgerufen werden, um treiberdefinierte Deskriptorfelder zurückzugeben.  
  
 Aus Leistungsgründen sollte eine Anwendung **SQLGetDescField** für eine IRD nicht aufrufen, bevor eine Anweisung ausgeführt wird.  
  
 Die Einstellungen mehrerer Felder, die den Namen, den Datentyp und den Speicher von Spalten- oder Parameterdaten beschreiben, können auch in einem einzigen Aufruf von **SQLGetDescRec**abgerufen werden. **SQLGetStmtAttr** kann aufgerufen werden, um die Einstellung eines einzelnen Felds im Deskriptorheader zurückzugeben, der auch ein Anweisungsattribut ist. **SQLColAttribute**, **SQLDescribeCol**und **SQLDescribeParam** geben Datensatz- oder Lesezeichenfelder zurück.  
  
 Wenn eine Anwendung **SQLGetDescField** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp nicht definiert ist, gibt die Funktion SQL_SUCCESS zurück, aber der für das Feld zurückgegebene Wert ist nicht definiert. Wenn Sie z. B. **SQLGetDescField** für die SQL_DESC_NAME oder SQL_DESC_NULLABLE Feld einer APD oder ARD aufrufen, wird SQL_SUCCESS, sondern ein nicht definierter Wert für das Feld zurückgegeben.  
  
 Wenn eine Anwendung **SQLGetDescField** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp definiert ist, aber keinen Standardwert hat und noch nicht festgelegt wurde, gibt die Funktion SQL_SUCCESS zurück, aber der für das Feld zurückgegebene Wert ist nicht definiert. Weitere Informationen zur Initialisierung von Deskriptorfeldern und Beschreibungen der Felder finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen mehrerer Deskriptorfelder|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Deskriptorfelds|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
