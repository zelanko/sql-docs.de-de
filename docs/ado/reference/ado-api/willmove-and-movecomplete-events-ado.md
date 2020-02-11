---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c91f3166b493ac1e2fada3e759cb107e34c7ca81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67945914"
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove- und MoveComplete-Ereignis (ADO)
Das Ereignis " **WillMove** " wird aufgerufen, bevor die aktuelle Position im [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)durch einen ausstehenden Vorgang geändert wird. Das Ereignis " **muvecomplete** " wird aufgerufen, nachdem sich die aktuelle Position im **Recordset** geändert hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [eventreasonenumerationswert](../../../ado/reference/ado-api/eventreasonenum.md) , der den Grund für dieses Ereignis angibt. Der Wert kann " **adrsnmovefirst**", " **adrsnmovelast**", " **adrsnmovenext**", " **adrsnmoveprevious**", " **adrsnmove**" oder " **adrsnrequery**" lauten.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist der-Parameter nicht festgelegt.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert.  
  
 Wenn " **WillMove** " aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war. Sie wird auf **adStatus-kandeny** festgelegt, wenn dieses Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn " **muvecomplete** " aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, oder auf " **adstatuuserrorsoccurrred** ", wenn der Vorgang fehlgeschlagen ist.  
  
 Legen Sie diesen Parameter auf **adStatus Cancel** fest, bevor Sie " **WillMove** " zurückgibt, um den Abbruch des ausstehenden Vorgangs anzufordern, oder legen Sie diesen Parameter auf " **adStatus-unwantedevent** " fest, um spätere Benachrichtigungen zu verhindern.  
  
 Legen Sie für diesen Parameter vor der Rückgabe von " **uvecomplete** " den Wert **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern  
  
 *precordset*  
 Ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt. Das **Recordset** , für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Das Ereignis " **WillMove** " oder " **MoveComplete** " kann aufgrund der folgenden **recordsetvorgänge** auftreten: [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md), [verschieben](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)und [Requery](../../../ado/reference/ado-api/requery-method.md). Diese Ereignisse können aufgrund der folgenden Eigenschaften auftreten: " [Filter](../../../ado/reference/ado-api/filter-property.md)", " [Index](../../../ado/reference/ado-api/index-property.md)", " [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md)", " [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)" und " [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)". Diese Ereignisse treten auch dann auf, wenn für ein untergeordnetes **Recordset** eine Verbindung mit **recordsetereignissen** besteht und das übergeordnete **Recordset** verschoben wird.  
  
 Sie müssen den *adStatus* -Parameter für jeden möglichen *adReason* -Wert auf **adStatusUnwantedEvent** festlegen, um die Ereignis Benachrichtigung für jedes Ereignis vollständig zu beenden, das einen *adReason* -Parameter enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
