---
title: Unterstützen von verteilten Transaktionen | Microsoft-Dokumentation
description: Verteilte Transaktionen im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
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
ms.author: pelopes
ms.openlocfilehash: c9827cd6bbc679bc312c0918eda71e6500063562
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011253"
---
# <a name="supporting-distributed-transactions"></a>Unterstützen von verteilten Transaktionen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Consumer des OLE DB-Treibers für SQL Server können die **ITransactionJoin::JoinTransaction**-Methode verwenden, um an verteilten Transaktionen teilzunehmen, die von Microsoft Distributed Transaction Coordinator (MS DTC) koordiniert werden.  
  
 MS DTC macht COM-Objekte verfügbar, mit denen Clients koordinierte Transaktionen initiieren und an koordinierten Transaktionen teilnehmen können, die sich über mehrere Verbindungen zu verschiedenen Datenspeichern erstrecken. Zum Initiieren einer Transaktion verwendet der Consumer des OLE DB-Treibers für SQL Server die DTC-Schnittstelle **ITransactionDispenser** von Microsoft. Das **BeginTransaction**-Element von **ITransactionDispenser** gibt einen Verweis auf ein verteiltes Transaktionsobjekt zurück. Dieser Verweis wird mit  **JoinTransaction** an den OLE DB-Treiber für SQL Server übergeben.  
  
 MS DTC unterstützt asynchrone „Commit“- und „Abort“-Funktionen bei verteilten Transaktionen. Für Benachrichtigungen über den asynchronen Transaktionsstatus implementiert der Consumer die **ITransactionOutcomeEvents**-Schnittstelle und verbindet die Schnittstelle mit einem MS DTC-Transaktionsobjekt.  
  
 Für verteilte Transaktionen implementiert der OLE DB-Treiber für SQL Server **ITransactionJoin::JoinTransaction**-Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*punkTransactionCoord*|Ein Zeiger auf ein MS DTC-Transaktionsobjekt|  
|*IsoLevel*|Wird vom OLE DB-Treiber für SQL Server ignoriert Die Isolationsstufe für MS DTC-koordinierte Transaktionen wird festgelegt, wenn der Consumer vom MS DTC ein Transaktionsobjekt abruft.|  
|*IsoFlags*|Muss den Wert 0 (null) haben. Der OLE DB-Treiber für SQL Server gibt XACT_E_NOISORETAIN zurück, wenn ein anderer Wert vom Consumer angegeben wird.|  
|*POtherOptions*|Wenn nicht NULL, fordert der OLE DB-Treiber für SQL Server das Optionsobjekt von der Schnittstelle an. Der OLE DB-Treiber für SQL Server gibt XACT_E_NOTIMEOUT zurück, wenn das *ulTimeout*-Element des Optionsobjekts nicht 0 (null) ist. Der OLE DB-Treiber für SQL Server ignoriert den Wert des *szDescription*-Elements.|  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Transaktionen](../../oledb/ole-db-transactions/transactions.md)  
  
  
