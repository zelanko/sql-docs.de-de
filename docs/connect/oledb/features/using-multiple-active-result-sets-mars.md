---
title: Verwenden von Multiple Active Result Sets (MARS) | Microsoft-Dokumentation
description: Verwenden von Multiple Active Result Sets (MARS)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, MARS
- MSOLEDBSQL, MARS
- data access [OLE DB Driver for SQL Server], MARS
- Multiple Active Result Sets
- OLE DB Driver for SQL Server, MARS
- MARS [SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 8174333abc11b47d62c154171726afebee24824f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67988813"
---
# <a name="using-multiple-active-result-sets-mars"></a>Verwenden von Multiple Active Result Sets (MARS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

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
>  Standardmäßig ist die MARS-Funktionalität nicht aktiviert. Um MARS bei der Verbindungsherstellung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über den OLE DB-Treiber für SQL Server zu verwenden, müssen Sie die Funktionalität in einer Verbindungszeichenfolge explizit aktivieren. Weitere Informationen finden Sie in den OLE DB-Treiber für SQL Server-Abschnitten weiter unten in diesem Thema.  
  
 Der OLE DB-Treiber für SQL Server schränkt die Anzahl aktiver Anweisungen für eine Verbindung nicht ein.  
  
 Traditionelle Anwendungen, bei denen kein Bedarf an mehreren Batches oder gespeicherten Prozeduren aus mehreren gleichzeitig ausgeführten Anweisungen besteht, profitieren von MARS, ohne die Implementierung von MARS verstehen zu müssen. Anwendungen mit komplexeren Anforderungen müssen diese jedoch berücksichtigen.  
  
 MARS ermöglicht die verschachtelte Ausführung mehrerer Anforderungen innerhalb einer einzelnen Verbindung. Das bedeutet, dass innerhalb der Ausführung eines Batches eine weitere Anforderung ausgeführt werden kann. Beachten Sie jedoch, dass MARS mit Blick auf Interleaving, nicht die parallele Ausführung definiert ist.  
  
 Die MARS-Infrastruktur ermöglicht die verschachtelte Ausführung mehrerer Batches, die Ausführung kann jedoch nur an genau definierten Punkten gewechselt werden. Außerdem müssen die meisten Anweisungen innerhalb eines Batches atomar ausgeführt werden. Anweisungen, die Zeilen an den Client zurückgeben (gelegentlich bezeichnet als *Zwischenergebnispunkte*) dürfen die Ausführung vor Abschluss verschachteln, während noch Zeilen an den Client gesendet werden. Beispiel:  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Alle anderen Anweisungen, die im Rahmen einer gespeicherten Prozedur oder eines Batches ausgeführt werden, müssen zunächst abgeschlossen werden, ehe die Ausführung zu anderen MARS-Anforderungen umgeschaltet werden kann.  
  
 Wie Batches die Ausführung genau verschachteln, hängt von zahlreichen Faktoren ab, und die exakte Ausführungsfolge von Befehlen aus mehreren Batches mit Zwischenergebnispunkten lässt sich nur schwer vorhersagen. Achten Sie darauf, unerwünschte Nebeneffekte aufgrund der verschachtelten Ausführung solcher komplexer Batches zu vermeiden.  
  
 Sie vermeiden Probleme, indem Sie den Verbindungsstatus (SET, USE) und Transaktionen (BEGIN TRAN, COMMIT, ROLLBACK) an Stelle von [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen mit API-Aufrufen verwalten. Schließen Sie diese Anweisungen zudem nicht in Batches mit mehreren Anweisungen ein, die auch Zwischenergebnispunkte enthalten, und serialisieren Sie die Ausführung solcher Batches durch Verarbeitung oder Abbruch aller Ergebnisse.  
  
> [!NOTE]  
>  Ein Batch oder eine gespeicherte Prozedur, die bei Aktivierung von MARS eine manuelle oder implizite Transaktion startet, muss diese Transaktion vor Ausführung des Batchs abschließen. Andernfalls führt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nach Abschluss des Batchs einen Rollback für alle von der Transaktion vorgenommenen Änderungen aus. Eine derartige Transaktion wird von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Transaktion im Bereich des Batchs verwaltet. Dieser Transaktionstyp wurde in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] neu eingeführt, um vorhandene, gut konzipierte gespeicherte Prozeduren verwenden zu können, wenn MARS aktiviert ist. Weitere Informationen zu Transaktionen im Bereich des Batches finden Sie unter [Transaktionsanweisungen &#40;Transact-SQL&#41;](../../../t-sql/statements/statements.md).  
  
 Ein Beispiel zur Verwendung von MARS aus ADO finden Sie unter [Verwenden von ADO mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
## <a name="in-memory-oltp"></a>In-Memory-OLTP  
 In-Memory-OLTP unterstützt MARS mithilfe von Abfragen und systemintern kompilierten gespeicherten Prozeduren. MARS ermöglicht das Anfordern von Daten aus mehreren Abfragen, ohne dass vor dem Senden einer Anforderung zum Abrufen von Zeilen aus einem neuen Resultset jedes Resultset vollständig abgerufen werden muss. Zum erfolgreichen Lesen von Daten aus mehreren geöffneten Resultsets müssen Sie eine für MARS aktivierte Verbindung verwenden.  
  
 MARS ist standardmäßig deaktiviert, deshalb muss die Funktion durch Hinzufügen von `MultipleActiveResultSets=True` zu einer Verbindungszeichenfolge explizit aktiviert werden. Das folgende Beispiel veranschaulicht, wie eine Verbindung mit einer SQL Server-Instanz hergestellt und wie angegeben wird, dass MARS aktiviert werden soll:  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS mit In-Memory-OLTP ist im Wesentlichen dasselbe wie MARS im Rest der SQL-Engine. In den folgenden Listen werden die Unterschiede bei der Verwendung von MARS in speicheroptimierten Tabellen und systemintern kompilierten gespeicherten Prozeduren unterstützt aufgeführt.  
  
 **MARS und speicheroptimierte Tabellen**  
  
 Im Folgenden werden die Unterschiede zwischen datenträgerbasierten und speicheroptimierten Tabellen bei Verwendung einer für MARS aktivierten Verbindung aufgeführt:  
  
-   Zwei Anweisungen können Daten im selben Zielobjekt ändern. Wenn aber beide Anweisungen versuchen, denselben Datensatz zu ändern, führt ein write-write-Konflikt zu einem Vorgangsfehler. Werden durch die zwei Vorgänge hingegen verschiedene Datensätze geändert, sind die Vorgänge erfolgreich.  
  
-   Jede Anweisung wird mit SNAPSHOT-Isolation ausgeführt, sodass neue Vorgänge die von vorhandenen Anweisungen durchgeführten Änderungen sehen können. Selbst wenn die parallel ausgeführten Anweisungen im Rahmen derselben Transaktion ausgeführt werden, erstellt die SQL-Engine für jede Anweisung Transaktionen im Bereich des Batches, die voneinander isoliert sind. Allerdings sind Transaktionen im Bereich des Batches weiterhin miteinander verbunden, sodass sich ein Rollback einer Transaktion im Bereich des Batches auf andere Transaktionen im selben Batch auswirkt.  
  
-   DDL-Vorgänge sind in Benutzertransaktionen nicht zugelassen und führen sofort zu einem Fehler.  
  
 **MARS und nativ kompilierte gespeicherte Prozeduren**  
  
 Systemintern kompilierte gespeicherte Prozeduren können in für MARS aktivierten Verbindungen ausgeführt werden und die Ausführung nur dann an eine andere Anweisung abgeben, wenn ein Abgabepunkt ermittelt wird. Ein Abgabepunkt erfordert eine SELECT-Anweisung, bei der es sich um die einzige Anweisung innerhalb einer systemintern kompilierten gespeicherten Prozedur handelt, die die Ausführung an eine andere Anweisung abgeben kann. Wenn keine SELECT-Anweisung in der Prozedur enthalten ist, erfolgt keine Abgabe, und die Prozedurausführung wird abgeschlossen, bevor andere Anweisungen ausgeführt werden.  
  
 **MARS und In-Memory-OLTP-Transaktionen**  
  
 Änderungen, die durch Anweisungen und atomare Blöcke vorgenommen werden, die sich überlappen, sind voneinander isoliert. Wenn beispielsweise eine Anweisung oder ein atomarer Block einige Änderungen vornimmt und dann die Ausführung an eine andere Anweisung abgibt, sind die von der ersten Anweisung durchgeführten Änderungen für die neue Anweisung nicht sichtbar. Darüber hinaus sind bei der Wiederaufnahme der Ausführung durch die erste Anweisungen keine Änderungen durch andere Anweisungen sichtbar. Für Anweisungen sind nur Änderungen sichtbar, die vor Beginn der Anweisung abgeschlossen und bestätigt wurden.  
  
 Eine neue Benutzertransaktion kann innerhalb der aktuellen Benutzertransaktion mit der BEGIN TRANSACTION-Anweisung gestartet werden. Dies wird allerdings nur im Interop-Modus unterstützt, sodass BEGIN TRANSACTION nur aus einer T-SQL-Anweisung aufgerufen werden kann, nicht jedoch aus einer systemintern kompilierten gespeicherten Prozedur. Sie können einen Sicherungspunkt in einer Transaktion mit SAVE TRANSACTION oder einem API-Aufruf an „transaction.Save(Name_Sicherungspunkt)“ erstellen, um einen Rollback auf den Sicherungspunkt durchzuführen. Diese Funktion wird ebenfalls nur aus T-SQL-Anweisungen aktiviert, und nicht aus systemintern kompilierten gespeicherten Prozeduren.  
  
 **MARS und Columnstore-Indizes**  
  
 SQL Server (ab Version 2016) unterstützt MARS mit Columnstore-Indizes. SQL Server 2014 verwendet MARS für schreibgeschützte Verbindungen mit Tabellen mit einem Columnstore-Index.    SQL Server 2014 unterstützt MARS jedoch nicht für gleichzeitige DML-Vorgänge (Data Manipulation Language, Datenbearbeitungssprache) für eine Tabelle mit einem Columnstore-Index. In diesem Fall beendet SQL Server die Verbindung und bricht die Transaktionen ab.   SQL Server 2012 umfasst schreibgeschützte Columnstore-Indizes, für die MARS nicht gilt.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server  
 Der OLE DB-Treiber für SQL Server unterstützt MARS durch Hinzufügen der SSPROP_INIT_MARSCONNECTION-Eigenschaft zur Datenquelleninitialisierung, die in der Eigenschaftengruppe DBPROPSET_SQLSERVERDBINIT implementiert wird. Außerdem wurde ein neues Verbindungszeichenfolgen-Schlüsselwort, **MarsConn**, aufgenommen. Akzeptiert werden die Werte **true** oder **false**, **false** ist die Standardeinstellung.  
  
 Die Datenquelleneigenschaft DBPROP_MULTIPLECONNECTIONS ist standardmäßig auf VARIANT_TRUE festgelegt. Das bedeutet, der Anbieter erzeugt mehrere Verbindungen, um mehrere gleichzeitige Befehls- und Rowsetobjekte zu unterstützen. Ist MARS aktiviert, kann der OLE DB-Treiber für SQL Server mehrere Befehls- und Rowsetobjekte in einer einzelnen Verbindung unterstützen. Daher ist MULTIPLE_CONNECTIONS standardmäßig auf VARIANT_FALSE festgelegt.  
  
 Weitere Informationen zu Verbesserungen am DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="ole-db-driver-for-sql-server-example"></a>OLE DB-Treiber für SQL Server: Beispiel  
 In diesem Beispiel wird mit dem OLE DB-Treiber für SQL Server ein Datenquellenobjekt erstellt. Vor der Erstellung des Sitzungsobjekts wird MARS mithilfe der DBPROPSET_SQLSERVERDBINIT-Eigenschaftengruppe aktiviert.  
  
```  
#include <msoledbsql.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
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

  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 
  
  
