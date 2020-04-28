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
ms.openlocfilehash: 9fc1ac74e7e3d521bae587957f5f95771e5a5268
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67945859"
---
# <a name="willconnect-event-ado"></a>WillConnect-Ereignis (ADO)
Das Ereignis " **WillConnect** " wird aufgerufen, bevor eine Verbindung gestartet wird.  
  
 **Gilt für:** [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine **Zeichenfolge** , die Verbindungsinformationen für die ausstehende Verbindung enthält.  
  
 *UserID*  
 Eine **Zeichen** Folge, die einen Benutzernamen für die ausstehende Verbindung enthält.  
  
 *Kennwort*  
 Eine **Zeichenfolge** , die ein Kennwort für die ausstehende Verbindung enthält.  
  
 *Optionen*  
 Ein **Long** -Wert, der angibt, wie der Anbieter *ConnectionString*auswerten soll. Ihre einzige Option ist **adasyncopen**.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert.  
  
 Wenn dieses Ereignis aufgerufen wird, wird dieser Parameter standardmäßig auf **adstatuusok** festgelegt. Sie wird auf **adStatus-kandeny** festgelegt, wenn das Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Bevor dieses Ereignis zurückkehrt, legen Sie diesen Parameter auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern. Legen Sie diesen Parameter auf **adStatus Cancel** fest, um den Verbindungsvorgang anzufordern, der den Abbruch dieser Benachrichtigung verursacht hat.  
  
 *pConnection*  
 Das [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt, für das diese Ereignis Benachrichtigung gilt. Änderungen an den Parametern der **Verbindung** durch den **WillConnect** -Ereignishandler haben keine Auswirkung auf die **Verbindung**.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn " **WillConnect** " aufgerufen wird, werden die Parameter " *ConnectionString*", " *UserID*", " *Password*" und " *options* " auf die Werte festgelegt, die durch den Vorgang festgelegt wurden, der dieses Ereignis verursacht hat (ausstehende Verbindung) **WillConnect** gibt möglicherweise eine Anforderung zurück, dass die ausstehende Verbindung abgebrochen wurde.  
  
 Wenn dieses Ereignis abgebrochen wird, wird **ConnectComplete** aufgerufen, wobei der *adStatus* -Parameter auf **adstatuserrorsoccurrred**festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)
