---
title: ConnectComplete und Disconnect-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2f84f89b1ace38350261d461993bf6f89bc155c1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698754"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete- und Disconnect-Ereignis (ADO)
Die **ConnectComplete** Ereignis wird immer dann aufgerufen, nachdem eine Verbindung gestartet. Die **trennen** Ereignis wird immer dann aufgerufen, nachdem eine Verbindung beendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird beschrieben, den aufgetretenen Wenn der Wert des *AdStatus* ist **AdStatusErrorsOccurred**; andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Wert, der immer gibt **AdStatusOK**.  
  
 Wenn **ConnectComplete** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusCancel** Wenn eine **WillConnect** Ereignis hat die ausstehende Verbindung Abbruch angefordert.  
  
 Vor der beiden Ereignisse zurückgibt, legen Sie diesen Parameter auf **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern. Allerdings schließen und erneuten Öffnen der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) bewirkt, dass diese Ereignisse erneut auftreten.  
  
 *pConnection*  
 Die **Verbindung** -Objekt für die dieses Ereignis gilt.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
