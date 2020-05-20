---
title: ConnectComplete-und Disconnect-Ereignisse (ADO) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 88aa5ee6b1d4eabecb65323f557e4bf594da8629
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760326"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete- und Disconnect-Ereignis (ADO)
Das **ConnectComplete** -Ereignis wird aufgerufen, nachdem eine Verbindung gestartet wurde. Das **Disconnect** -Ereignis wird aufgerufen, nachdem eine Verbindung beendet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatus usenum](../../../ado/reference/ado-api/eventstatusenum.md) -Wert, der immer **adstatuusok**zurückgibt.  
  
 Wenn **ConnectComplete** aufgerufen wird, wird dieser Parameter auf **adStatus Cancel** festgelegt, wenn ein **WillConnect** -Ereignis einen Abbruch der ausstehenden Verbindung angefordert hat.  
  
 Bevor beide Ereignisse zurückgegeben werden, legen Sie diesen Parameter auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern. Das schließen und wieder öffnen der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) bewirkt jedoch, dass diese Ereignisse erneut auftreten.  
  
 *pConnection*  
 Das **Verbindungs** Objekt, für das dieses Ereignis gilt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)
