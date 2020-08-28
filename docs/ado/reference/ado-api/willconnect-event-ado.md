---
description: WillConnect-Ereignis (ADO)
title: WillConnect-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 259ef55060d7968d9ec557c831412ad58609a6df
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987781"
---
# <a name="willconnect-event-ado"></a>WillConnect-Ereignis (ADO)
Das Ereignis " **WillConnect** " wird aufgerufen, bevor eine Verbindung gestartet wird.  
  
 **Gilt für:** [Verbindungs Objekt (ADO)](./connection-object-ado.md)  
  
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
 Ein [eventstatusenum](./eventstatusenum.md) -Statuswert.  
  
 Wenn dieses Ereignis aufgerufen wird, wird dieser Parameter standardmäßig auf **adstatuusok** festgelegt. Sie wird auf **adStatus-kandeny** festgelegt, wenn das Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Bevor dieses Ereignis zurückkehrt, legen Sie diesen Parameter auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern. Legen Sie diesen Parameter auf **adStatus Cancel** fest, um den Verbindungsvorgang anzufordern, der den Abbruch dieser Benachrichtigung verursacht hat.  
  
 *pConnection*  
 Das [Verbindungs](./connection-object-ado.md) Objekt, für das diese Ereignis Benachrichtigung gilt. Änderungen an den Parametern der **Verbindung** durch den **WillConnect** -Ereignishandler haben keine Auswirkung auf die **Verbindung**.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn " **WillConnect** " aufgerufen wird, werden die Parameter " *ConnectionString*", " *UserID*", " *Password*" und " *options* " auf die Werte festgelegt, die durch den Vorgang festgelegt wurden, der dieses Ereignis verursacht hat (ausstehende Verbindung) **WillConnect** gibt möglicherweise eine Anforderung zurück, dass die ausstehende Verbindung abgebrochen wurde.  
  
 Wenn dieses Ereignis abgebrochen wird, wird **ConnectComplete** aufgerufen, wobei der *adStatus* -Parameter auf **adstatuserrorsoccurrred**festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](./ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../guide/data/ado-event-handler-summary.md)