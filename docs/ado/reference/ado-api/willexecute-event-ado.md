---
description: WillExecute-Ereignis (ADO)
title: WillExecute-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillExecute
- Connection::WillExecute
helpviewer_keywords:
- WillExecute event [ADO]
ms.assetid: dd755e46-f589-48a3-93a9-51ff998d44b5
author: rothja
ms.author: jroth
ms.openlocfilehash: affe058e06d20ffec9c27a5f4a60812f6fee1b03
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776869"
---
# <a name="willexecute-event-ado"></a>WillExecute-Ereignis (ADO)
Das **WillExecute** -Ereignis wird aufgerufen, kurz bevor ein ausstehender Befehl für eine Verbindung ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Eine **Zeichenfolge** , die einen SQL-Befehl oder den Namen einer gespeicherten Prozedur enthält.  
  
 *CursorType*  
 Eine [CursorTypeEnum](./cursortypeenum.md) , die den Typ des Cursors für das **Recordset** enthält, das geöffnet wird. Mit diesem Parameter können Sie den Cursor während eines **Recordset**-Vorgangs für die[Open-Methode (ADO Recordset)](./open-method-ado-recordset.md) in einen beliebigen Typ ändern. " *Cursor Type* " wird für jeden anderen Vorgang ignoriert.  
  
 *LockType*  
 Eine [LockTypeEnum](./locktypeenum.md) , die den Sperrentyp für das zu öffnende **Recordset** enthält. Mit diesem Parameter können Sie die Sperre während eines **recordsetopen** -Vorgangs in einen beliebigen Typ ändern. Der *LockType* wird für jeden anderen Vorgang ignoriert.  
  
 *Optionen*  
 Ein **Long** -Wert, der Optionen angibt, die zum Ausführen des Befehls oder zum Öffnen des **Recordsets**verwendet werden können.  
  
 *adStatus*  
 Ein [eventstatusenum](./eventstatusenum.md) -Statuswert, der **adStatusCantDeny** oder **adStatusOK** sein kann, wenn dieses Ereignis aufgerufen wird. Wenn es **adStatus cantdeny**ist, fordert dieses Ereignis möglicherweise keinen Abbruch des ausstehenden Vorgangs an.  
  
 *pCommand*  
 Das [ADO-Objekt (Command Object)](./command-object-ado.md) , für das diese Ereignis Benachrichtigung gilt.  
  
 *pRecordset*  
 Das [Recordset-Objekt (ADO)](./recordset-object-ado.md) -Objekt, für das diese Ereignis Benachrichtigung gilt.  
  
 *pConnection*  
 Das [ADO-Objekt (Connection Object)](./connection-object-ado.md) , für das diese Ereignis Benachrichtigung gilt.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **WillExecute** -Ereignis kann aufgrund einer Verbindung auftreten.  [Execute-Methode (ADO-Verbindung)](./execute-method-ado-connection.md), [Execute-Methode (ADO-Befehl)](./execute-method-ado-command.md)oder [Open-Methode (ADO Recordset)](./open-method-ado-recordset.md) -Methode der *pconnection* -Parameter sollte immer einen gültigen Verweis auf ein **Verbindungs** Objekt enthalten. Wenn das Ereignis auf **Connection.Exeniedlich**zurückzuführen ist, werden die Parameter " *precordset* " und " *pcommand* " auf " **Nothing**" festgelegt. Wenn das Ereignis auf **Recordset. Open**zurückzuführen ist, verweist der *precordset* -Parameter auf das **Recordset** -Objekt, und der *pcommand* -Parameter wird auf " **Nothing**" festgelegt. Wenn das Ereignis auf **Command.Exeniedlich**zurückzuführen ist, verweist der *pcommand* -Parameter auf das **Command** -Objekt, und der *precordset* -Parameter wird auf " **Nothing**" festgelegt.  
  
 Mit **WillExecute** können Sie die ausstehenden Ausführungs Parameter überprüfen und ändern. Dieses Ereignis gibt möglicherweise eine Anforderung zurück, dass der ausstehende Befehl abgebrochen wurde.  
  
> [!NOTE]
>  Wenn die ursprüngliche Quelle für einen **Befehl** ein Stream ist, der von der Eigenschaft " [CommandStream-Eigenschaft (ADO)](./commandstream-property-ado.md) " angegeben wird, wird durch Zuweisen einer neuen Zeichenfolge zum " **WillExecute**"-_Quell_ Parameter die Quelle des **Befehls**geändert. Die **CommandStream** -Eigenschaft wird gelöscht, und die [CommandText-Eigenschaft (ADO)](./commandtext-property-ado.md) -Eigenschaft wird mit der neuen Quelle aktualisiert. Der von **CommandStream** angegebene ursprüngliche Stream wird freigegeben, und es kann nicht darauf zugegriffen werden.  
  
 Wenn der Dialekt der neuen Quell Zeichenfolge von der ursprünglichen Einstellung der Eigenschaft [Dialekt Eigenschaft](./dialect-property.md) abweicht (die dem **CommandStream**entsprach), muss der korrekte Dialekt angegeben werden, indem die Eigenschaft **Dialekt** des Befehls Objekts festgelegt wird, auf das von *pcommand*verwiesen wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](./ado-events-model-example-vc.md)   
 [ADO-Ereignis Handler-Zusammenfassung](../../guide/data/ado-event-handler-summary.md)   
 [Connection-Objekt (ADO)](./connection-object-ado.md)