---
title: Verwenden von Multiple Active Resultsets (MARS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, MARS
- SQLNCLI, MARS
- data access [SQL Server Native Client], MARS
- Multiple Active Result Sets
- SQL Server Native Client, MARS
- MARS [SQL Server]
- SQL Server Native Client ODBC driver, MARS
ms.assetid: ecfd9c6b-7d29-41d8-af2e-89d7fb9a1d83
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 929229de6e30c9a9a5da0a50db69d4718070eaaa
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39536420"
---
# <a name="using-multiple-active-result-sets-mars"></a>Verwenden von Multiple Active Result Sets (MARS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Seit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] werden Multiple Active Result Sets (MARS) in Anwendungen unterstützt, die auf [!INCLUDE[ssDE](../../../includes/ssde-md.md)] zugreifen. In früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] konnten Datenbankanwendungen nicht mehrere aktive Anweisungen über eine Verbindung verwalten. Beim Verwenden von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standardresultsets musste die Anwendung alle Resultsets aus einem Batch verarbeiten oder abbrechen, bevor ein anderer Batch auf dieser Verbindung ausgeführt werden konnte. In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wurde ein neues Verbindungsattribut eingeführt, das es Anwendungen ermöglicht, mehr als eine ausstehende Anforderung pro Verbindung und mehr als ein aktives Standardresultset pro Verbindung anzugeben.  
  
 MARS vereinfacht den Anwendungsentwurf mit den folgenden neuen Fähigkeiten:  
  
-   Anwendungen können mehrere Standardresultsets geöffnet haben und die Lesevorgänge daraus verschachteln.  
  
-   Anwendungen können bei geöffneten Standardresultsets andere Anweisungen ausführen (z. B. INSERT, UPDATE, DELETE und Aufrufe gespeicherter Prozeduren).  
  
 Für Anwendungen, die MARS verwenden, gelten die folgenden nützlichen Richtlinien:  
  
-   Standardresultsets sollten für kurzlebige oder kurze Resultsets verwendet werden, die durch einzelne SQL-Anweisungen generiert werden (SELECT, DML mit OUTPUT, RECEIVE, READ TEXT usw.).  
  
-   Servercursor sollten für längerlebige oder große Resultsets verwendet werden, die durch einzelne SQL-Anweisungen generierte werden.  
  
-   Lesen Sie bei Batches, die mehrere Ergebnisse zurückgeben, und bei Prozeduranforderungen immer bis zum Ende der Results, unabhängig davon, ob Ergebnisse zurückgeben werden oder nicht.  
  
-   Wo möglich, verwenden Sie anstelle von [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen API-Aufrufe, um Verbindungseigenschaften zu ändern und Transaktionen zu verwalten.  
  
-   In MARS wird ein Identitätswechsel im Bereich einer Sitzung verhindert, solange gleichzeitige Batches ausgeführt werden.  
  
> [!NOTE]  
>  Standardmäßig ist die MARS-Funktionalität nicht aktiviert. Um MARS bei der Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu verwenden, müssen Sie die Funktionalität in einer Verbindungszeichenfolge explizit aktivieren. Weitere Informationen finden Sie in den Abschnitten zum [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter und dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber weiter unten in diesem Thema.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client schränkt die Anzahl aktiver Anweisungen auf einer Verbindung nicht ein.  
  
 Typische Anwendungen, bei denen kein Bedarf für mehrere Batches oder gespeicherte Prozeduren aus mehreren gleichzeitig ausgeführten Anweisungen besteht, profitieren von MARS, ohne die Implementierung von MARS verstehen zu müssen. Anwendungen mit komplexeren Anforderungen müssen diese jedoch berücksichtigen.  
  
 MARS ermöglicht die verschachtelte Ausführung mehrerer Anforderungen innerhalb einer einzelnen Verbindung. Das bedeutet, dass innerhalb der Ausführung eines Batches eine weitere Anforderung ausgeführt werden kann. Beachten Sie jedoch, dass MARS mit Blick auf Interleaving, nicht die parallele Ausführung definiert ist.  
  
 Die MARS-Infrastruktur ermöglicht die verschachtelte Ausführung mehrerer Batches, die Ausführung kann jedoch nur an genau definierten Punkten gewechselt werden. Außerdem müssen die meisten Anweisungen innerhalb eines Batches atomar ausgeführt werden. Anweisungen, die Rückgabe an den Client, der manchmal auch als bezeichnet *zwischenergebnispunkte*, um die Ausführung vor Abschluss verschachteln, während die Zeilen an den Client, z. B. gesendet werden dürfen:  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Alle anderen Anweisungen, die im Rahmen einer gespeicherten Prozedur oder eines Batches ausgeführt werden, müssen zunächst abgeschlossen werden, ehe die Ausführung zu anderen MARS-Anforderungen umgeschaltet werden kann.  
  
 Wie Batches die Ausführung genau verschachteln, hängt von zahlreichen Faktoren ab, und die exakte Ausführungsfolge von Befehlen aus mehreren Batches mit Zwischenergebnispunkten lässt sich nur schwer vorhersagen. Achten Sie darauf, unerwünschte Nebeneffekte aufgrund der verschachtelten Ausführung solcher komplexer Batches zu vermeiden.  
  
 Sie vermeiden Probleme, indem Sie den Verbindungsstatus (SET, USE) und Transaktionen (BEGIN TRAN, COMMIT, ROLLBACK) an Stelle von [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen mit API-Aufrufen verwalten. Schließen Sie diese Anweisungen zudem nicht in Batches mit mehreren Anweisungen ein, die auch Zwischenergebnispunkte enthalten, und serialisieren Sie die Ausführung solcher Batches durch Verarbeitung oder Abbruch aller Ergebnisse.  
  
> [!NOTE]  
>  Ein Batch oder eine gespeicherte Prozedur, die bei Aktivierung von MARS eine manuelle oder implizite Transaktion startet, muss diese Transaktion vor Ausführung des Batchs abschließen. Andernfalls führt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nach Abschluss des Batchs einen Rollback für alle von der Transaktion vorgenommenen Änderungen aus. Eine derartige Transaktion wird von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Transaktion im Bereich des Batchs verwaltet. Dieser Transaktionstyp wurde in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] neu eingeführt, um vorhandene, gut konzipierte gespeicherte Prozeduren verwenden zu können, wenn MARS aktiviert ist. Weitere Informationen zu Transaktionen mit batchbereich, finden Sie unter [Transaction-Anweisungen &#40;Transact-SQL&#41;](~/t-sql/statements/statements.md).  
  
 Ein Beispiel der Verwendung von MARS aus ADO finden Sie unter [mithilfe von ADO mit SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
## <a name="in-memory-oltp"></a>In-Memory OLTP  
 In-Memory-OLTP unterstützt MARS mithilfe von Abfragen und systemintern kompilierte gespeicherte Prozeduren. MARS ermöglicht die anfordernde Daten aus mehreren Abfragen ohne die einzelnen Resultsets, die vor dem Senden einer Anforderung zum Abrufen von Zeilen aus einem neuen Resultset vollständig abrufen. Zum Lesen von aus mehrere open Ergebnis erfolgreich aktiviert Mengen, die Sie verwenden müssen, eine MARS Verbindung.  
  
 MARS ist standardmäßig deaktiviert, sodass Sie es explizit durch das Hinzufügen aktivieren müssen `MultipleActiveResultSets=True` auf eine Verbindungszeichenfolge. Im folgende Beispiel wird veranschaulicht, wie eine Verbindung mit einer Instanz von SQL Server, und geben an, dass MARS aktiviert ist:  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS mit In-Memory-OLTP ist im Grunde identisch mit MARS im weiteren Verlauf der SQL-Engine. Im folgenden werden die Unterschiede beim Verwenden von MARS in speicheroptimierten Tabellen und systemintern gespeicherten Prozeduren kompilierten aufgeführt.  
  
 **MARS und Speicheroptimierte Tabellen**  
  
 Im folgenden sind die Unterschiede zwischen datenträgerbasierte und Speicheroptimierte Tabellen bei der Verbindung mit einem MARS aktiviert werden:  
  
-   Zwei Anweisungen können Daten in dem gleichen Zielobjekt ändern, wenn beide versuchen, denselben Datensatz zu ändern ein Write-Write-Konflikt führt aber zu den neuen Vorgang fehlschlägt. Wenn beide Vorgänge auf unterschiedliche Datensätze ändern, werden jedoch die Vorgänge erfolgreich.  
  
-   Jede Anweisung unter momentaufnahmeisolation ausgeführt wird, sodass neue Vorgänge nicht von den vorhandenen Anweisungen vorgenommene Änderungen sehen können. Auch wenn die gleichzeitigen Anweisungen unter der gleichen Transaktion ausgeführt werden erstellt die SQL-Engine mit batchbereich Transaktionen für jede Anweisung, die voneinander isoliert sind. Transaktionen mit batchbereich sind daher ein Rollback für eine Transaktion mit batchbereich anderen Formeln in demselben Batch wirkt sich jedoch immer noch miteinander verbunden.  
  
-   DDL-Vorgänge sind in Transaktionen nicht zulässig, sodass sie sofort fehl.  
  
 **MARS und nativ kompilierte gespeicherte Prozeduren**  
  
 Systemintern kompilierte gespeicherte Prozeduren können in Verbindungen mit aktivierter MARS-Funktion ausgeführt und können die Ausführung an eine andere Anweisung ergibt, nur, wenn ein Yield-Punkt gefunden wird. Ein Yield-Punkt erfordert eine SELECT-Anweisung die einzige Anweisung in einer systemintern kompilierten gespeicherten Prozedur handelt, die Ausführung einer anderen Anweisung ergeben können. Wenn eine SELECT-Anweisung nicht in die Prozedur vorhanden, die sie nicht liefert ist, wird es bis zum Abschluss ausgeführt, bevor andere Anweisungen beginnen.  
  
 **MARS und In-Memory-OLTP-Transaktionen**  
  
 Von Anweisungen und atomic-Blöcke, die sich überlappen vorgenommenen Änderungen sind voneinander isoliert. Z. B. wenn eine Anweisung oder atomic-Block nimmt einige Änderungen vor, und klicken Sie dann setzt die Ausführung auf einer anderen Anweisung aus, sehen die neue Anweisung nicht durch die erste Anweisung vorgenommene Änderungen. Darüber hinaus bei der ersten Anweisung die Ausführung fortgesetzt wird, wird sie keine Änderungen, die von allen anderen Anweisungen angezeigt. Anweisungen werden nur Änderungen angezeigt, die abgeschlossen und ein Commit ausgeführt, bevor die Anweisung beginnt.  
  
 Eine neue Benutzertransaktion in der aktuellen Benutzertransaktion, die mit der BEGIN TRANSACTION-Anweisung gestartet werden – dies ist nur im interop-Modus unterstützt werden, damit der BEGIN TRANSACTION kann nur von einer T-SQL-Anweisung aufgerufen werden und nicht aus innerhalb einer systemintern kompilierten gespeicherten die Prozedur. Sie können einen erstellen, zeigen Sie mit der Transaktion zu speichern oder einen API-Aufruf zu Transaktion in einer Transaktion. Save(save_point_name), ein Rollback zum Sicherungspunkt auszuführen. Dieses Feature ist auch nur von T-SQL-Anweisungen aktiviert und nicht in systemintern kompilierten gespeicherten Prozeduren.  
  
 **MARS und columnstore-Indizes**  
  
 SQL Server (ab 2016) unterstützt MARS mit columnstore-Indizes. SQL Server 2014 verwendet MARS für schreibgeschützte Verbindungen mit Tabellen mit einem Columnstore-Index.    SQL Server 2014 unterstützt MARS jedoch nicht für gleichzeitige DML-Vorgänge (Data Manipulation Language, Datenbearbeitungssprache) für eine Tabelle mit einem Columnstore-Index. In diesem Fall beendet SQL Server die Verbindung und bricht die Transaktionen ab.   SQL Server 2012 bietet nur-Lese columnstore-Indizes und MARS gilt nicht für sie.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt MARS durch Hinzufügen der SSPROP_INIT_MARSCONNECTION Initialisierungseigenschaft-Datenquellen, die in der Eigenschaftengruppe DBPROPSET_SQLSERVERDBINIT implementiert wird. Außerdem wurde ein neues Verbindungszeichenfolgen-Schlüsselwort, **MarsConn**, aufgenommen. Er akzeptiert **"true"** oder **"false"** Werte **"false"** ist die Standardeinstellung.  
  
 Die Datenquelleneigenschaft DBPROP_MULTIPLECONNECTIONS ist standardmäßig auf VARIANT_TRUE festgelegt. Das bedeutet, der Anbieter erzeugt mehrere Verbindungen, um mehrere gleichzeitige Befehls- und Rowsetobjekte zu unterstützen. Wenn MARS aktiviert ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client können mehrere Befehls- und Rowsetobjekte Objekte auf einer einzelnen Verbindung unterstützen, daher ist MULTIPLE_CONNECTIONS standardmäßig auf VARIANT_FALSE festgelegt ist.  
  
 Weitere Informationen zu Verbesserungen der DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>OLE DB-Anbieter von SQL Server Native Client: Beispiel  
 In diesem Beispiel wird ein Datenquellenobjekt erstellt, mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native OLE DB-Anbieter und MARS wird mithilfe der DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz, bevor das Sitzungsobjekt erstellt wird aktiviert.  
  
```  
#include <sqlncli.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt MARS durch Hinzufügungen zu den [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) und [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) Funktionen. SQL_COPT_SS_MARS_ENABLED wurde hinzugefügt, um entweder SQL_MARS_ENABLED_YES oder SQL_MARS_ENABLED_NO zu akzeptieren. Der Standardwert ist SQL_MARS_ENABLED_NO. Darüber hinaus eine neue Verbindungszeichenfolgen-Schlüsselwort, **Mars_Connection**, hinzugefügt wurde. Gültige Werte sind "Ja" oder "Nein", wobei "Nein" die Standardeinstellung ist.  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>SQL Server Native Client-ODBC-Treiber: Beispiel  
 In diesem Beispiel die **SQLSetConnectAttr** Funktion dient zum Aktivieren von MARS vor dem Aufruf der **SQLDriverConnect** Funktion, um die Datenbank zu verbinden. Nachdem die Verbindung wird hergestellt, zwei **SQLExecDirect** Funktionen aufgerufen, um zwei gesonderte Resultsets für dieselbe Verbindung zu erstellen.  
  
```  
#include <sqlncli.h>  
  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_MARS_ENABLED, SQL_MARS_ENABLED_YES, SQL_IS_UINTEGER);  
SQLDriverConnect(hdbc, hwnd,   
   "DRIVER=SQL Server Native Client 10.0;  
   SERVER=(local);trusted_connection=yes;", SQL_NTS, szOutConn,   
   MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt2);  
  
// The 2nd execute would have failed with connection busy error if  
// MARS were not enabled.  
SQLExecDirect(hstmt1, L”SELECT * FROM Authors”, SQL_NTS);  
SQLExecDirect(hstmt2, L”SELECT * FROM Titles”, SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Verwenden von SQL Server-Standardresultsets](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
