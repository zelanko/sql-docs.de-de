---
title: Unterstützen von lokalen Transaktionen | Microsoft-Dokumentation
description: Lokale Transaktionen im OLE DB-Treiber für SQL Server
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
ms.openlocfilehash: 13e0337ff4ccc8a6797d9fdd23a61d637a37688b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011245"
---
# <a name="supporting-local-transactions"></a>Unterstützen lokaler Transaktionen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Eine Sitzung begrenzt den Transaktionsbereich für eine lokale Transaktion des OLE DB-Treibers für SQL Server. Wenn der OLE DB-Treiber für SQL Server auf Anweisung eines Consumers eine Anforderung an eine verbundene [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz übermittelt, stellt die Anforderung für den OLE DB-Treiber für SQL Server eine Arbeitseinheit dar. Lokale Transaktionen umschließen stets eine oder mehrere Arbeitseinheiten in einer einzigen Sitzung des OLE DB-Treibers für SQL Server.  
  
 Bei Verwendung des standardmäßigen Autocommitmodus des OLE DB-Treibers für SQL Server wird eine einzelne Arbeitseinheit als Bereich einer lokalen Transaktion behandelt. Nur eine Einheit nimmt an der lokalen Transaktion teil. Bei Erstellung einer Sitzung beginnt der OLE DB-Treiber für SQL Server eine Transaktion für die Sitzung. Nach der erfolgreichen Verarbeitung einer Arbeitseinheit wird ein Commit für die Arbeit ausgeführt. Bei Auftreten eines Fehlers wird ein Rollback für den begonnenen Teil der Arbeit ausgeführt, und der Fehler wird dem Consumer gemeldet. In jedem Fall beginnt der OLE DB-Treiber für SQL Server eine neue lokale Transaktion für die Sitzung, damit die gesamte Arbeitseinheit innerhalb einer Transaktion verarbeitet wird.  
  
 Der Consumer des OLE DB-Treibers für SQL Server kann den Bereich der lokalen Transaktion mithilfe der **ITransactionLocal** -Schnittstelle genauer steuern. Wenn eine Consumersitzung eine Transaktion initiiert, werden alle Arbeitseinheiten der Sitzung zwischen dem Anfangspunkt der Transaktion und eventuellen Aufrufen der Methode **Commit** oder der Methode **Abort** als eine unteilbare Einheit behandelt. Der OLE DB-Treiber für SQL Server beginnt eine Transaktion implizit, sobald er vom Consumer dazu aufgefordert wird. Wenn der Consumer keine Beibehaltung anfordert, kehrt die Sitzung zum Verhalten der übergeordneten Transaktionsebene zurück, in der Regel ist das der Autocommitmodus.  
  
 Der OLE DB-Treiber für SQL Server unterstützt **ITransactionLocal::StartTransaction**-Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*isoLevel*[in]|Die innerhalb dieser Transaktion zu verwendende Isolationsstufe. Der OLE DB-Treiber für SQL Server unterstützt in lokalen Transaktionen Folgendes:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Hinweis: Unabhängig davon, ob die Versionsverwaltung für die Datenbank aktiviert ist, ist ISOLATIONLEVEL_SNAPSHOT ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] für das Argument *isoLevel* gültig. Jedoch tritt ein Fehler auf, wenn der Benutzer versucht, eine Anweisung auszuführen und die Versionsverwaltung nicht aktiviert und/oder die Datenbank nicht schreibgeschützt ist. Zudem tritt bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Version, die älter als [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ist, der Fehler XACT_E_ISOLATIONLEVEL auf, wenn ISOLATIONLEVEL_SNAPSHOT als *isoLevel* angegeben wird.|  
|*isoFlags*[in]|Der OLE DB-Treiber für SQL Server gibt für jeden Wert außer 0 (null) einen Fehler zurück.|  
|*pOtherOptions*[in]|Wenn nicht NULL, fordert der OLE DB-Treiber für SQL Server das Optionsobjekt von der Schnittstelle an. Der OLE DB-Treiber für SQL Server gibt XACT_E_NOTIMEOUT zurück, wenn das *ulTimeout*-Element des Optionsobjekts nicht 0 (null) ist. Der OLE DB-Treiber für SQL Server ignoriert den Wert des *szDescription*-Elements.|  
|*pulTransactionLevel*[out]|Wenn der Wert nicht NULL lautet, gibt der OLE DB-Treiber für SQL Server die geschachtelte Ebene der Transaktion zurück.|  
  
 Für lokale Transaktionen implementiert der OLE DB-Treiber für SQL Server **ITransaction::Abort**-Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*pboidReason*[in]|Wird bei Festlegung ignoriert. Kann daher auch NULL sein.|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Wenn der Wert FALSE lautet, kehrt der OLE DB-Treiber für SQL Server für die Sitzung zum Autocommitmodus zurück.|  
|*fAsync*[in]|Der asynchrone Abbruch wird vom OLE DB-Treiber für SQL Server nicht unterstützt. Der OLE DB-Treiber für SQL Server gibt XACT_E_NOTSUPPORTED zurück, wenn der Wert nicht FALSE lautet.|  
  
 Für lokale Transaktionen implementiert der OLE DB-Treiber für SQL Server **ITransaction::Commit**-Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Wenn der Wert FALSE lautet, kehrt der OLE DB-Treiber für SQL Server für die Sitzung zum Autocommitmodus zurück.|  
|*grfTC*[in]|Die asynchrone Rückkehr und die Rückkehr zu Phase eins werden vom OLE DB-Treiber für SQL Server nicht unterstützt. Der OLE DB-Treiber für SQL Server gibt außer für XACTTC_SYNC für jeden Wert XACT_E_NOTSUPPORTED zurück.|  
|*grfRM*[in]|Muss den Wert 0 (null) haben.|  
  
 Die Rowsets des OLE DB-Treibers für SQL Server für die Sitzung werden bei einem lokalen Commit- oder Abbruchvorgang je nach den Werten für die Rowseteigenschaften DBPROP_ABORTPRESERVE und DBPROP_COMMITPRESERVE beibehalten. Standardmäßig lauten die Werte dieser Eigenschaften auf VARIANT_FALSE und gehen alle Rowsets des OLE DB Driver for SQL Server für die Sitzung bei einem Abbruch- oder Commitvorgang verloren.  
  
 Der OLE DB-Treiber für SQL Server implementiert die **ITransactionObject**-Schnittstelle nicht. Bei einem Versuch des Consumers, einen Verweis auf die Schnittstelle abzurufen, wird E_NOINTERFACE zurückgegeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Transaktionen](../../oledb/ole-db-transactions/transactions.md)   
 [Arbeiten mit der Momentaufnahmeisolation](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
