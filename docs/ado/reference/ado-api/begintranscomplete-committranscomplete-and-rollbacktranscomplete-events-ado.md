---
title: BeginTrans, CommitTrans, RollbackTrans-Ereignisse (ADO) | Microsoft-Dokumentation
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
ms.openlocfilehash: 750e89e97eb916c7db23e71475b753a57a4d90e9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920447"
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete-, CommitTransComplete-und RollbackTransComplete-Ereignis (ADO)
Diese Ereignisse werden aufgerufen, nachdem der zugehörige Vorgang für das [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt die Ausführung abgeschlossen hat.  
  
-   **BeginTransComplete** wird nach dem [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) -Vorgang aufgerufen.  
  
-   **CommitTransComplete** wird nach dem [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) -Vorgang aufgerufen.  
  
-   **RollbackTransComplete** wird nach dem [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) -Vorgang aufgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *Transaktionlevel*  
 Ein **Long** -Wert, der die neue Transaktionsebene des **BeginTrans** -Werts enthält, der dieses Ereignis verursacht hat.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von EventStatus usenum **adstatuuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert. Wenn eines dieser Ereignisse aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, oder auf **adstatuuserrorsoccurrred** , wenn der Vorgang fehlgeschlagen ist.  
  
 Diese Ereignisse können nachfolgende Benachrichtigungen verhindern, indem Sie diesen Parameter auf **adstatuingunwantedevent** festlegen, bevor das Ereignis zurückgegeben wird.  
  
 *pConnection*  
 Das **Verbindungs** Objekt, für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 In Visual C++ können mehrere **Verbindungen** dieselbe Ereignis Behandlungsmethode verwenden. Die-Methode verwendet das zurückgegebene **Connection** -Objekt, um zu bestimmen, welches Objekt das Ereignis verursacht hat.  
  
 Wenn die Eigenschaft [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) auf **adxactcommitbeibehaltenen** oder **adxactabortretribute**festgelegt ist, wird eine neue Transaktion gestartet, nachdem ein Commit oder Rollback einer Transaktion ausgeführt wurde. Verwenden Sie das **BeginTransComplete** -Ereignis, um alle außer dem ersten Transaktions Start Ereignis zu ignorieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans-, CommitTrans-und RollbackTrans-Methoden Beispiel (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [BeginTrans-, CommitTrans- und RollbackTrans-Methode (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
