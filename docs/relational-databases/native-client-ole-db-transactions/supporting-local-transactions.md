---
title: Unterstützen lokaler Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 76e14df87e8dca104fc0b9da44836288dc56ea69
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761549"
---
# <a name="supporting-local-transactions"></a>Unterstützen lokaler Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine Sitzung begrenzt den Transaktions Bereich für eine lokale Transaktion eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieters. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieter eine Anforderung an eine verbundene Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]übermittelt, stellt die Anforderung eine Arbeitseinheit für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter dar, wenn der Native Client Anbieter eine Anforderung an eine verbundene Instanz von sendet. Lokale Transaktionen wrappen immer eine oder mehrere Arbeitseinheiten in einer einzigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Sitzung.  
  
 Mithilfe des Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Autocommit-Modus von Native Client OLE DB-Anbieter wird eine einzelne Arbeitseinheit als Bereich einer lokalen Transaktion behandelt. Nur eine Einheit nimmt an der lokalen Transaktion teil. Wenn eine Sitzung erstellt wird, startet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter eine Transaktion für die Sitzung. Nach der erfolgreichen Verarbeitung einer Arbeitseinheit wird ein Commit für die Arbeit ausgeführt. Bei Auftreten eines Fehlers wird ein Rollback für den begonnenen Teil der Arbeit ausgeführt, und der Fehler wird dem Consumer gemeldet. In beiden Fällen beginnt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter eine neue lokale Transaktion für die Sitzung, sodass alle Aufgaben innerhalb einer Transaktion durchgeführt werden.  
  
 Der Consumer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters kann mithilfe der **itransaktionlocal** -Schnittstelle eine genauere Kontrolle über den lokalen Transaktions Bereich leiten. Wenn eine Consumersitzung eine Transaktion initiiert, werden alle Arbeitseinheiten der Sitzung zwischen dem Anfangspunkt der Transaktion und eventuellen Aufrufen der Methode **Commit** oder der Methode **Abort** als eine unteilbare Einheit behandelt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter beginnt implizit eine Transaktion, wenn er vom Consumer an ihn weitergeleitet wird. Wenn der Consumer keine Beibehaltung anfordert, kehrt die Sitzung zum Verhalten der übergeordneten Transaktionsebene zurück, in der Regel ist das der Autocommitmodus.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **ITransaction local:: Start Transaction** -Parameter wie folgt.  
  
|Parameter|und Beschreibung|  
|---------------|-----------------|  
|*isoLevel*[in]|Die innerhalb dieser Transaktion zu verwendende Isolationsstufe. In lokalen Transaktionen unterstützt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Folgendes:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Hinweis: Unabhängig davon, ob die Versionsverwaltung für die Datenbank aktiviert ist, ist ISOLATIONLEVEL_SNAPSHOT ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] für das Argument *isoLevel* gültig. Jedoch tritt ein Fehler auf, wenn der Benutzer versucht, eine Anweisung auszuführen und die Versionsverwaltung nicht aktiviert und/oder die Datenbank nicht schreibgeschützt ist. Zudem tritt bei einer Verbindung mit einer *-Version, die älter als*  ist, der Fehler XACT_E_ISOLATIONLEVEL auf, wenn ISOLATIONLEVEL_SNAPSHOT als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]isoLevel[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] angegeben wird.|  
|*isoFlags*[in]|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler für einen beliebigen Wert ungleich 0 (null) zurück.|  
|*pOtherOptions*[in]|Wenn nicht NULL, fordert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter das Options-Objekt von der-Schnittstelle an. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt XACT_E_NOTIMEOUT zurück, wenn der *ulTimeout* -Member des Options-Objekts nicht 0 (null) ist. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ignoriert den Wert des *szDescription* -Members.|  
|*pulTransactionLevel*[out]|Wenn der Wert nicht NULL ist, gibt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter die auf der Ebene der Transaktion eingefügte Ebene zurück.|  
  
 Für lokale Transaktionen implementiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter **ITransaction:: Abort** -Parameter wie folgt.  
  
|Parameter|und Beschreibung|  
|---------------|-----------------|  
|*pboidReason*[in]|Wird bei Festlegung ignoriert. Kann daher auch NULL sein.|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Wenn der Wert false ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter für die Sitzung auf den Autocommitmodus zurückgesetzt.|  
|*fAsync*[in]|Der asynchrone Abbruch wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter nicht unterstützt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt XACT_E_NOTSUPPORTED zurück, wenn der Wert nicht false ist.|  
  
 Für lokale Transaktionen implementiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter **ITransaction:: Commit** -Parameter wie folgt.  
  
|Parameter|und Beschreibung|  
|---------------|-----------------|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Wenn der Wert false ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter für die Sitzung auf den Autocommitmodus zurückgesetzt.|  
|*grfTC*[in]|Asynchrone und Phase 1-Rückgaben werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter nicht unterstützt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt XACT_E_NOTSUPPORTED für jeden anderen Wert als XACTTC_SYNC zurück.|  
|*grfRM*[in]|Muss den Wert 0 (null) haben.|  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Rowsets in der Sitzung werden bei einem lokalen Commit-oder Abbruch Vorgang basierend auf den Werten der Rowseteigenschaften DBPROP_ABORTPRESERVE und DBPROP_COMMITPRESERVE beibehalten. Standardmäßig sind diese Eigenschaften VARIANT_FALSE, und alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nativen Client-OLE DB Anbieter-Rowsets in der Sitzung gehen nach einem Abbruch-oder Commitvorgang verloren.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert die **itransaktionobject** -Schnittstelle nicht. Bei einem Versuch des Consumers, einen Verweis auf die Schnittstelle abzurufen, wird E_NOINTERFACE zurückgegeben.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Transaktionen](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Arbeiten mit der Momentaufnahmeisolation](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)  
  
  
