---
title: Unterstützen von lokalen Transaktionen | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8533747bbe5ccb79a06b10a754c4af45ab241843
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280172"
---
# <a name="supporting-local-transactions"></a>Unterstützen lokaler Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine Sitzung grenzt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Transaktionsbereich für eine lokale Transaktion des nativen Client-OLE-DB-Anbieters ab. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter auf Anweisung eines Consumers eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Anforderung an eine verbundene Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von sendet, stellt die Anforderung eine Arbeitseinheit für den nativen Client-OLE-DB-Anbieter dar. Lokale Transaktionen umschließen immer eine oder mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Arbeitseinheiten in einer einzelnen Native Client OLE DB-Anbietersitzung.  
  
 Im standardmäßigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommit-Modus des nativen Client-OLE-DB-Anbieters wird eine einzelne Arbeitseinheit als Bereich einer lokalen Transaktion behandelt. Nur eine Einheit nimmt an der lokalen Transaktion teil. Wenn eine Sitzung erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird, startet der native Client-OLE-DB-Anbieter eine Transaktion für die Sitzung. Nach der erfolgreichen Verarbeitung einer Arbeitseinheit wird ein Commit für die Arbeit ausgeführt. Bei Auftreten eines Fehlers wird ein Rollback für den begonnenen Teil der Arbeit ausgeführt, und der Fehler wird dem Consumer gemeldet. In beiden Fällen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beginnt der native Client-OLE-DB-Anbieter eine neue lokale Transaktion für die Sitzung, sodass alle Arbeiten innerhalb einer Transaktion ausgeführt werden.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer des nativen Client-OLE-DB-Anbieters kann mithilfe der **ITransactionLocal-Schnittstelle** eine genauere Steuerung des lokalen Transaktionsbereichs übertragen. Wenn eine Consumersitzung eine Transaktion initiiert, werden alle Arbeitseinheiten der Sitzung zwischen dem Anfangspunkt der Transaktion und eventuellen Aufrufen der Methode **Commit** oder der Methode **Abort** als eine unteilbare Einheit behandelt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter startet implizit eine Transaktion, wenn er vom Consumer dazu aufgefordert wird. Wenn der Consumer keine Beibehaltung anfordert, kehrt die Sitzung zum Verhalten der übergeordneten Transaktionsebene zurück, in der Regel ist das der Autocommitmodus.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt die Parameter **ITransactionLocal::StartTransaction** wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*isoLevel*[in]|Die innerhalb dieser Transaktion zu verwendende Isolationsstufe. Bei lokalen Transaktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt der native Client-OLE-DB-Anbieter Folgendes:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Hinweis: Unabhängig davon, ob die Versionsverwaltung für die Datenbank aktiviert ist, ist ISOLATIONLEVEL_SNAPSHOT ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] für das Argument *isoLevel* gültig. Jedoch tritt ein Fehler auf, wenn der Benutzer versucht, eine Anweisung auszuführen und die Versionsverwaltung nicht aktiviert und/oder die Datenbank nicht schreibgeschützt ist. Zudem tritt bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version, die älter als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ist, der Fehler XACT_E_ISOLATIONLEVEL auf, wenn ISOLATIONLEVEL_SNAPSHOT als *isoLevel* angegeben wird.|  
|*isoFlags*[in]|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt einen Fehler für einen anderen Wert als Null zurück.|  
|*pOtherOptions*[in]|Wenn nicht NULL, fordert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter das Optionsobjekt von der Schnittstelle an. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt XACT_E_NOTIMEOUT zurück, wenn das *ulTimeout-Member* des Optionsobjekts nicht Null ist. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter ignoriert den Wert des *szDescription-Members.*|  
|*pulTransactionLevel*[out]|Wenn nicht NULL, gibt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter die geschachtelte Ebene der Transaktion zurück.|  
  
 Bei lokalen Transaktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementiert der native Client-OLE-DB-Anbieter **die Parameter ITransaction::Abort** wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*pboidReason*[in]|Wird bei Festlegung ignoriert. Kann daher auch NULL sein.|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Bei FALSE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kehrt der native Client-OLE-DB-Anbieter in den Autocommit-Modus für die Sitzung zurück.|  
|*fAsync*[in]|Asynchroner Abbruch wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nativen Client-OLE-DB-Anbieter nicht unterstützt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt XACT_E_NOTSUPPORTED zurück, wenn der Wert nicht FALSE ist.|  
  
 Bei lokalen Transaktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementiert der native Client-OLE-DB-Anbieter **die Parameter ITransaction::Commit** wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Bei FALSE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kehrt der native Client-OLE-DB-Anbieter in den Autocommit-Modus für die Sitzung zurück.|  
|*grfTC*[in]|Asynchrone und Phase-1-Rückgaben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden vom Native Client OLE DB-Anbieter nicht unterstützt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt XACT_E_NOTSUPPORTED für einen anderen Wert als XACTTC_SYNC zurück.|  
|*grfRM*[in]|Muss den Wert 0 (null) haben.|  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Stammreihen des nativen Client-OLE-DB-Anbieters in der Sitzung werden für einen lokalen Commit- oder Abbruchvorgang basierend auf den Werten der Rowseteigenschaften DBPROP_ABORTPRESERVE und DBPROP_COMMITPRESERVE beibehalten. Standardmäßig sind diese Eigenschaften sowohl [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE als auch alle Stammsätze des nativen Client-OLE-DB-Anbieters in der Sitzung gehen nach einem Abbruch- oder Commitvorgang verloren.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter implementiert die **ITransactionObject-Schnittstelle** nicht. Bei einem Versuch des Consumers, einen Verweis auf die Schnittstelle abzurufen, wird E_NOINTERFACE zurückgegeben.  
  
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
 [Transaktionen](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Arbeiten mit Momentaufnahmeisolation](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)  
  
  
