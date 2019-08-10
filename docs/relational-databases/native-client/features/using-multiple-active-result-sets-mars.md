---
title: Verwenden von Multiple Active Result Sets (Mars) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d98975e0c8d690224d9cd58c4154f0d6fbdb083
ms.sourcegitcommit: 3ec48823bee1c092ce2aba6011b95174de03fb65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926868"
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
> Standardmäßig wird die Mars-Funktionalität nicht durch den Treiber aktiviert. Um Mars zu verwenden, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit Native Client eine Verbindung mit herstellen, müssen Sie Mars speziell in einer Verbindungs Zeichenfolge aktivieren. Einige Anwendungen können Mars jedoch standardmäßig aktivieren, wenn die Anwendung erkennt, dass der Treiber Mars unterstützt. Für diese Anwendungen können Sie Mars in der Verbindungs Zeichenfolge nach Bedarf deaktivieren. Weitere Informationen finden Sie in den Abschnitten zum [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter und dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber weiter unten in diesem Thema.

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client schränkt die Anzahl aktiver Anweisungen auf einer Verbindung nicht ein.  
  
 Typische Anwendungen, die nicht mehr als einen einzelnen Batch oder eine gespeicherte Prozedur mit mehreren Anweisungen verwenden müssen, die gleichzeitig ausgeführt werden, profitieren von Mars, ohne dass Sie wissen müssen, wie Mars implementiert ist. Anwendungen mit komplexeren Anforderungen müssen diese jedoch berücksichtigen.  
  
 MARS ermöglicht die verschachtelte Ausführung mehrerer Anforderungen innerhalb einer einzelnen Verbindung. Das bedeutet, dass innerhalb der Ausführung eines Batches eine weitere Anforderung ausgeführt werden kann. Beachten Sie jedoch, dass MARS mit Blick auf Interleaving, nicht die parallele Ausführung definiert ist.  
  
 Die MARS-Infrastruktur ermöglicht die verschachtelte Ausführung mehrerer Batches, die Ausführung kann jedoch nur an genau definierten Punkten gewechselt werden. Außerdem müssen die meisten Anweisungen innerhalb eines Batches atomar ausgeführt werden. Anweisungen, die Zeilen an den Client zurückgeben (manchmal auch als *Yield Points*bezeichnet), dürfen die Ausführung vor dem Abschluss überarbeiten, während Zeilen an den Client gesendet werden, z. b.:  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Alle anderen Anweisungen, die im Rahmen einer gespeicherten Prozedur oder eines Batches ausgeführt werden, müssen zunächst abgeschlossen werden, ehe die Ausführung zu anderen MARS-Anforderungen umgeschaltet werden kann.  
  
 Wie Batches die Ausführung genau verschachteln, hängt von zahlreichen Faktoren ab, und die exakte Ausführungsfolge von Befehlen aus mehreren Batches mit Zwischenergebnispunkten lässt sich nur schwer vorhersagen. Achten Sie darauf, unerwünschte Nebeneffekte aufgrund der verschachtelten Ausführung solcher komplexer Batches zu vermeiden.  
  
 Sie vermeiden Probleme, indem Sie den Verbindungsstatus (SET, USE) und Transaktionen (BEGIN TRAN, COMMIT, ROLLBACK) an Stelle von [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen mit API-Aufrufen verwalten. Schließen Sie diese Anweisungen zudem nicht in Batches mit mehreren Anweisungen ein, die auch Zwischenergebnispunkte enthalten, und serialisieren Sie die Ausführung solcher Batches durch Verarbeitung oder Abbruch aller Ergebnisse.  
  
> [!NOTE]  
>  Ein Batch oder eine gespeicherte Prozedur, die bei Aktivierung von MARS eine manuelle oder implizite Transaktion startet, muss diese Transaktion vor Ausführung des Batchs abschließen. Andernfalls führt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nach Abschluss des Batchs einen Rollback für alle von der Transaktion vorgenommenen Änderungen aus. Eine derartige Transaktion wird von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Transaktion im Bereich des Batchs verwaltet. Dieser Transaktionstyp wurde in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] neu eingeführt, um vorhandene, gut konzipierte gespeicherte Prozeduren verwenden zu können, wenn MARS aktiviert ist. Weitere Informationen zu Transaktionen im Batch Bereich finden Sie unter [Transaktions Anweisungen &#40;Transact-SQL&#41;](~/t-sql/statements/statements.md).  
  
 Ein Beispiel für die Verwendung von Mars aus ADO finden [Sie unter Verwenden von ADO mit SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
## <a name="in-memory-oltp"></a>In-Memory-OLTP  
 In-Memory OLTP unterstützt Mars mithilfe von Abfragen und nativ kompilierten gespeicherten Prozeduren. Mars ermöglicht das Anfordern von Daten aus mehreren Abfragen, ohne dass jedes Resultset vollständig abgerufen werden muss, bevor eine Anforderung zum Abrufen von Zeilen aus einem neuen Resultset gesendet wird. Um erfolgreich aus mehreren geöffneten Resultsets zu lesen, müssen Sie eine Verbindung mit Mars-Aktivierung verwenden.  
  
 Mars ist standardmäßig deaktiviert, sodass Sie es explizit aktivieren müssen, `MultipleActiveResultSets=True` indem Sie zu einer Verbindungs Zeichenfolge hinzufügen. Im folgenden Beispiel wird veranschaulicht, wie Sie eine Verbindung mit einer Instanz von SQL Server herstellen und angeben, dass MARS aktiviert ist:  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 Mars mit in-Memory-OLTP ist im Wesentlichen mit dem Mars im Rest der SQL-Engine identisch. Im folgenden werden die Unterschiede bei der Verwendung von Mars in Speicher optimierten Tabellen und System intern kompilierten gespeicherten Prozeduren aufgelistet.  
  
 **Mars-und Speicher optimierte Tabellen**  
  
 Im folgenden sind die Unterschiede zwischen Datenträger basierten und Speicher optimierten Tabellen bei Verwendung einer Mars-aktivierten Verbindung aufgeführt:  
  
-   Zwei-Anweisungen können Daten im gleichen Zielobjekt ändern, aber wenn beide versuchen, denselben Datensatz zu ändern, führt ein Write-Write-Konflikt dazu, dass der neue Vorgang fehlschlägt. Wenn jedoch beide Vorgänge unterschiedliche Datensätze ändern, werden die Vorgänge erfolgreich ausgeführt.  
  
-   Jede Anweisung wird unter der Momentaufnahme Isolation ausgeführt, sodass neue Vorgänge keine Änderungen sehen können, die von den vorhandenen Anweisungen vorgenommen werden Auch wenn die gleichzeitigen Anweisungen unter derselben Transaktion ausgeführt werden, erstellt die SQL-Engine Transaktionen im Batch Bereich für jede Anweisung, die voneinander isoliert sind. Transaktionen mit Batch Bereich werden jedoch immer noch zusammengebunden, sodass ein Rollback einer Transaktion mit Batch Bereich andere Auswirkungen auf andere im gleichen Batch hat.  
  
-   DDL-Vorgänge sind in Benutzer Transaktionen nicht zulässig, sodass Sie sofort fehlschlagen.  
  
 **MARS und nativ kompilierte gespeicherte Prozeduren**  
  
 System intern kompilierte gespeicherte Prozeduren können in Mars-fähigen Verbindungen ausgeführt werden und können nur dann in einer anderen Anweisung ausgeführt werden, wenn ein Yield Point erreicht wird. Ein Yield Point erfordert eine SELECT-Anweisung, die die einzige Anweisung in einer System intern kompilierten gespeicherten Prozedur ist, die die Ausführung für eine andere Anweisung erzielen kann. Wenn eine SELECT-Anweisung in der Prozedur nicht vorhanden ist, wird Sie bis zum Abschluss ausgeführt, bevor andere Anweisungen beginnen.  
  
 **Mars-und in-Memory-OLTP-Transaktionen**  
  
 Änderungen, die durch-Anweisungen und atomarische Blöcke vorgenommen werden, die verschachtelt sind, sind voneinander isoliert. Wenn z. b. eine-Anweisung oder ein Atomic-Block Änderungen vornimmt und die Ausführung dann an eine andere Anweisung übergibt, werden die von der ersten Anweisung vorgenommenen Änderungen von der neuen Anweisung nicht angezeigt. Wenn die erste Anweisung die Ausführung fortsetzt, werden darüber hinaus keine von anderen Anweisungen vorgenommenen Änderungen angezeigt. In-Anweisungen werden nur Änderungen angezeigt, die vor dem Start der Anweisung abgeschlossen und committet wurden.  
  
 Eine neue Benutzertransaktion kann mit der BEGIN TRANSACTION-Anweisung innerhalb der aktuellen Benutzertransaktion gestartet werden. Dies wird nur im Interop-Modus unterstützt, sodass die BEGIN TRANSACTION nur von einer T-SQL-Anweisung aus aufgerufen werden kann, und nicht aus einer nativ kompilierten gespeicherten Dringlichkeit. Sie können einen Sicherungspunkt in einer Transaktion erstellen, indem Sie Transaktion speichern oder einen API-Aufrufe der Transaktion verwenden. Speichern (save_point_name), um ein Rollback auf den Sicherungspunkt auszuführen. Diese Funktion ist auch nur über T-SQL-Anweisungen und nicht innerhalb von System intern kompilierten gespeicherten Prozeduren aktiviert.  
  
 **Mars-und columnstore--Indizes**  
  
 SQL Server (beginnend mit 2016) unterstützt Mars mit columnstore--Indizes. SQL Server 2014 verwendet MARS für schreibgeschützte Verbindungen mit Tabellen mit einem Columnstore-Index.    SQL Server 2014 unterstützt MARS jedoch nicht für gleichzeitige DML-Vorgänge (Data Manipulation Language, Datenbearbeitungssprache) für eine Tabelle mit einem Columnstore-Index. In diesem Fall beendet SQL Server die Verbindung und bricht die Transaktionen ab.   SQL Server 2012 hat schreibgeschützte columnstore--Indizes, und Mars gilt nicht für Sie.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Mars durch das Hinzufügen der SSPROP_INIT_MARSCONNECTION-Datenquellen-Initialisierungs Eigenschaft, die im DBPROPSET_SQLSERVERDBINIT-Eigenschaften Satz implementiert ist. Außerdem wurde ein neues Verbindungszeichenfolgen-Schlüsselwort, **MarsConn**, aufgenommen. Er akzeptiert **true** -oder **false** -Werte. der Standardwert ist **false** .  
  
 Die Datenquelleneigenschaft DBPROP_MULTIPLECONNECTIONS ist standardmäßig auf VARIANT_TRUE festgelegt. Das bedeutet, der Anbieter erzeugt mehrere Verbindungen, um mehrere gleichzeitige Befehls- und Rowsetobjekte zu unterstützen. Wenn MARS aktiviert ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann Native Client mehrere Befehls-und Rowsetobjekte in einer einzelnen Verbindung unterstützen, sodass MULTIPLE_CONNECTIONS standardmäßig auf VARIANT_FALSE festgelegt ist.  
  
 Weitere Informationen zu Verbesserungen am DBPROPSET_SQLSERVERDBINIT-Eigenschaften Satz finden Sie unter [Initialisierungs-und Autorisierungs Eigenschaften](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>OLE DB-Anbieter von SQL Server Native Client: Beispiel  
 In diesem Beispiel wird ein Datenquellen Objekt mithilfe des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] systemeigenen OLE DB Anbieters erstellt, und Mars wird mithilfe des DBPROPSET_SQLSERVERDBINIT-Eigenschaften Satzes aktiviert, bevor das Sitzungs Objekt erstellt wird.  
  
```cpp
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
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt Mars durch Ergänzungen zu den Funktionen [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) und [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) . SQL_COPT_SS_MARS_ENABLED wurde hinzugefügt, um entweder SQL_MARS_ENABLED_YES oder SQL_MARS_ENABLED_NO zu akzeptieren. Der Standardwert ist SQL_MARS_ENABLED_NO. Außerdem wurde das neue Verbindungs Zeichenfolgen-Schlüsselwort **Mars_Connection**hinzugefügt. Gültige Werte sind "Ja" oder "Nein", wobei "Nein" die Standardeinstellung ist.  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>SQL Server Native Client-ODBC-Treiber: Beispiel  
 In diesem Beispiel wird die **SQLSetConnectAttr** -Funktion verwendet, um Mars zu aktivieren, bevor die **SQLDriverConnect** -Funktion aufgerufen wird, um eine Verbindung mit der Datenbank herzustellen. Nachdem die Verbindung hergestellt wurde, werden zwei **SQLExecDirect** -Funktionen aufgerufen, um zwei separate Resultsets für die gleiche Verbindung zu erstellen.  
  
```cpp
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
SQLExecDirect(hstmt1, L"SELECT * FROM Authors", SQL_NTS);  
SQLExecDirect(hstmt2, L"SELECT * FROM Titles", SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Verwenden von SQL Server-Standardresultsets](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
