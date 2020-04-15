---
title: SQLCopyDesc-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef1fa5b319e8d72d5b70e6f2010e493eec6f844a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301227"
---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLCopyDesc** kopiert Deskriptorinformationen von einem Deskriptorhandle in ein anderes.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Argumente  
 *SourceDescHandle*  
 [Eingabe] Quelldeskriptor-Handle.  
  
 *TargetDescHandle*  
 [Eingabe] Zieldeskriptor-Handle. Das *TargetDescHandle-Argument* kann ein Handle für einen Anwendungsdeskriptor oder eine IPD sein. *TargetDescHandle* kann nicht auf ein Handle für eine IRD festgelegt werden, oder **SQLCopyDesc** gibt SQLSTATE HY016 zurück (kann einen Implementierungszeilendeskriptor nicht ändern).  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCopyDesc** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DESC und einem *Handle* von *TargetDescHandle*aufgerufen wird. Wenn ein ungültiges *SourceDescHandle* im Aufruf übergeben wurde, wird SQL_INVALID_HANDLE zurückgegeben, aber es wird kein SQLSTATE zurückgegeben. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLCopyDesc** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
 Wenn ein Fehler zurückgegeben wird, wird der Aufruf von **SQLCopyDesc** sofort abgebrochen, und der Inhalt der Felder im *TargetDescHandle-Deskriptor* ist nicht definiert.  
  
 Da **SQLCopyDesc** durch Aufrufen von **SQLGetDescField** und **SQLSetDescField**implementiert werden kann, gibt **SQLCopyDesc** möglicherweise SQLSTATEs zurück, die von **SQLGetDescField** oder **SQLSetDescField**zurückgegeben werden.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den für die Unterstützung der Ausführung oder den Abschluss der Funktion erforderlichen Speicher nicht zuweisen.|  
|HY007|Zugehörige Anweisung ist nicht vorbereitet|*SourceDescHandle* wurde einem IRD zugeordnet, und das zugeordnete Anweisungshandle befand sich nicht im vorbereiteten oder ausgeführten Zustand.|  
|HY010|Funktionssequenzfehler|(DM) Das Deskriptorhandle in *SourceDescHandle* oder *TargetDescHandle* wurde einem *StatementHandle* zugeordnet, für das eine asynchron ausführende Funktion (nicht diese) aufgerufen wurde und immer noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) Das Deskriptorhandle in *SourceDescHandle* oder *TargetDescHandle* wurde einem *StatementHandle* zugeordnet, für das **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** aufgerufen und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Für das Verbindungshandle, das dem *SourceDescHandle* oder *TargetDescHandle*zugeordnet ist, wurde eine asynchron ausführende Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLCopyDesc-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungshandles aufgerufen, die dem *SourceDescHandle* oder *TargetDescHandle* zugeordnet sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY016|Eine Implementierungszeilenbeschreibung kann nicht geändert werden.|*TargetDescHandle* wurde einem IRD zugeordnet.|  
|HY021|Inkonsistente Deskriptorinformationen|Die bei einer Konsistenzprüfung überprüften Deskriptorinformationen waren nicht konsistent. Weitere Informationen finden Sie unter "Konsistenzprüfungen" in **SQLSetDescField**.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der Aufruf von **SQLCopyDesc** hat einen Aufruf von **SQLSetDescField**ausgelöst, * \*aber ValuePtr* war für das *FieldIdentifier-Argument* in *TargetDescHandle*ungültig.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der Treiber, der dem *SourceDescHandle* oder *TargetDescHandle* zugeordnet ist, unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Ein Aufruf von **SQLCopyDesc** kopiert die Felder des Quelldeskriptorhandles in das Zieldeskriptorhandle. Felder können nur in einen Anwendungsdeskriptor oder eine IPD kopiert werden, nicht jedoch in eine IRD. Felder können entweder aus einer Anwendung oder einer Implementierungsbeschreibung kopiert werden.  
  
 Felder können nur dann aus einem IRD kopiert werden, wenn sich das Anweisungshandle im vorbereiteten oder ausgeführten Zustand befindet. Andernfalls gibt die Funktion SQLSTATE HY007 zurück (Die Associated-Anweisung ist nicht vorbereitet).  
  
 Felder können aus einer IPD kopiert werden, unabhängig davon, ob eine Anweisung vorbereitet wurde oder nicht. Wenn eine SQL-Anweisung mit dynamischen Parametern vorbereitet wurde und die automatische Auffüllung der IPD unterstützt und aktiviert wird, wird die IPD vom Treiber aufgefüllt. Wenn **SQLCopyDesc** mit der IPD als *SourceDescHandle*aufgerufen wird, werden die ausgefüllten Felder kopiert. Wenn die IPD nicht vom Treiber aufgefüllt wird, wird der Inhalt der Felder, die sich ursprünglich in der IPD befinden, kopiert.  
  
 Alle Felder des Deskriptors, mit Ausnahme SQL_DESC_ALLOC_TYPE (die angibt, ob das Deskriptor-Handle automatisch oder explizit zugewiesen wurde), werden kopiert, unabhängig davon, ob das Feld für den Zieldeskriptor definiert ist oder nicht. Kopierte Felder überschreiben die vorhandenen Felder.  
  
 Der Treiber kopiert alle Deskriptorfelder, wenn die *Argumente SourceDescHandle* und *TargetDescHandle* demselben Treiber zugeordnet sind, auch wenn sich die Treiber auf zwei unterschiedlichen Verbindungen oder Umgebungen befinden. Wenn die *Argumente SourceDescHandle* und *TargetDescHandle* verschiedenen Treibern zugeordnet sind, kopiert der Treiber-Manager ODBC-definierte Felder, kopiert jedoch keine treiberdefinierten Felder oder Felder, die nicht von ODBC für den Deskriptortyp definiert wurden.  
  
 Der Aufruf von **SQLCopyDesc** wird sofort abgebrochen, wenn ein Fehler auftritt.  
  
 Wenn das SQL_DESC_DATA_PTR Feld kopiert wird, wird eine Konsistenzprüfung für den Zieldeskriptor durchgeführt. Wenn die Konsistenzprüfung fehlschlägt, wird SQLSTATE HY021 (Inkonsistente Deskriptorinformationen) zurückgegeben, und der Aufruf von **SQLCopyDesc** wird sofort abgebrochen. Weitere Informationen zu Konsistenzprüfungen finden Sie unter "Konsistenzprüfungen" in der [SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Deskriptor-Handles können über Verbindungen hinweg kopiert werden, auch wenn sich die Verbindungen in verschiedenen Umgebungen befinden. Wenn der Treiber-Manager erkennt, dass die Quell- und die Zieldeskriptor-Handles nicht zur gleichen Verbindung gehören und die beiden Verbindungen zu separaten Treibern gehören, implementiert er **SQLCopyDesc,** indem eine Feld-für-Feld-Kopie mit **SQLGetDescField** und **SQLSetDescField**ausgeführt wird.  
  
 Wenn **SQLCopyDesc** mit einem *SourceDescHandle* für einen Treiber und einem *TargetDescHandle* für einen anderen Treiber aufgerufen wird, wird die Fehlerwarteschlange des *SourceDescHandle* gelöscht. Dies liegt daran, dass **SQLCopyDesc** in diesem Fall durch Aufrufe von **SQLGetDescField** und **SQLSetDescField**implementiert wird.  
  
> [!NOTE]  
>  Eine Anwendung kann möglicherweise ein explizit zugewiesenes Deskriptorhandle einem *StatementHandle*zuordnen, anstatt **SQLCopyDesc** aufzurufen, um Felder von einem Deskriptor in einen anderen zu kopieren. Ein explizit zugewiesener Deskriptor kann einem anderen *StatementHandle* für dasselbe *ConnectionHandle* zugeordnet werden, indem das Attribut SQL_ATTR_APP_ROW_DESC oder SQL_ATTR_APP_PARAM_DESC Anweisung auf das Handle des explizit zugewiesenen Deskriptors gesetzt wird. Wenn dies geschieht, muss **SQLCopyDesc** nicht aufgerufen werden, um Deskriptorfeldwerte von einem Deskriptor in einen anderen zu kopieren. Ein Deskriptorhandle kann jedoch nicht einem *StatementHandle* für ein anderes *ConnectionHandle*zugeordnet werden. um dieselben Deskriptorfeldwerte für *StatementHandles* in verschiedenen *ConnectionHandles*zu verwenden, muss **SQLCopyDesc** aufgerufen werden.  
  
 Eine Beschreibung der Felder in einem Deskriptorheader oder -datensatz finden Sie unter [SQLSetDescField Function](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptoren](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="copying-rows-between-tables"></a>Kopieren von Zeilen zwischen Tabellen  
 Eine Anwendung kann Daten von einer Tabelle in eine andere kopieren, ohne die Daten auf Anwendungsebene zu kopieren. Zu diesem Tun bindet die Anwendung dieselben Datenpuffer und Deskriptorinformationen an eine Anweisung, die die Daten und die Anweisung abruft, die die Daten in eine Kopie einfügt. Dies kann entweder durch die Freigabe eines Anwendungsdeskriptors (Bindung eines explizit zugewiesenen Deskriptors als ARD an eine Anweisung und die APD in einer anderen) oder durch Verwendung von **SQLCopyDesc** zum Kopieren der Bindungen zwischen der ARD und der APD der beiden Aussagen erreicht werden. Wenn sich die Anweisungen auf verschiedenen Verbindungen befinden, muss **SQLCopyDesc** verwendet werden. Darüber hinaus muss **SQLCopyDesc** aufgerufen werden, um die Bindungen zwischen der IRD und der IPD der beiden Anweisungen zu kopieren. Beim Kopieren von Anweisungen in derselben Verbindung muss der vom Treiber für einen Aufruf von **SQLGetInfo** zurückgegebene SQL_ACTIVE_STATEMENTS-Informationstyp größer als 1 sein, damit dieser Vorgang erfolgreich ausgeführt werden kann. (Dies ist beim Kopieren über Verbindungen hinweg nicht der Fall.)  
  
### <a name="code-example"></a>Codebeispiel  
 Im folgenden Beispiel werden Deskriptorvorgänge verwendet, um die Felder der PartsSource-Tabelle in die PartsCopy-Tabelle zu kopieren. Der Inhalt der PartsSource-Tabelle wird in rowset-Puffer in *hstmt0*abgerufen. Diese Werte werden als Parameter einer INSERT-Anweisung auf *hstmt1* verwendet, um die Spalten der PartsCopy-Tabelle aufzufüllen. Dazu werden die Felder der IRD von *hstmt0* in die Felder der IPD von *hstmt1*und die Felder der ARD von *hstmt0* in die Felder der APD von *hstmt1*kopiert. Verwenden Sie **SQLSetDescField,** um das SQL_DESC_PARAMETER_TYPE-Attribut der IPD auf SQL_PARAM_INPUT festzulegen, wenn Sie IRD-Felder aus einer Anweisung mit Ausgabeparametern in IPD-Felder kopieren, die Eingabeparameter sein müssen.  
  
```cpp  
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
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen mehrerer Deskriptorfelder|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen eines einzelnen Deskriptorfelds|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
