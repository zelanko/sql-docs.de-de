---
title: Sqlgetdebug-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescRec
helpviewer_keywords:
- SQLGetDescRec function [ODBC]
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c27b16d8b72e289f66a051cb2710004f72309599
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103789"
---
# <a name="sqlgetdescrec-function"></a>SQLGetDescRec-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDescRec** gibt die aktuellen Einstellungen oder Werte mehrerer Felder eines deskriptordaten Satzes zurück. Die zurückgegebenen Felder beschreiben den Namen, den Datentyp und die Speicherung von Spalten-oder Parameterdaten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetDescRec(  
      SQLHDESC        DescriptorHandle,  
      SQLSMALLINT     RecNumber,  
      SQLCHAR *       Name,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLSMALLINT *   TypePtr,  
      SQLSMALLINT *   SubTypePtr,  
      SQLLEN *        LengthPtr,  
      SQLSMALLINT *   PrecisionPtr,  
      SQLSMALLINT *   ScalePtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *Deskriptorhandle*  
 Der Deskriptorhandle.  
  
 *RecNumber*  
 Der Gibt den Deskriptordatensatz an, von dem die Anwendung Informationen sucht. Deskriptordatensätze sind von 1 nummeriert, wobei die Datensatznummer 0 der Lesezeichen Daten Satz ist. Das Argument " *RecNumber* " muss kleiner als oder gleich dem Wert von "SQL_DESC_COUNT" sein. Wenn " *RecNumber* " kleiner oder gleich SQL_DESC_COUNT ist, die Zeile jedoch keine Daten für eine Spalte oder einen Parameter enthält, gibt ein **SQLGetDescRec** -Befehl die Standardwerte der Felder zurück. (Weitere Informationen finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *Name*  
 Ausgeben Ein Zeiger auf einen Puffer, in den das SQL_DESC_NAME Feld für den Deskriptordatensatz zurückgegeben werden soll.  
  
 Wenn *Name* den Wert NULL hat, gibt *stringlengthptr* weiterhin die Gesamtzahl der Zeichen zurück (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten), die im Puffer zurückgegeben werden können, auf den mit *Name*verwiesen wird.  
  
 *Pufferlänge*  
 Der Länge des *-*namens* Puffers in Zeichen.  
  
 *Stringlengthptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Anzahl der Daten zurückgegeben werden soll, die im \* *namens* Puffer zur Rückgabe verfügbar sind, ausgenommen das NULL-Beendigungs Zeichen. Wenn die Anzahl der Zeichen größer als oder gleich *BufferLength*war, werden die Daten im \* *Namen* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt und vom Treiber auf NULL-terminiert.  
  
 *Typeptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den der Wert des SQL_DESC_TYPE Felds für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *Subtypeptr*  
 Ausgeben Bei Datensätzen, deren Typ SQL_DATETIME oder SQL_INTERVAL ist, ist dies ein Zeiger auf einen Puffer, in dem der Wert des SQL_DESC_DATETIME_INTERVAL_CODE Felds zurückgegeben werden soll.  
  
 *Verlängert*  
 Ausgeben Ein Zeiger auf einen Puffer, in den der Wert des SQL_DESC_OCTET_LENGTH Felds für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *"Precisionptr"*  
 Ausgeben Ein Zeiger auf einen Puffer, in den der Wert des SQL_DESC_PRECISION Felds für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *Scaleptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den der Wert des SQL_DESC_SCALE Felds für den Deskriptordatensatz zurückgegeben werden soll.  
  
 *Nullableptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in den der Wert des SQL_DESC_NULLABLE Felds für den Deskriptordatensatz zurückgegeben werden soll.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA oder SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA wird zurückgegeben, wenn " *RecNumber* " größer als die aktuelle Anzahl der Deskriptordatensätze ist.  
  
 SQL_NO_DATA wird zurückgegeben, wenn *descriptorhandle* ein IRD-Handle ist und die Anweisung den Zustand "vorbereitet" oder "ausgeführt" aufweist, dem aber kein offener Cursor zugeordnet ist.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetDescRec** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Typ* SQL_HANDLE_DESC und einem *handle* von *descriptorhandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die normalerweise von **SQLGetDescRec** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Der Puffer \* *Name* war nicht groß genug, um das gesamte Deskriptorfeld zurückzugeben. Daher wurde das Feld abgeschnitten. Die Länge des nicht abgeschnittene deskriptorfelds wird in "**stringlengthptr*" zurückgegeben. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger deskriptorindex.|Das *fieldidentifier* -Argument war ein Daten Satz Feld, das *RecNumber* -Argument wurde auf 0 festgelegt, und das *Deskriptorhandle* -Argument war ein IPD-handle.<br /><br /> (DM) das *RecNumber* -Argument wurde auf 0 festgelegt, und das SQL_ATTR_USE_BOOKMARKS Statement-Attribut wurde auf SQL_UB_OFF festgelegt, und das *Deskriptorhandle* -Argument war ein IRD-handle.<br /><br /> Das *RecNumber* -Argument war kleiner als 0 (null).|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte den erforderlichen Arbeitsspeicher nicht zuordnen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY007|Die zugehörige Anweisung ist nicht vorbereitet.|*Descriptorhandle* wurde einem IRD zugeordnet, und das zugehörige Anweisungs Handle befand sich nicht im vorbereiteten oder ausgeführten Zustand.|  
|HY010|Funktions Sequenz Fehler|(DM) *descriptorhandle* wurde einem *StatementHandle* zugeordnet, für das eine asynchron ausgeführte Funktion (nicht diese) aufgerufen wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) *descriptorhandle* wurde einem *StatementHandle* zugeordnet, für das **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** aufgerufen und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das dem *Deskriptorhandle*zugeordnet ist. Diese asynchrone Funktion wurde noch ausgeführt, als " **sqlgetdebug** " aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der mit *descriptorhandle* verknüpfte Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **sqlgetdebug** aufrufen, um die Werte der folgenden Deskriptorfelder für eine einzelne Spalte oder einen Parameter abzurufen:  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze, deren Typ SQL_DATETIME oder SQL_INTERVAL ist)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **Sqlgetdebuc** Ruft die Werte für Header Felder nicht ab.  
  
 Eine Anwendung kann die Rückgabe der Einstellung eines Felds verhindern, indem das Argument, das dem Feld entspricht, einem NULL-Zeiger entsprechend festgelegt wird.  
  
 Wenn eine Anwendung **SQLGetDescRec** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp nicht definiert ist, gibt die Funktion SQL_SUCCESS zurück, der für das Feld zurückgegebene Wert ist jedoch nicht definiert. Beispielsweise gibt das Aufrufen von **SQLGetDescRec** für das SQL_DESC_NAME oder SQL_DESC_NULLABLE Feld eines APD oder einer ARD SQL_SUCCESS, aber einen nicht definierten Wert für das Feld zurück.  
  
 Wenn eine Anwendung **SQLGetDescRec** aufruft, um den Wert eines Felds abzurufen, das für einen bestimmten Deskriptortyp definiert ist, aber keinen Standardwert hat und noch nicht festgelegt wurde, gibt die Funktion SQL_SUCCESS zurück, der für das Feld zurückgegebene Wert ist jedoch nicht definiert. Weitere Informationen finden Sie unter "Initialisierung von Deskriptorfeldern" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Die Werte von Feldern können auch einzeln durch einen **SQLGetDescField**-Befehl abgerufen werden. Eine Beschreibung der Felder in einem deskriptorheader oder Datensatz finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden einer Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Parameters|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Erhalten eines deskriptorfelds|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
