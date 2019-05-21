---
title: Unterstützen lokaler Transaktionen | Microsoft-Dokumentation
description: Lokale Transaktionen in OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 82621a5c289a3ae7a31affa848bc5b2a77800736
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788680"
---
# <a name="supporting-local-transactions"></a>Unterstützen lokaler Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Eine Sitzung begrenzt den Transaktionsbereich für eine OLE DB-Treiber für die lokale SQL Server-Transaktion. Wenn auf die Richtung eines Consumers, der OLE DB-Treiber für SQL Server eine Anforderung an eine verbundene Instanz von übermittelt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], die Anforderung stellt eine Arbeitseinheit für den OLE DB-Treiber für SQL Server dar. Lokale Transaktionen umschließen stets eine oder mehrere Arbeitseinheiten für einen einzelnen OLE DB-Treiber für SQL Server-Sitzung.  
  
 Bei Verwendung des standardmäßigen Autocommitmodus des OLE DB-Treibers für SQL Server wird eine einzelne Arbeitseinheit als Bereich einer lokalen Transaktion behandelt. Nur eine Einheit nimmt an der lokalen Transaktion teil. Wenn eine Sitzung erstellt wird, beginnt der OLE DB-Treiber für SQL Server für die Sitzung eine Transaktion aus. Nach der erfolgreichen Verarbeitung einer Arbeitseinheit wird ein Commit für die Arbeit ausgeführt. Bei Auftreten eines Fehlers wird ein Rollback für den begonnenen Teil der Arbeit ausgeführt, und der Fehler wird dem Consumer gemeldet. In jedem Fall beginnt der OLE DB-Treiber für SQL Server eine neue lokale Transaktion für die Sitzung, damit die gesamte Arbeitseinheit innerhalb einer Transaktion verarbeitet wird.  
  
 Der Consumer des OLE DB-Treibers für SQL Server kann den Bereich der lokalen Transaktion mithilfe der **ITransactionLocal** -Schnittstelle genauer steuern. Wenn eine Consumersitzung eine Transaktion initiiert, werden alle Arbeitseinheiten der Sitzung zwischen dem Anfangspunkt der Transaktion und eventuellen Aufrufen der Methode **Commit** oder der Methode **Abort** als eine unteilbare Einheit behandelt. Der OLE DB-Treiber für SQL Server beginnt implizit eine Transaktion, wenn Sie dazu aufgefordert werden, vom Consumer. Wenn der Consumer keine Beibehaltung anfordert, kehrt die Sitzung zum Verhalten der übergeordneten Transaktionsebene zurück, in der Regel ist das der Autocommitmodus.  
  
 Der OLE DB-Treiber für SQL Server unterstützt **ITransactionLocal:: StartTransaction** Parameter wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*isoLevel*[in]|Die innerhalb dieser Transaktion zu verwendende Isolationsstufe. In lokalen Transaktionen unterstützt der OLE DB-Treiber für SQL Server Folgendes:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Hinweis: Unabhängig davon, ob die Versionsverwaltung für die Datenbank aktiviert ist, ist ISOLATIONLEVEL_SNAPSHOT ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] für das Argument *isoLevel* gültig. Jedoch tritt ein Fehler auf, wenn der Benutzer versucht, eine Anweisung auszuführen und die Versionsverwaltung nicht aktiviert und/oder die Datenbank nicht schreibgeschützt ist. Zudem tritt bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Version, die älter als [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ist, der Fehler XACT_E_ISOLATIONLEVEL auf, wenn ISOLATIONLEVEL_SNAPSHOT als *isoLevel* angegeben wird.|  
|*isoFlags*[in]|Der OLE DB-Treiber für SQL Server gibt einen Fehler für einen anderen Wert als 0 (null) zurück.|  
|*pOtherOptions*[in]|Wenn nicht NULL ist, der OLE DB-Treiber für SQL Server-Anforderungen das Options-Objekt von der Schnittstelle. Der OLE DB-Treiber für SQL Server gibt xact_e_notimeout zurück, wenn des optionsobjekts *UlTimeout* Member ist nicht 0 (null). Der OLE DB-Treiber für SQL Server ignoriert den Wert des der *SzDescription* Member.|  
|*pulTransactionLevel*[out]|Wenn nicht NULL ist, der OLE DB-Treiber für SQL Server gibt die Schachtelungsebene der Transaktion.|  
  
 Für lokale Transaktionen implementiert der OLE DB-Treiber für SQL Server **ITransaction:: Abort** Parameter wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*pboidReason*[in]|Wird bei Festlegung ignoriert. Kann daher auch NULL sein.|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Bei "FALSE" wird der OLE DB-Treiber für SQL Server für die Sitzung den Autocommit-Modus zurückgesetzt.|  
|*fAsync*[in]|Asynchroner Abbruch wird nicht vom OLE DB-Treiber für SQL Server unterstützt. Der OLE DB-Treiber für SQL Server gibt xact_e_notsupported zurück, wenn der Wert nicht "false" ist.|  
  
 Für lokale Transaktionen implementiert der OLE DB-Treiber für SQL Server **ITransaction:: Commit** Parameter wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Bei "FALSE" wird der OLE DB-Treiber für SQL Server für die Sitzung den Autocommit-Modus zurückgesetzt.|  
|*grfTC*[in]|Asynchrone Rückkehr und die Phase, in einen zurückgibt werden nicht vom OLE DB-Treiber für SQL Server unterstützt. Der OLE DB-Treiber für SQL Server gibt xacttc_sync für jeden Wert xact_e_notsupported zurück.|  
|*grfRM*[in]|Muss den Wert 0 (null) haben.|  
  
 Die Rowsets des OLE DB-Treibers für SQL Server für die Sitzung werden bei einem lokalen Commit- oder Abbruchvorgang je nach den Werten für die Rowseteigenschaften DBPROP_ABORTPRESERVE und DBPROP_COMMITPRESERVE beibehalten. Standardmäßig lauten die Werte dieser Eigenschaften auf VARIANT_FALSE und gehen alle Rowsets des OLE DB Driver for SQL Server für die Sitzung bei einem Abbruch- oder Commitvorgang verloren.  
  
 Der OLE DB-Treiber für SQL Server implementiert nicht die **ITransactionObject** Schnittstelle. Bei einem Versuch des Consumers, einen Verweis auf die Schnittstelle abzurufen, wird E_NOINTERFACE zurückgegeben.  
  
 Im folgenden Beispiel wird **ITransactionLocal** verwendet.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Transaktionen](../../oledb/ole-db-transactions/transactions.md)   
 [Arbeiten mit der Momentaufnahmeisolation](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
