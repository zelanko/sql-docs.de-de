---
title: BeginTrans, CommitTrans, RollbackTrans-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CommitTransComplete
- Connection::BeginTransComplete
- Connection::RollbackTransComplete
- Connection::CommitTransComplete
- RollbackTransComplete
- BeginTransComplete
helpviewer_keywords:
- CommitTransComplete event [ADO]
- RollbackTransComplete event [ADO]
- BeginTransComplete event [ADO]
ms.assetid: ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afd8b9d4a45bdc98388f1133b3478a1cfbe51e4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773448"
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete-, CommitTransComplete- und RollbackTransComplete-Ereignis (ADO)
Diese Ereignisse werden nach dem zugehörigen Vorgang aufgerufen werden, auf die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt die Ausführung abgeschlossen ist.  
  
-   **BeginTransComplete** wird aufgerufen, nachdem die [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) Vorgang.  
  
-   **CommitTransComplete** wird aufgerufen, nachdem die [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) Vorgang.  
  
-   **RollbackTransComplete** wird aufgerufen, nachdem die [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) Vorgang.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *TransactionLevel*  
 Ein **lange** Wert, der die neue Transaktionsebene der enthält die **BeginTrans** , dieses Ereignis verursacht hat.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es beschreibt den Fehler, die aufgetreten sind, wenn der Wert des EventStatusEnum **AdStatusErrorsOccurred**; andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert. Wenn eines dieser Ereignisse aufgerufen wird, wird dieser Parameter festgelegt, um **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war, oder mit **AdStatusErrorsOccurred** bei fehlgeschlagenem Vorgang.  
  
 Diese Ereignisse können nachfolgende Benachrichtigungen verhindern, indem Sie die Festlegung dieses Parameters auf **AdStatusUnwantedEvent** bevor das Ereignis zurückgegeben.  
  
 *pConnection*  
 Die **Verbindung** Objekt für die dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 In Visual C++ mehrere **Verbindungen** können die gleiche Ereignisbehandlungsmethode freigeben. Die Methode verwendet den zurückgegebenen **Verbindung** Objekt, um zu bestimmen, welches Objekt das Ereignis verursacht hat.  
  
 Wenn die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaftensatz auf **AdXactCommitRetaining** oder **AdXactAbortRetaining**, eine neue Transaktion gestartet wird, nach dem Commit oder Rollback einer Transaktion. Verwenden der **BeginTransComplete** -Ereignis, um alle zu ignorieren, aber die erste Transaktion Start-Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans, CommitTrans und RollbackTrans-Methoden – Beispiel (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [BeginTrans-, CommitTrans- und RollbackTrans-Methode (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
