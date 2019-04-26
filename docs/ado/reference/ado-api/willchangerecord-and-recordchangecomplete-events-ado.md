---
title: WillChangeRecord- und RecordChangeComplete-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- RecordChangeComplete
- Recordset::WillChangeRecord
- WillChangeRecord
- Recordset::RecordChangeComplete
helpviewer_keywords:
- WillChangeRecord event [ADO]
- recordchangecomplete event [ADO]
ms.assetid: cbc369fd-63af-4a7d-96ae-efa91b78ca69
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd31a75a45bd38bda04655bbb47daca09714803c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642889"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>WillChangeRecord- und RecordChangeComplete-Ereignis (ADO)
Die **WillChangeRecord** Ereignis wird aufgerufen, bevor Sie einen oder mehrere Datensätze (Zeilen) in der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ändern. Die **RecordChangeComplete** Ereignis wird aufgerufen, nachdem eine oder mehrere Datensätze zu ändern.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) -Wert, der den Grund für dieses Ereignis angibt. Die Werte sind möglich **AdRsnAddNew**, **AdRsnDelete**, **AdRsnUpdate**, **AdRsnUndoUpdate**, **AdRsnUndoAddNew**, **AdRsnUndoDelete**, oder **AdRsnFirstChange**.  
  
 *cRecords*  
 Ein **lange** Wert, der die Anzahl der Datensätze, die ändern (betroffen) angibt.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird beschrieben, den aufgetretenen Wenn der Wert des *AdStatus* ist **AdStatusErrorsOccurred**; andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 Wenn **WillChangeRecord** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war. Es wird festgelegt, um **AdStatusCantDeny** Wenn dieses Ereignis auf Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **RecordChangeComplete** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war, oder mit **AdStatusErrorsOccurred** Wenn der Vorgang ist fehlgeschlagen.  
  
 Vor dem **WillChangeRecord** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusCancel** auf Anforderung Abbruch des Vorgangs, der dieses Ereignis verursacht hat, oder legen diesen Parameter auf  **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern.  
  
 Vor dem **RecordChangeComplete** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein **Recordset** Objekt. Die **Recordset** für die dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein **WillChangeRecord** oder **RecordChangeComplete** Ereignis kann auftreten, für das erste geänderte Feld in einer Zeile folgende Ursachen **Recordset** Vorgänge: [Update](../../../ado/reference/ado-api/update-method.md), [löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), und [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md). Der Wert des der **Recordset** [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) bestimmt, welche Vorgänge dazu führen, dass die Ereignisse auftreten.  
  
 Während der **WillChangeRecord** -Ereignis, das **Recordset** [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaftensatz auf **AdFilterAffectedRecords**. Diese Eigenschaft kann nicht geändert werden, während der Verarbeitung des Ereignisses.  
  
 Sie müssen festlegen, die **AdStatus** Parameter **AdStatusUnwantedEvent** für jeden möglichen **AdReason** Wert, der die ereignisbenachrichtigung für jedes Ereignis vollständig beendet wurde, die enthält ein **AdReason** Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
