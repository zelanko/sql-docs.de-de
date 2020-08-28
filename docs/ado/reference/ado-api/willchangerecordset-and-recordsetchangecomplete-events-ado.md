---
description: WillChangeRecordset- und RecordsetChangeComplete-Ereignis (ADO)
title: WillChangeRecordset-und RecordsetChangeComplete-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c3066ebce2f1f3e96404e933af1c39ad0fdd2659
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987801"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>WillChangeRecordset- und RecordsetChangeComplete-Ereignis (ADO)
Das Ereignis " **WillChangeRecordset** " wird aufgerufen, bevor das [Recordset](./recordset-object-ado.md)durch einen ausstehenden Vorgang geändert wird. Das **RecordsetChangeComplete** -Ereignis wird aufgerufen, nachdem das **Recordset** geändert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *adReason*  
 Ein [eventreasonenumerationswert](./eventreasonenum.md) , der den Grund für dieses Ereignis angibt. Der Wert kann **adrsnrequery**, **adrsnresynch**, **adrsnclose**, **adrsnopen**lauten.  
  
 *adStatus*  
 Ein [eventstatusenum](./eventstatusenum.md) -Statuswert.  
  
 Wenn **WillChangeRecordset** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war. Sie wird auf **adStatus-kandeny** festgelegt, wenn dieses Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **RecordsetChangeComplete** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, **adstatuuserrorsoccurrred** , wenn der Vorgang fehlgeschlagen ist, oder **adStatus Cancel** , wenn der Vorgang abgebrochen wurde, der dem zuvor akzeptierten Ereignis " **WillChangeRecordset** " zugeordnet ist.  
  
 Legen Sie diesen Parameter vor der Rückgabe von " **WillChangeRecordset** " auf " **adStatus Cancel** " fest, um den Abbruch des ausstehenden Vorgangs anzufordern, oder legen Sie diesen Parameter auf "adstatufeunwantedevent" fest, um nachfolgende Benachrichtigungen  
  
 Bevor " **WillChangeRecordset** " oder " **RecordsetChangeComplete** " zurückgegeben wird, legen Sie diesen Parameter auf **adstatuingunwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern  
  
 *pError*  
 Ein [Fehler](./error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt. Das **Recordset** , für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein " **WillChangeRecordset** "-oder " **RecordsetChangeComplete** "-Ereignis kann aufgrund der **Recordset** [-oder](./requery-method.md) [Open](./open-method-ado-recordset.md) -Methoden auftreten.  
  
 Wenn der Anbieter keine Lesezeichen unterstützt, tritt jedes Mal eine **recordsetchange** -Ereignis Benachrichtigung auf, wenn neue Zeilen vom Anbieter abgerufen werden. Die Häufigkeit dieses Ereignisses hängt von der **recordsetcachesize** -Eigenschaft ab.  
  
 Sie müssen den **adStatus** -Parameter für jeden möglichen **adReason** -Wert auf **adStatusUnwantedEvent** festlegen, um die Ereignis Benachrichtigung für jedes Ereignis vollständig zu beenden, das einen **adReason** -Parameter enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](./ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../guide/data/ado-event-handler-summary.md)