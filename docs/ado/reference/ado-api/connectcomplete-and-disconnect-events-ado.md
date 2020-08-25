---
description: ConnectComplete- und Disconnect-Ereignis (ADO)
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
ms.openlocfilehash: 47fa12ef5fe4d678107254923b6d6cfa569e0db2
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776029"
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
 Ein [Fehler](./error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatus usenum](./eventstatusenum.md) -Wert, der immer **adstatuusok**zurückgibt.  
  
 Wenn **ConnectComplete** aufgerufen wird, wird dieser Parameter auf **adStatus Cancel** festgelegt, wenn ein **WillConnect** -Ereignis einen Abbruch der ausstehenden Verbindung angefordert hat.  
  
 Bevor beide Ereignisse zurückgegeben werden, legen Sie diesen Parameter auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern. Das schließen und wieder öffnen der [Verbindung](./connection-object-ado.md) bewirkt jedoch, dass diese Ereignisse erneut auftreten.  
  
 *pConnection*  
 Das **Verbindungs** Objekt, für das dieses Ereignis gilt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](./ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../guide/data/ado-event-handler-summary.md)