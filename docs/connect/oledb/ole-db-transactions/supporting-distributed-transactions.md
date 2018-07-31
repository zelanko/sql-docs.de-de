---
title: Unterstützen von verteilten Transaktionen
description: Verteilte Transaktionen in OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: abd6cda6c01f46dd179c462b2d6038c09137de03
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105986"
---
# <a name="supporting-distributed-transactions"></a>Unterstützen von verteilten Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Consumer des OLE DB-Treibers für SQL Server können die **ITransactionJoin::JoinTransaction**-Methode verwenden, um an verteilten Transaktionen teilzunehmen, die von Microsoft Distributed Transaction Coordinator (MS DTC) koordiniert werden.  
  
 MS DTC macht COM-Objekte verfügbar, mit denen Clients koordinierte Transaktionen initiieren und an koordinierten Transaktionen teilnehmen können, die sich über mehrere Verbindungen zu verschiedenen Datenspeichern erstrecken. Zum Initiieren einer Transaktion verwendet der Consumer des **Native Client OLE DB-Anbieters die MS DTC ITransactionDispenser**-Schnittstelle. Das **BeginTransaction**-Element von **ITransactionDispenser** gibt einen Verweis auf ein verteiltes Transaktionsobjekt zurück. Dieser Verweis wird an den OLE DB-Treiber für die Verwendung von SQL Server übergeben **JoinTransaction**.  
  
 MS DTC unterstützt asynchrone „Commit“- und „Abort“-Funktionen bei verteilten Transaktionen. Für Benachrichtigungen über den asynchronen Transaktionsstatus implementiert der Consumer die **ITransactionOutcomeEvents**-Schnittstelle und verbindet die Schnittstelle mit einem MS DTC-Transaktionsobjekt.  
  
 Für verteilte Transaktionen implementiert der OLE DB-Treiber für SQL Server **ITransactionJoin::JoinTransaction**-Parameter wie folgt.  
  
|Parameter|und Beschreibung|  
|---------------|-----------------|  
|*punkTransactionCoord*|Ein Zeiger auf ein MS DTC-Transaktionsobjekt|  
|*IsoLevel*|Wird von der OLE DB-Treiber für SQLServer ignoriert. Die Isolationsstufe für MS DTC-koordinierte Transaktionen wird festgelegt, wenn der Consumer vom MS DTC ein Transaktionsobjekt abruft.|  
|*IsoFlags*|Muss den Wert 0 (null) haben. Der  Native Client OLE DB-Anbieter gibt XACT_E_NOISORETAIN zurück, wenn vom Consumer ein anderer Wert angegeben wird.|  
|*POtherOptions*|Wenn nicht NULL ist, der OLE DB-Treiber für SQL Server-Anforderungen das Options-Objekt von der Schnittstelle. Der  *Native Client OLE DB-Anbieter gibt XACT_E_NOTIMEOUT zurück, wenn das ulTimeout*-Element des Optionsobjekts nicht 0 (null) ist. Der OLE DB-Treiber für SQL Server ignoriert den Wert des der *SzDescription* Member.|  
  
 In diesem Beispiel wird eine Transaktion mit MS DTC koordiniert.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
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
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Transaktionen](../../oledb/ole-db-transactions/transactions.md)  
  
  
