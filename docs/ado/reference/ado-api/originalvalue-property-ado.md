---
description: OriginalValue-Eigenschaft (ADO)
title: OriginalValue-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
author: rothja
ms.author: jroth
ms.openlocfilehash: 13353013575db87f5ec30ceb8cf4a5aab6a06079
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443122"
---
# <a name="originalvalue-property-ado"></a>OriginalValue-Eigenschaft (ADO)
Gibt den Wert eines [Felds](../../../ado/reference/ado-api/field-object.md) an, das im Datensatz vorhanden war, bevor Änderungen vorgenommen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Variant** -Wert zurück, der den Wert eines Felds vor einer Änderung darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die Eigenschaft **OriginalValue** , um den ursprünglichen Feldwert für ein Feld aus dem aktuellen Datensatz zurückzugeben.  
  
 Im *sofortigen Update Modus* (in dem der Anbieter Änderungen in die zugrunde liegende Datenquelle schreibt, nachdem Sie die [Update](../../../ado/reference/ado-api/update-method.md) -Methode aufgerufen haben), gibt die **OriginalValue** -Eigenschaft den Feldwert zurück, der vor allen Änderungen vorhanden war (d. h. seit dem letzten **Aktualisierungs** Methodenaufrufe). Dies ist derselbe Wert, den die [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) -Methode verwendet, um die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft zu ersetzen.  
  
 Im *Batch Aktualisierungs Modus* (in dem der Anbieter mehrere Änderungen zwischenspeichert und Sie nur dann in die zugrunde liegende Datenquelle schreibt, wenn Sie die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methode aufrufen), gibt die **OriginalValue** -Eigenschaft den Feldwert zurück, der vor allen Änderungen vorhanden war (d.h. seit dem letzten **UpdateBatch** -Methodenaufrufe). Dies ist derselbe Wert, den die [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) -Methode verwendet, um die **value** -Eigenschaft zu ersetzen. Wenn Sie diese Eigenschaft mit der [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) -Eigenschaft verwenden, können Sie Konflikte lösen, die sich aus Batch Updates ergeben.  
  
## <a name="record"></a>Datensatz  
 Bei [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekten ist die **OriginalValue** -Eigenschaft für Felder, die vor dem Aufrufen des [Updates](../../../ado/reference/ado-api/update-method.md) hinzugefügt werden, leer.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OriginalValue-und UnderlyingValue-Eigenschaften (Beispiel) (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue-und UnderlyingValue-Eigenschaften Beispiel (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue-Eigenschaft](../../../ado/reference/ado-api/underlyingvalue-property.md)
