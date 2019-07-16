---
title: WillMove- und MoveComplete-Ereignis (ADO) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945914"
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove- und MoveComplete-Ereignis (ADO)
Die **WillMove** Ereignis wird immer dann aufgerufen, bevor Sie ein ausstehender Vorgang ändert sich die aktuelle Position in der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Die **MoveComplete** Ereignis wird aufgerufen, nachdem die aktuelle Position in der **Recordset** Änderungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) -Wert, der den Grund für dieses Ereignis angibt. Die Werte sind möglich **AdRsnMoveFirst**, **AdRsnMoveLast**, **AdRsnMoveNext**, **AdRsnMovePrevious**, **AdRsnMove** , oder **AdRsnRequery**.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird beschrieben, wenn aufgetretenen Fehlers der Wert des *AdStatus* ist **AdStatusErrorsOccurred**; andernfalls wird der Parameter nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 Wenn **WillMove** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war. Es wird festgelegt, um **AdStatusCantDeny** Wenn dieses Ereignis auf Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **MoveComplete** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war, oder mit **AdStatusErrorsOccurred** Wenn die Fehler bei Vorgang.  
  
 Vor dem **WillMove** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusCancel** Anforderung Abbrechen des ausstehenden Vorgangs, oder legen Sie diesen Parameter **AdStatusUnwantedEvent** um nachfolgende Benachrichtigungen zu verhindern.  
  
 Vor dem **MoveComplete** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt. Die **Recordset** für die dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein **WillMove** oder **MoveComplete** Ereignis kann auftreten, aufgrund der folgenden **Recordset** Vorgänge: [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md), [verschieben](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), und [Requery](../../../ado/reference/ado-api/requery-method.md). Diese Ereignisse können auftreten, aufgrund der folgenden Eigenschaften: [Filter](../../../ado/reference/ado-api/filter-property.md), [Index](../../../ado/reference/ado-api/index-property.md), [Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md), und [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md). Diese Ereignisse auch auftreten, wenn ein Kind **Recordset** hat **Recordset** Ereignisse, die Verbindung hergestellt und das übergeordnete Element **Recordset** verschoben wird.  
  
 Müssen Sie festlegen, die *AdStatus* Parameter **AdStatusUnwantedEvent** für jeden möglichen *AdReason* Wert, um die ereignisbenachrichtigung für jedes Ereignis vollständig zu beenden, enthält eine *AdReason* Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
