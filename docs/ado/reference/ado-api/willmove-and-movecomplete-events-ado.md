---
description: WillMove- und MoveComplete-Ereignis (ADO)
title: Ereignisse "WillMove" und "MoveComplete" (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::MoveComplete
- WillMove
- MoveComplete
- Recordset::WillMove
helpviewer_keywords:
- MoveComplete event [ADO]
- WillMove event [ADO]
ms.assetid: 1a3d1042-4f30-4526-a0c7-853c242496db
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dbc74fbca54ab1bdafb3c0f2ba941aee49f2213
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776849"
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove- und MoveComplete-Ereignis (ADO)
Das Ereignis " **WillMove** " wird aufgerufen, bevor die aktuelle Position im [Recordset](./recordset-object-ado.md)durch einen ausstehenden Vorgang geändert wird. Das Ereignis " **muvecomplete** " wird aufgerufen, nachdem sich die aktuelle Position im **Recordset** geändert hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [eventreasonenumerationswert](./eventreasonenum.md) , der den Grund für dieses Ereignis angibt. Der Wert kann " **adrsnmovefirst**", " **adrsnmovelast**", " **adrsnmovenext**", " **adrsnmoveprevious**", " **adrsnmove**" oder " **adrsnrequery**" lauten.  
  
 *pError*  
 Ein [Fehler](./error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist der-Parameter nicht festgelegt.  
  
 *adStatus*  
 Ein [eventstatusenum](./eventstatusenum.md) -Statuswert.  
  
 Wenn " **WillMove** " aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war. Sie wird auf **adStatus-kandeny** festgelegt, wenn dieses Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn " **muvecomplete** " aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, oder auf " **adstatuuserrorsoccurrred** ", wenn der Vorgang fehlgeschlagen ist.  
  
 Legen Sie diesen Parameter auf **adStatus Cancel** fest, bevor Sie " **WillMove** " zurückgibt, um den Abbruch des ausstehenden Vorgangs anzufordern, oder legen Sie diesen Parameter auf " **adStatus-unwantedevent** " fest, um spätere Benachrichtigungen zu verhindern.  
  
 Legen Sie für diesen Parameter vor der Rückgabe von " **uvecomplete** " den Wert **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern  
  
 *pRecordset*  
 Ein [Recordset](./recordset-object-ado.md) -Objekt. Das **Recordset** , für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Das Ereignis " **WillMove** " oder " **MoveComplete** " kann aufgrund der folgenden **recordsetvorgänge** auftreten: [Öffnen](./open-method-ado-recordset.md), [verschieben](./move-method-ado.md), [MoveFirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](./addnew-method-ado.md)und [Requery](./requery-method.md). Diese Ereignisse können aufgrund der folgenden Eigenschaften auftreten: " [Filter](./filter-property.md)", " [Index](./index-property.md)", " [Bookmark](./bookmark-property-ado.md)", " [AbsolutePage](./absolutepage-property-ado.md)" und " [AbsolutePosition](./absoluteposition-property-ado.md)". Diese Ereignisse treten auch dann auf, wenn für ein untergeordnetes **Recordset** eine Verbindung mit **recordsetereignissen** besteht und das übergeordnete **Recordset** verschoben wird.  
  
 Sie müssen den *adStatus* -Parameter für jeden möglichen *adReason* -Wert auf **adStatusUnwantedEvent** festlegen, um die Ereignis Benachrichtigung für jedes Ereignis vollständig zu beenden, das einen *adReason* -Parameter enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](./ado-events-model-example-vc.md)   
 [ADO-Ereignis Handler-Zusammenfassung](../../guide/data/ado-event-handler-summary.md)   
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)