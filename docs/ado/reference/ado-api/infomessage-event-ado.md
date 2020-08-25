---
description: InfoMessage-Ereignis (ADO)
title: Infomess-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 4cab5acb3ccedb9a1e42426da3701bc015f0ec2d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774829"
---
# <a name="infomessage-event-ado"></a>InfoMessage-Ereignis (ADO)
Das **infomess** -Ereignis wird immer dann aufgerufen, wenn während eines **ConnectionEvent** -Vorgangs eine Warnung auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *pError*  
 Ein [Fehler](./error-object.md) Objekt. Dieser Parameter enthält alle Fehler, die zurückgegeben werden. Wenn mehrere Fehler zurückgegeben werden, können Sie die **Fehler** Auflistung aufzählen, um Sie zu finden.  
  
 *adStatus*  
 Ein [eventstatusenum](./eventstatusenum.md) -Statuswert. Wenn eine Warnung auftritt, wird *adStatus* auf **adStatusOK** festgelegt, und die *Warnung enthält die* Warnung.  
  
 Bevor dieses Ereignis zurückkehrt, legen Sie diesen Parameter auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern.  
  
 *pConnection*  
 Ein [Verbindungs](./connection-object-ado.md) Objekt. Die Verbindung, für die die Warnung aufgetreten ist. Beispielsweise können Warnungen auftreten, wenn Sie ein **Verbindungs** Objekt öffnen oder einen [Befehl](./command-object-ado.md) für eine **Verbindung**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](./ado-events-model-example-vc.md)   
 [ADO-Ereignis Handler-Zusammenfassung](../../guide/data/ado-event-handler-summary.md)   
 [Connection-Objekt (ADO)](./connection-object-ado.md)