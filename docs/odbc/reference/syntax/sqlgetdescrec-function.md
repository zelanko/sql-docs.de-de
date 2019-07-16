---
title: SQLGetDescRec-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103789"
---
# <a name="sqlgetdescrec-function"></a>SQLGetDescRec-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDescRec** gibt den aktuellen Einstellungen oder Werten aus mehreren Feldern, die von einem anwendungsparameterdeskriptor-Datensatz zurück. Die zurückgegebenen Felder beschrieben, die Namen, Datentyp und Speicherung von Daten für Spalte oder des Parameters.  
  
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
 *DescriptorHandle*  
 [Eingabe] Deskriptorhandles.  
  
 *RecNumber*  
 [Eingabe] Gibt an, die von dem die Anwendung Informationen sucht anwendungsparameterdeskriptor-Datensatz. Deskriptordatensätze werden von 1, mit der Datensatznummer lesezeichendatensatzes wird 0 nummeriert. Die *RecNumber* Argument muss kleiner oder gleich dem Wert des SQL_DESC_COUNT sein. Wenn *RecNumber* ist kleiner als oder gleich SQL_DESC_COUNT die Zeile enthält jedoch keine Daten für eine Spalte oder Parameter, einen Aufruf von **SQLGetDescRec** gibt die Standardwerte der Felder zurück. (Weitere Informationen finden Sie unter "Initialisierung der Deskriptorfelder" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *Name*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in die SQL_DESC_NAME-Felds für den anwendungsparameterdeskriptor-Datensatz zurückgegeben werden sollen.  
  
 Wenn *Namen* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *Namen*.  
  
 *BufferLength*  
 [Eingabe] Länge der **Namen* Puffers in Zeichen.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem zum Zurückgeben der Anzahl von Zeichen von Daten, die in Zurückgeben der \* *Namen* Puffer, der Null-Terminierungszeichen ausschließen. Die Anzahl von Zeichen war größer als oder gleich *Pufferlänge*, die Daten in \* *Name* auf abgeschnitten *Pufferlänge* abzüglich der Länge des ein NULL-Terminierungszeichen, und Null-terminiert ist vom Treiber.  
  
 *TypePtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem der Wert, der das SQL_DESC_TYPE-Feld für den anwendungsparameterdeskriptor-Datensatz zurückgegeben.  
  
 *SubTypePtr*  
 [Ausgabe] Für Datensätze vom Typ SQL_DATETIME oder SQL_INTERVAL hat, ist dies ein Zeiger auf einen Puffer, in dem den Wert des Felds SQL_DESC_DATETIME_INTERVAL_CODE zurückgegeben.  
  
 *LengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem den Wert des Felds "SQL_DESC_OCTET_LENGTH" für den anwendungsparameterdeskriptor-Datensatz zurückgegeben.  
  
 *PrecisionPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem den Wert des Felds "SQL_DESC_PRECISION" für den anwendungsparameterdeskriptor-Datensatz zurückgegeben.  
  
 *ScalePtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem den Wert des Felds "SQL_DESC_SCALE" für den anwendungsparameterdeskriptor-Datensatz zurückgegeben.  
  
 *NullablePtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem den Wert des Felds "SQL_DESC_NULLABLE" für den anwendungsparameterdeskriptor-Datensatz zurückgegeben.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA zurückgibt oder SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA zurückgegeben wird, wenn *RecNumber* ist größer als die aktuelle Anzahl der deskriptordatensätze.  
  
 SQL_NO_DATA zurückgegeben wird, wenn *DescriptorHandle* ist ein IRD-Handle und die Anweisung befindet sich im Zustand vorbereitete oder ausgeführte. es wurde jedoch keine geöffneten Cursor zugeordnet.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetDescRec** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_DESC und *behandeln* von *DescriptorHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die in der Regel vom **SQLGetDescRec** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *Namen* nicht groß genug war, um das gesamte Deskriptorfeld zurückzugeben. Aus diesem Grund wurde das Feld abgeschnitten. Die Länge des Felds den ungekürzten Deskriptor wird zurückgegeben, **StringLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|Die *FieldIdentifier* Argument wurde ein Datensatzfeld, der *RecNumber* -Argument wurde auf 0 (null) festgelegt und die *DescriptorHandle* Argument war ein IPD-Handle.<br /><br /> (DM) die *RecNumber* Argument auf 0 festgelegt wurde, und das SQL_ATTR_USE_BOOKMARKS-Anweisungsattribut auf SQL_UB_OFF, festgelegt wurde und die *DescriptorHandle* Argument war ein IRD-Handle.<br /><br /> Die *RecNumber* Argument war kleiner als 0.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zum Belegen des Speichers, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich ist.|  
|HY007|Zugeordnete Anweisung ist nicht vorbereitet.|*DescriptorHandle* wurde ein IRD zugeordnet, und das Handle für die zugeordnete Anweisung wurde nicht im Status vorbereitet oder ausgeführt.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) *DescriptorHandle* zugeordnet wurde eine *StatementHandle* für den eine asynchron ausgeführte Funktion (diese keiner) aufgerufen wurde, und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) *DescriptorHandle* zugeordnet wurde eine *StatementHandle* für die **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, oder **SQLSetPos** war aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *DescriptorHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn **SQLGetDescRec** aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet *DescriptorHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Kann eine Anwendung aufrufen **SQLGetDescRec** zum Abrufen der Werte für die folgenden deskriptorfelder für eine einzelne Spalte oder Parameter:  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze vom Typ SQL_DATETIME oder SQL_INTERVAL hat)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec** ruft nicht die Werte für die Felder ab.  
  
 Eine Anwendung kann zu verhindern, dass die Rückgabe von der Einstellung eines durch das Argument, das entspricht dem Feld einen null-Zeiger festlegen.  
  
 Wenn eine Anwendung ruft **SQLGetDescRec** zum Abrufen des Werts eines Felds, das für einen bestimmten Deskriptortyp undefiniert ist die Funktion gibt SQL_SUCCESS zurück, aber der Wert zurückgegeben, für das Feld ist nicht definiert. Zum Beispiel der Aufruf **SQLGetDescRec** für das Feld SQL_DESC_NAME oder SQL_DESC_NULLABLE eines APD oder ARD SQL_SUCCESS jedoch einen nicht definierten Wert für das Feld zurück.  
  
 Wenn eine Anwendung ruft **SQLGetDescRec** zum Abrufen des Werts eines Felds aus, für einen bestimmten Deskriptortyp definiert ist, aber hat keinen Standardwert und wurde noch nicht festgelegt, die Funktion gibt SQL_SUCCESS zurück, aber der Wert zurückgegeben, für die das Feld ist nicht definiert. Weitere Informationen finden Sie unter "Initialisierung der Deskriptorfelder" in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Die Werte der Felder können auch einzeln von einem Aufruf abgerufen werden **SQLGetDescField**. Eine Beschreibung der Felder in ein Deskriptor Header oder einen Datensatz, finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu den sicherheitsbeschreibungen, finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden eine Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ein Parameter gebunden|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abrufen von einem Beschreibungsfeld|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Festlegen von mehreren deskriptorfeldern|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
