---
title: WillChangeRecordset- und RecordsetChangeComplete-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::RecordsetChangeComplete
- RecordsetChangeComplete
- Recordset::WillChangeRecordset
- WillChangeRecordset
helpviewer_keywords:
- RecordsetChangeComplete event [ADO]
- WillChangeRecordset event [ADO]
ms.assetid: d5d44659-e0d9-46d9-a297-99c43555082f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ed1c7a9f1ed86359eef75fdaf13c9e40d838f3f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642444"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>WillChangeRecordset- und RecordsetChangeComplete-Ereignis (ADO)
Die **WillChangeRecordset** Ereignis wird immer dann aufgerufen, bevor Sie ein ausstehender Vorgang ändert die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Die **RecordsetChangeComplete** Ereignis wird aufgerufen, nachdem die **Recordset** hat sich geändert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) -Wert, der den Grund für dieses Ereignis angibt. Die Werte sind möglich **AdRsnRequery**, **AdRsnResynch**, **AdRsnClose**, **AdRsnOpen**.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 Wenn **WillChangeRecordset** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war. Es wird festgelegt, um **AdStatusCantDeny** Wenn dieses Ereignis auf Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **RecordsetChangeComplete** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war, **AdStatusErrorsOccurred** Wenn der Vorgang fehlgeschlagen ist, oder **AdStatusCancel** zuvor akzeptierten Vorgangs zugeordnet **WillChangeRecordset** Ereignis abgebrochen wurde.  
  
 Vor dem **WillChangeRecordset** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusCancel** Anforderung Abbrechen des ausstehenden Vorgangs, oder legen Sie diesen Parameter, zu verhindern, dass nachfolgende Benachrichtigungen.  
  
 Vor dem **WillChangeRecordset** oder **RecordsetChangeComplete** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird beschrieben, den aufgetretenen Wenn der Wert des *AdStatus* ist **AdStatusErrorsOccurred**; andernfalls ist es nicht festgelegt.  
  
 *pRecordset*  
 Ein **Recordset** Objekt. Die **Recordset** für die dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein **WillChangeRecordset** oder **RecordsetChangeComplete** Ereignis kann auftreten, da die **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) oder [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methoden.  
  
 Wenn der Anbieter keine Lesezeichen unterstützt eine **RecordsetChange** ereignisbenachrichtigung tritt jedes Mal, die neue Zeilen, die vom Anbieter abgerufen werden. Die Häufigkeit dieses Ereignisses hängt die **RecordsetCacheSize** Eigenschaft.  
  
 Sie müssen festlegen, die **AdStatus** Parameter **AdStatusUnwantedEvent** für jeden möglichen **AdReason** Wert, der die ereignisbenachrichtigung für jedes Ereignis vollständig beendet wurde, die enthält ein **AdReason** Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
