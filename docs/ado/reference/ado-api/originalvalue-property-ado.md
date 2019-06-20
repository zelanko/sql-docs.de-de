---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e9a576220d7771ed539765da2947f6a7cc750f64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66706927"
---
# <a name="originalvalue-property-ado"></a>OriginalValue-Eigenschaft (ADO)
Gibt den Wert des einem [Feld](../../../ado/reference/ado-api/field-object.md) , die im Datensatz vorhanden waren, bevor Änderungen vorgenommen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variant** -Wert, der den Wert eines Felds vor jeder Änderung darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **OriginalValue** Eigenschaft, die den ursprünglichen Feldwert für ein Feld aus dem aktuellen Datensatz zurückgegeben.  
  
 In *sofortupdatemodus* (in dem der Anbieter schreibt Änderungen in der zugrunde liegenden Datenquelle nach dem Aufrufen der [aktualisieren](../../../ado/reference/ado-api/update-method.md) Methode), wird die **OriginalValue** -Eigenschaft gibt der Wert des Felds, die vor Änderungen vorhanden waren (d. h. seit dem letzten **Update** Methodenaufruf). Dies entspricht dem Wert, der [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) Methode verwendet, um das Ersetzen der [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft.  
  
 In *Update Batchmodus* (in dem der Anbieter speichert mehrere Änderungen, und sie in der zugrunde liegenden Datenquelle schreibt, nur bei Aufruf der [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode), wird die **OriginalValue** Eigenschaft gibt den Wert des Felds, die vor Änderungen vorhanden waren (d. h. seit dem letzten **UpdateBatch** Methodenaufruf). Dies entspricht dem Wert, der [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) Methode verwendet, um das Ersetzen der **Wert** Eigenschaft. Bei Verwendung dieser Eigenschaft mit dem [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) -Eigenschaft, können Sie Konflikte von BatchUpdates beheben.  
  
## <a name="record"></a>Datensatz  
 Für [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekte, die **OriginalValue** Eigenschaft ist für Felder hinzugefügt, bevor leer, [Update](../../../ado/reference/ado-api/update-method.md) aufgerufen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [OriginalValue und UnderlyingValue – Beispiel (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue und UnderlyingValue – Beispiel (VC++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue-Eigenschaft](../../../ado/reference/ado-api/underlyingvalue-property.md)
