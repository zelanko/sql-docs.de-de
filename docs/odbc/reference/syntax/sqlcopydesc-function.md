---
title: SQLCopyDesc-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e91febb4b5b94b5a7f9df62347b4db5edcecf975
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53202439"
---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO-92  
  
 **Zusammenfassung**  
 **SQLCopyDesc** kopiert Informationen der Sicherheitsbeschreibung aus einen Deskriptorhandle an einen anderen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *SourceDescHandle*  
 [Eingabe] Das Quellhandle-Deskriptor.  
  
 *TargetDescHandle*  
 [Eingabe] Ziel-Deskriptorhandle. Die *TargetDescHandle* -Argument kann es sich um ein Handle für einen Anwendungsdienst-Deskriptor oder einem IPD. *TargetDescHandle* kann nicht auf ein Handle für ein IRD festgelegt werden oder **SQLCopyDesc** SQLSTATE HY016 (ein Implementierungszeilendeskriptor kann nicht geändert werden) zurück.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCopyDesc** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_DESC und *behandeln* von *TargetDescHandle*. Wenn ein ungültiger *SourceDescHandle* übergeben wurde in den Aufruf SQL_INVALID_HANDLE zurückgegeben werden, aber keine SQLSTATE zurückgegeben werden. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLCopyDesc** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
 Wenn ein Fehler zurückgegeben wird, wird den Aufruf von **SQLCopyDesc** sofort abgebrochen wird, und die Inhalte der Felder in der *TargetDescHandle* Deskriptor sind nicht definiert.  
  
 Da **SQLCopyDesc** kann implementiert werden, durch den Aufruf **SQLGetDescField** und **SQLSetDescField**, **SQLCopyDesc** möglicherweise zurück Zurückgegebenes SQLSTATEs **SQLGetDescField** oder **SQLSetDescField**.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zum Belegen des Speichers zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY007|Zugeordnete Anweisung ist nicht vorbereitet.|*SourceDescHandle* wurde ein IRD zugeordnet, und das Handle für die zugeordnete Anweisung wurde nicht im Status vorbereitet oder ausgeführt.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) auf der Deskriptor behandeln *SourceDescHandle* oder *TargetDescHandle* zugeordnet wurde eine *StatementHandle* für die eine asynchrone (nicht-Funktion eine) wurde aufgerufen und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) auf der Deskriptor behandeln *SourceDescHandle* oder *TargetDescHandle* zugeordnet wurde eine *StatementHandle* für die **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** war aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *SourceDescHandle* oder *TargetDescHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLCopyDesc** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** für eines der zugeordneten Anweisungshandles aufgerufen wurde die *SourceDescHandle* oder *TargetDescHandle* und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY016|Ein Implementierungszeilendeskriptor kann nicht geändert werden.|*TargetDescHandle* wurde ein IRD zugeordnet.|  
|HY021|Inkonsistente deskriptorinformation|Die Informationen der Sicherheitsbeschreibung während einer konsistenzprüfung eingecheckt war nicht konsistent. Weitere Informationen finden Sie unter "Von Konsistenzprüfungen" in **SQLSetDescField**.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der Aufruf von **SQLCopyDesc** aufgefordert, einen Aufruf von **SQLSetDescField**, aber  *\*ValuePtr* war nicht gültig für die *FieldIdentifier* Arguments auf *TargetDescHandle*.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *SourceDescHandle* oder *TargetDescHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Ein Aufruf von **SQLCopyDesc** Kopien, die die Felder des Deskriptors Quelle zu, auf das Handle der Ziel-Deskriptor behandeln. Felder können nur für einen Anwendungsdienst-Deskriptor oder einem IPD, aber nicht für eine IRD kopiert werden. Felder können aus einer Anwendung oder einen Deskriptor Implementierung kopiert werden.  
  
 Felder können aus einer IRD kopiert werden, nur dann, wenn das Anweisungshandle im Status vorbereitet oder ausgeführt wird; andernfalls gibt die Funktion SQLSTATE HY007 (zugeordnete Anweisung ist nicht vorbereitet).  
  
 Felder können aus einem IPD kopiert werden, und zwar unabhängig davon, ob eine Anweisung vorbereitet wurde. Wenn eine SQL-Anweisung mit dynamischen Parametern vorbereitet wurde und die automatischer Auffüllung des IPD unterstützt und aktiviert ist, wird vom Treiber IPD aufgefüllt. Wenn **SQLCopyDesc** aufgerufen wird und die IPD als die *SourceDescHandle*, die aufgefüllten Felder beim Übertragungsvorgang kopiert werden. Wenn IPD vom Treiber nicht aufgefüllt ist, wird der Inhalt der Felder in IPD ursprünglich kopiert.  
  
 Alle Felder des Deskriptors, mit Ausnahme von SQL_DESC_ALLOC_TYPE (die angibt, ob die Deskriptorhandles, automatisch oder explizit zugeordnet wurde), werden kopiert, und zwar unabhängig davon, ob das Feld für den Deskriptor Ziel definiert ist. Kopierte Felder überschreiben die vorhandenen Felder.  
  
 Der Treiber alle deskriptorfelder kopiert, wenn die *SourceDescHandle* und *TargetDescHandle* Argumente gleichen Treibers zugeordnet sind, auch wenn die Treiber auf zwei verschiedenen Verbindungen werden oder Umgebungen. Wenn die *SourceDescHandle* und *TargetDescHandle* Argumente sind unterschiedliche Treiber zugeordnet, die der Treiber-Manager kopiert die ODBC-definierten Felder, kopiert jedoch keine treiberdefinierten Felder oder Felder werden nicht von ODBC für den Typ der Sicherheitsbeschreibung definiert.  
  
 Der Aufruf von **SQLCopyDesc** sofort abgebrochen wird, wenn ein Fehler auftritt.  
  
 Wenn das SQL_DESC_DATA_PTR-Feld kopiert wird, erfolgt eine konsistenzprüfung auf dem Ziel-Deskriptor. Wenn die konsistenzprüfung fehlschlägt, SQLSTATE HY021 (inkonsistente Deskriptorinformationen) wird zurückgegeben, und der Aufruf von **SQLCopyDesc** sofort abgebrochen wird. Weitere Informationen zu konsistenzprüfungen, finden Sie unter "Von Konsistenzprüfungen" in [SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Deskriptorhandles können über Verbindungen kopiert werden, auch wenn die Verbindungen in anderen Umgebungen sind. Wenn der Treiber-Manager erkennt, dass die Quelle und Ziel Deskriptor Handles nicht zu derselben Verbindung und die beiden Verbindungen gehören gehören, um Treiber zu trennen, implementiert **SQLCopyDesc** anhand von einem Feld-nach-Feld Kopieren mithilfe von **SQLGetDescField** und **SQLSetDescField**.  
  
 Wenn **SQLCopyDesc** aufgerufen wird und eine *SourceDescHandle* auf einen Treiber und ein *TargetDescHandle* auf einem anderen Treiber, die Fehlerwarteschlange von der  *SourceDescHandle* deaktiviert ist. Dies geschieht, weil **SQLCopyDesc** wird in diesem Fall durch Aufrufe von implementiert **SQLGetDescField** und **SQLSetDescField**.  
  
> [!NOTE]  
>  Eine Anwendung möglicherweise eine explizit zugeordneten Deskriptorhandles mit Zuordnen einer *StatementHandle*, anstatt Aufrufen **SQLCopyDesc** Felder aus einen Deskriptor auf einen anderen zu kopieren. Ein explizit zugewiesenen Deskriptor kann mit einem anderen verbunden werden *StatementHandle* auf dem gleichen *ConnectionHandle* durch Festlegen der SQL_ATTR_APP_ROW_DESC oder SQL_ATTR_APP_PARAM_DESC-Anweisung Attribut für das Handle des explizit zugewiesene Deskriptors. Wenn dies abgeschlossen ist, **SQLCopyDesc** muss nicht aufgerufen werden, um deskriptorfeldwerte aus einen Deskriptor auf einen anderen zu kopieren. Ein Deskriptorhandle kann nicht zugeordnet werden eine *StatementHandle* auf einem anderen *ConnectionHandle*, jedoch mit den Feldwerten des Deskriptors auf *StatementHandles*auf anderen *ConnectionHandles*, **SQLCopyDesc** aufgerufen werden muss.  
  
 Eine Beschreibung der Felder in ein Deskriptor Header oder einen Datensatz, finden Sie unter [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu den sicherheitsbeschreibungen, finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="copying-rows-between-tables"></a>Kopieren von Zeilen zwischen Tabellen  
 Eine Anwendung kann Daten aus einer Tabelle in eine andere kopieren, ohne Kopieren der Daten auf Anwendungsebene. Zu diesem Zweck bindet die Anwendung den gleichen Datenpuffer und die Informationen der Sicherheitsbeschreibung eine Anweisung, die die Daten abruft und die Anweisung, die die Daten in eine Kopie eingefügt. Dies kann erreicht werden, entweder indem Sie einen Anwendungsdienst-Deskriptor (Bindung einen explizit zugewiesenen Deskriptor als die ARD für eine Anweisung und in einer anderen APD) freigeben oder mit **SQLCopyDesc** , kopieren Sie die Bindungen zwischen der ARD und APD der beiden Anweisungen. Wenn Sie die Anweisungen für unterschiedliche Verbindungen sind **SQLCopyDesc** muss verwendet werden. Darüber hinaus **SQLCopyDesc** muss aufgerufen werden, um die Bindungen zwischen IRD und IPD der beiden Anweisungen zu kopieren. Beim Kopieren in Anweisungen für die gleiche Verbindung den Informationstyp SQL_ACTIVE_STATEMENTS vom Treiber bei einem Aufruf zurückgegebene **SQLGetInfo** muss größer sein als 1 für diesen Vorgang erfolgreich ausgeführt werden kann. (Dies ist nicht der Fall beim Kopieren von über Verbindungen.)  
  
### <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel werden Deskriptor Vorgänge verwendet, die Felder der Tabelle PartsSource in die Tabelle PartsCopy zu kopieren. Den Inhalt der Tabelle PartsSource werden abgerufen, in der Rowset-Puffer im *hstmt0*. Diese Werte werden als Parameter eine INSERT-Anweisung verwendet, auf *hstmt1* zum Auffüllen der Spalten der Tabelle PartsCopy. Die Felder des IRD von dazu *hstmt0* in die Felder des IPD der kopiert werden *hstmt1*, und die Felder der ARD von *hstmt0* werden in die Felder der APD von kopiert*hstmt1*. Verwendung **SQLSetDescField** , legen Sie IPDs-SQL_DESC_PARAMETER_TYPE-Attribut auf SQL_PARAM_INPUT, wenn Sie IRD-Feldern von einer Anweisung mit der Output-Parameter in IPD-Feldern kopieren, die Eingabeparameter werden müssen.  
  
```  
#define ROWS 100  
#define DESC_LEN 50  
#define SQL_SUCCEEDED(rc) (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)  
  
// Template for a row  
typedef struct {  
   SQLINTEGER   sPartID;  
   SQLINTEGER   cbPartID;  
   SQLUCHAR     szDescription[DESC_LENGTH];  
   SQLINTEGER   cbDescription;  
   REAL         sPrice;  
   SQLINTEGER   cbPrice;  
} PartsSource;  
  
PartsSource    rget[ROWS];          // rowset buffer  
SQLUSMALLINT   sts_ptr[ROWS];       // status pointer  
SQLHSTMT       hstmt0, hstmt1;  
SQLHDESC       hArd0, hIrd0, hApd1, hIpd1;  
  
// ARD and IRD of hstmt0  
SQLGetStmtAttr(hstmt0, SQL_ATTR_APP_ROW_DESC, &hArd0, 0, NULL);  
SQLGetStmtAttr(hstmt0, SQL_ATTR_IMP_ROW_DESC, &hIrd0, 0, NULL);  
  
// APD and IPD of hstmt1  
SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_PARAM_DESC, &hApd1, 0, NULL);  
SQLGetStmtAttr(hstmt1, SQL_ATTR_IMP_PARAM_DESC, &hIpd1, 0, NULL);  
  
// Use row-wise binding on hstmt0 to fetch rows  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER) sizeof(PartsSource), 0);  
  
// Set rowset size for hstmt0  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
  
// Execute a select statement  
SQLExecDirect(hstmt0, "SELECT PARTID, DESCRIPTION, PRICE FROM PARTS ORDER BY 3, 1, 2"",  
               SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt0, 1, SQL_C_SLONG, rget[0].sPartID, 0,   
   &rget[0].cbPartID);  
SQLBindCol(hstmt0, 2, SQL_C_CHAR, &rget[0].szDescription, DESC_LEN,   
   &rget[0].cbDescription);  
SQLBindCol(hstmt0, 3, SQL_C_FLOAT, rget[0].sPrice,   
   0, &rget[0].cbPrice);  
  
// Perform parameter bindings on hstmt1.   
SQLCopyDesc(hArd0, hApd1);  
SQLCopyDesc(hIrd0, hIpd1);  
  
// Set the array status pointer of IRD  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_STATUS_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the ARRAY_STATUS_PTR field of APD to be the same  
// as that in IRD.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_PARAM_OPERATION_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the hIpd1 records as input parameters  
rc = SQLSetDescField(hIpd1, 1, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 2, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 3, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
  
// Prepare an insert statement on hstmt1. PartsCopy is a copy of  
// PartsSource  
SQLPrepare(hstmt1, "INSERT INTO PARTS_COPY VALUES (?, ?, ?)", SQL_NTS);  
  
// In a loop, fetch a rowset, and copy the fetched rowset to PARTS_COPY  
  
rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
while (SQL_SUCCEEDED(rc)) {  
  
   // After the call to SQLFetchScroll, the status array has row   
   // statuses. This array is used as input status in the APD  
   // and hence determines which elements of the rowset buffer  
   // are inserted.  
   SQLExecute(hstmt1);  
  
   rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
} // while  
```  
  
### <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen von deskriptorfelder für mehrere|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen einer einzelnen Deskriptorfeld|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen von mehreren deskriptorfeldern|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
