---
title: EndOfRecordset-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 414094da95076a7fb3781877645c5d43a03e6a7f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698216"
---
# <a name="endofrecordset-event-ado"></a>EndOfRecordset-Ereignis (ADO)
Die **EndOfRecordset** Ereignis wird aufgerufen, wenn versucht wird, wechseln auf eine Zeile nach dem Ende der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *fMoreData*  
 Ein **VARIANT_BOOL** -Wert, wenn auf VARIANT_TRUE festgelegt ist, gibt an, um weitere Zeilen hinzugefügt wurden die **Recordset**.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 Wenn **EndOfRecordset** wird aufgerufen, wird dieser Parameter auf festgelegt **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war. Es wird festgelegt, um **AdStatusCantDeny** Wenn dieses Ereignis Abbruch des Vorgangs nicht anfordern kann, die dieses Ereignis verursacht hat.  
  
 Vor dem **EndOfRecordset** zurückgegeben wird, legen Sie diesen Parameter zu **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein **Recordset** Objekt. Die **Recordset** für die dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein **EndOfRecordset** Ereignis kann auftreten, wenn die [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) -Vorgang fehl.  
  
 Dieser Ereignishandler wird aufgerufen, wenn versucht wird, verschieben Sie nach dem Ende der **Recordset** -Objekt, z. B. als Ergebnis eines Aufrufs **MoveNext**. Jedoch während in diesem Fall kann mehrere Datensätze aus einer Datenbank abgerufen und fügen sie am Ende der **Recordset**. In diesem Fall legen *fMoreData* auf VARIANT_TRUE fest, und Rückgabe von **EndOfRecordset**. Rufen Sie anschließend **MoveNext** erneut aus, um die neu abgerufenen Datensätze zugreifen.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
