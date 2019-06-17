---
title: WillConnect-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 01b5c20668f97c80ae5abdcbb213914c012c7359
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710058"
---
# <a name="willconnect-event-ado"></a>WillConnect-Ereignis (ADO)
Die **WillConnect** Ereignis wird immer dann aufgerufen, bevor eine Verbindung gestartet wird.  
  
 **Gilt für:** [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Ein **Zeichenfolge** , die Verbindungsinformationen für die ausstehende Verbindung enthält.  
  
 *UserID*  
 Ein **Zeichenfolge** , einen Benutzernamen für die ausstehende Verbindung enthält.  
  
 *Kennwort*  
 Ein **Zeichenfolge** , ein Kennwort für die ausstehende Verbindung enthält.  
  
 *Options*  
 Ein **lange** Wert, der angibt, wie der Anbieter auswerten soll die *"ConnectionString"* . Ihre einzige Option **AdAsyncOpen**.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 Wenn dieses Ereignis aufgerufen wird, wird dieser Parameter festgelegt, um **AdStatusOK** standardmäßig. Es wird festgelegt, um **AdStatusCantDeny** Wenn das Ereignis auf Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Bevor Sie dieses Ereignis zurückgegeben wird, legen Sie diesen Parameter auf **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern. Legen Sie diesen Parameter **AdStatusCancel** die Verbindungsoperation anfordern, die diese Benachrichtigung Abbruch verursacht hat.  
  
 *pConnection*  
 Die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt für die dieser ereignisbenachrichtigung angewendet wird. Änderungen an den Parametern des der **Verbindung** durch die **WillConnect** -Ereignishandler hat keine Auswirkungen auf die **Verbindung**.  
  
## <a name="remarks"></a>Hinweise  
 Wenn **WillConnect** aufgerufen wird, die *"ConnectionString"* , *"UserID"* , *Kennwort*, und *Optionen* Parameter werden festgelegt, auf die Werte, die hergestellt, indem der Vorgang, der dieses Ereignis (die Verbindung steht aus), und kann geändert werden, bevor das Ereignis zurückgegeben. **WillConnect** möglicherweise zurück, eine Anforderung, dass die ausstehende verbindungsanforderung abgebrochen werden.  
  
 Wenn dieses Ereignis abgebrochen wird, **ConnectComplete** wird mit aufgerufen werden, dessen *AdStatus* Parametersatz zu **AdStatusErrorsOccurred**.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
