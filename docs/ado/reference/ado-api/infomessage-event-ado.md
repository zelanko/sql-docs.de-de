---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 25eef06b7e25538cb874d99af98aee95495b95ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932334"
---
# <a name="infomessage-event-ado"></a>InfoMessage-Ereignis (ADO)
Das **infomess** -Ereignis wird immer dann aufgerufen, wenn während eines **ConnectionEvent** -Vorgangs eine Warnung auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Dieser Parameter enthält alle Fehler, die zurückgegeben werden. Wenn mehrere Fehler zurückgegeben werden, können Sie die **Fehler** Auflistung aufzählen, um Sie zu finden.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert. Wenn eine Warnung auftritt, wird *adStatus* auf **adStatusOK** festgelegt, und die *Warnung enthält die* Warnung.  
  
 Bevor dieses Ereignis zurückkehrt, legen Sie diesen Parameter auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern.  
  
 *pConnection*  
 Ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Die Verbindung, für die die Warnung aufgetreten ist. Beispielsweise können Warnungen auftreten, wenn Sie ein **Verbindungs** Objekt öffnen oder einen [Befehl](../../../ado/reference/ado-api/command-object-ado.md) für eine **Verbindung**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
