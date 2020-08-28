---
description: WillChangeRecord- und RecordChangeComplete-Ereignis (ADO)
title: WillChangeRecord-und RecordChangeComplete-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e22e922a240643d499408dda3941fdf638a529ff
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987861"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>WillChangeRecord- und RecordChangeComplete-Ereignis (ADO)
Das Ereignis **WillChangeRecord** wird aufgerufen, bevor ein oder mehrere Datensätze (Zeilen) in der [recordsetänderung](./recordset-object-ado.md) geändert werden. Das **RecordChangeComplete** -Ereignis wird aufgerufen, nachdem sich ein oder mehrere Datensätze geändert haben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [eventreasonenumerationswert](./eventreasonenum.md) , der den Grund für dieses Ereignis angibt. Der Wert kann " **adrsnaddnew**", " **adrsndelete**", " **adrsnupdate**", " **adrsnundoupdate**", " **adrsnundoaddnew**", "adrsnundodelete" oder " **adrsnfirstchange**" lauten. **adRsnUndoDelete**  
  
 *cRecords*  
 Ein **Long** -Wert, der die Anzahl der geänderten Datensätze angibt (betroffen).  
  
 *pError*  
 Ein [Fehler](./error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [eventstatusenum](./eventstatusenum.md) -Statuswert.  
  
 Wenn **WillChangeRecord** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war. Sie wird auf **adStatus-kandeny** festgelegt, wenn dieses Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **RecordChangeComplete** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, oder auf **adstatuuserrorsoccurrred** , wenn der Vorgang fehlgeschlagen ist.  
  
 Legen Sie diesen Parameter vor der Rückgabe von " **WillChangeRecord** " auf " **adStatus Cancel** " fest, um den Abbruch des Vorgangs anzufordern, der dieses Ereignis verursacht hat, oder legen Sie diesen Parameter auf " **adstatueunwantedevent** " fest  
  
 Legen Sie diesen Parameter vor der Rückgabe von **RecordChangeComplete** auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt. Das **Recordset** , für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **WillChangeRecord** - **oder RecordChangeComplete** -Ereignis kann aufgrund der folgenden **recordsetvorgänge** für das erste geänderte Feld in einer Zeile auftreten: [Update](./update-method.md), [Delete](./delete-method-ado-recordset.md), [CancelUpdate](./cancelupdate-method-ado.md), [AddNew](./addnew-method-ado.md), [UpdateBatch](./updatebatch-method.md)und [CancelBatch](./cancelbatch-method-ado.md). Der Wert des **Recordset** - [Cursor Typs](./cursortype-property-ado.md) bestimmt, welche Vorgänge bewirken, dass die Ereignisse auftreten.  
  
 Während des **WillChangeRecord** -Ereignisses wird die **Recordset** - [Filter](./filter-property.md) Eigenschaft auf **adFilterAffectedRecords**festgelegt. Diese Eigenschaft kann bei der Verarbeitung des Ereignisses nicht geändert werden.  
  
 Sie müssen den **adStatus** -Parameter für jeden möglichen **adReason** -Wert auf **adStatusUnwantedEvent** festlegen, um die Ereignis Benachrichtigung für jedes Ereignis vollständig zu beenden, das einen **adReason** -Parameter enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](./ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../guide/data/ado-event-handler-summary.md)