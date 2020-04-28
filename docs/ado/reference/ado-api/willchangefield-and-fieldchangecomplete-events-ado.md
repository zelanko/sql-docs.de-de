---
title: Ereignisse "WillChangeField" und "FieldChangeComplete" (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldChangeComplete
- Recordset::WillChangeField
- Recordset::FieldChangeComplete
- WillChangeField
helpviewer_keywords:
- WillChangeField event [ADO]
- fieldchangecomplete event [ADO]
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7484e2a57925cc22c83456c244dc67aded5cefd2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67945881"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>WillChangeField- und FieldChangeComplete-Ereignis (ADO)
Das Ereignis " **WillChangeField** " wird aufgerufen, bevor durch einen ausstehenden Vorgang der Wert von einem oder mehreren [Feld](../../../ado/reference/ado-api/field-object.md) Objekten im [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)geändert wird. Das Ereignis **FieldChangeComplete** wird aufgerufen, nachdem sich der Wert eines oder mehrerer **Feld** Objekte geändert hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *cFields*  
 Ein **Long** -Wert, der die Anzahl der **Feld** Objekte in *Feldern*angibt.  
  
 *Felder*  
 Der *Fields* -Parameter für " **WillChangeField**" ist ein Array von **Varianten** , das **Feld** Objekte mit den ursprünglichen Werten enthält. Für **FieldChangeComplete**ist der *Fields* -Parameter ein Array von **Varianten** , das **Feld** Objekte mit den geänderten Werten enthält.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von *adStatus* **adstatuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert.  
  
 Wenn " **WillChangeField** " aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war. Sie wird auf **adStatus-kandeny** festgelegt, wenn dieses Ereignis keinen Abbruch des ausstehenden Vorgangs anfordern kann.  
  
 Wenn **FieldChangeComplete** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, oder auf **adstatuuserrorsoccurrred** , wenn der Vorgang fehlgeschlagen ist.  
  
 Legen Sie diesen Parameter vor der Rückgabe von " **WillChangeField** " auf " **adStatus Cancel** " fest, um den Abbruch des ausstehenden Vorgangs anzufordern.  
  
 Legen Sie diesen Parameter vor der Rückgabe von **FieldChangeComplete** auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt. Das **Recordset** , für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft festlegen und die [Update](../../../ado/reference/ado-api/update-method.md) -Methode mit Feld-und Wert Array Parametern aufrufen, kann ein Ereignis vom Typ " **WillChangeField** " oder " **FieldChangeComplete** " auftreten  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)
