---
title: Verwenden von Multiple Active Result Sets (Mars) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
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
>  Standardmäßig ist die MARS-Funktionalität nicht aktiviert. Wenn Sie Mars für die Verbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit OLE DB-Treiber für SQL Server verwenden möchten, müssen Sie ihn speziell in einer Verbindungs Zeichenfolge aktivieren. Weitere Informationen finden Sie im Abschnitt OLE DB Driver for SQL Server weiter unten in diesem Thema.  
  
 Der OLE DB-Treiber für SQL Server schränkt die Anzahl der aktiven Anweisungen für eine Verbindung nicht ein.  
  
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
>  Ein Batch oder eine gespeicherte Prozedur, die bei Aktivierung von MARS eine manuelle oder implizite Transaktion startet, muss diese Transaktion vor Ausführung des Batchs abschließen. Andernfalls führt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nach Abschluss des Batchs einen Rollback für alle von der Transaktion vorgenommenen Änderungen aus. Eine derartige Transaktion wird von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Transaktion im Bereich des Batchs verwaltet. Dieser Transaktionstyp wurde in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] neu eingeführt, um vorhandene, gut konzipierte gespeicherte Prozeduren verwenden zu können, wenn MARS aktiviert ist. Weitere Informationen zu Transaktionen im Batch Bereich finden Sie unter [Transaktions Anweisungen &#40;Transact-SQL&#41;](../../../t-sql/statements/statements.md).  
  
 Ein Beispiel für die Verwendung von Mars aus ADO finden [Sie unter Verwenden von ADO mit OLE DB-Treiber für SQL Server](../../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
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
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server  
 Der OLE DB-Treiber für SQL Server unterstützt MARS durch Hinzufügen der SSPROP_INIT_MARSCONNECTION-Eigenschaft zur Datenquelleninitialisierung, die in der Eigenschaftengruppe DBPROPSET_SQLSERVERDBINIT implementiert wird. Außerdem wurde ein neues Verbindungszeichenfolgen-Schlüsselwort, **MarsConn**, aufgenommen. Er akzeptiert **true** -oder **false** -Werte. der Standardwert ist **false** .  
  
 Die Datenquelleneigenschaft DBPROP_MULTIPLECONNECTIONS ist standardmäßig auf VARIANT_TRUE festgelegt. Das bedeutet, der Anbieter erzeugt mehrere Verbindungen, um mehrere gleichzeitige Befehls- und Rowsetobjekte zu unterstützen. Ist MARS aktiviert, kann der OLE DB-Treiber für SQL Server mehrere Befehls- und Rowsetobjekte in einer einzelnen Verbindung unterstützen. Daher ist MULTIPLE_CONNECTIONS standardmäßig auf VARIANT_FALSE festgelegt.  
  
 Weitere Informationen zu Verbesserungen am DBPROPSET_SQLSERVERDBINIT-Eigenschaften Satz finden Sie unter [Initialisierungs-und Autorisierungs Eigenschaften](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
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
 
  
  
