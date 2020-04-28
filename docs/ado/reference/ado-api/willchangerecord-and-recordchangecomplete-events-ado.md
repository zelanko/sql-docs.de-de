---
title: WillChangeRecord-und RecordChangeComplete-Ereignis (ADO) | Microsoft-Dokumentation
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
ms.openlocfilehash: 6e632db34fbbacbee61cd943067052af27a8cfe8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938676"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>WillChangeRecord- und RecordChangeComplete-Ereignis (ADO)
Das Ereignis **WillChangeRecord** wird aufgerufen, bevor ein oder mehrere Datensätze (Zeilen) in der [recordsetänderung](../../../ado/reference/ado-api/recordset-object-ado.md) geändert werden. Das **RecordChangeComplete** -Ereignis wird aufgerufen, nachdem sich ein oder mehrere Datensätze geändert haben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [eventreasonenumerationswert](../../../ado/reference/ado-api/eventreasonenum.md) , der den Grund für dieses Ereignis angibt. Der Wert kann " **adrsnaddnew**", " **adrsndelete**", " **adrsnupdate**", " **adrsnundoupdate**", " **adrsnundoaddnew**", "adrsnundodelete" oder " **adrsnfirstchange**" lauten. **adRsnUndoDelete**  
  
 *cRecords*  
 Ein **Long** -Wert, der die Anzahl der geänderten Datensätze angibt (betroffen).  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert.  
  
 Wenn **WillChangeRecord** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war. Sie wird auf **adStatus-kandeny** festgelegt, wenn dieses Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **RecordChangeComplete** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, oder auf **adstatuuserrorsoccurrred** , wenn der Vorgang fehlgeschlagen ist.  
  
 Legen Sie diesen Parameter vor der Rückgabe von " **WillChangeRecord** " auf " **adStatus Cancel** " fest, um den Abbruch des Vorgangs anzufordern, der dieses Ereignis verursacht hat, oder legen Sie diesen Parameter auf " **adstatueunwantedevent** " fest  
  
 Legen Sie diesen Parameter vor der Rückgabe von **RecordChangeComplete** auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt. Das **Recordset** , für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **WillChangeRecord** - **oder RecordChangeComplete** -Ereignis kann aufgrund der folgenden **recordsetvorgänge** für das erste geänderte Feld in einer Zeile auftreten: [Update](../../../ado/reference/ado-api/update-method.md), [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)und [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md). Der Wert des **Recordset** - [Cursor Typs](../../../ado/reference/ado-api/cursortype-property-ado.md) bestimmt, welche Vorgänge bewirken, dass die Ereignisse auftreten.  
  
 Während des **WillChangeRecord** -Ereignisses wird die **Recordset** - [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft auf **adFilterAffectedRecords**festgelegt. Diese Eigenschaft kann bei der Verarbeitung des Ereignisses nicht geändert werden.  
  
 Sie müssen den **adStatus** -Parameter für jeden möglichen **adReason** -Wert auf **adStatusUnwantedEvent** festlegen, um die Ereignis Benachrichtigung für jedes Ereignis vollständig zu beenden, das einen **adReason** -Parameter enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)
