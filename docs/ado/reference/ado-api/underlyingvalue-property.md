---
title: UnderlyingValue-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 582d0b87edd4729ce54cc2a7323b0a63443cab82
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938857"
---
# <a name="underlyingvalue-property"></a>UnderlyingValue-Eigenschaft
Gibt den aktuellen Wert von einem [Feld](../../../ado/reference/ado-api/field-object.md) Objekt in der Datenbank.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Variant** -Wert, der der Wert gibt die **Feld**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **UnderlyingValue** Eigenschaft, um den aktuellen Wert des Felds aus der Datenbank zurückzugeben. Der Wert des Felds in die **UnderlyingValue** -Eigenschaft ist der Wert, der für die Transaktion sichtbar ist und möglicherweise, dass das Ergebnis ein kürzlich veröffentlichtes Update von einer anderen Transaktion. Dies weicht möglicherweise von der [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) -Eigenschaft, die den Wert wiedergibt, die ursprünglich an zurückgegeben wurde die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Dies ist vergleichbar mit der Verwendung der [Resync](../../../ado/reference/ado-api/resync-method.md) -Methode, aber die **UnderlyingValue** Eigenschaft gibt nur den Wert für ein bestimmtes Feld des aktuellen Datensatzes zurück. Dies entspricht dem Wert, der [Resync](../../../ado/reference/ado-api/resync-method.md) Methode verwendet, um das Ersetzen der [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft.  
  
 Bei Verwendung dieser Eigenschaft mit dem **OriginalValue** -Eigenschaft, können Sie Konflikte von BatchUpdates beheben.  
  
## <a name="record"></a>Datensatz  
 Für [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekten, die diese Eigenschaft ist für Felder hinzugefügt, bevor leer, [Update](../../../ado/reference/ado-api/update-method.md) aufgerufen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [OriginalValue und UnderlyingValue – Beispiel (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue und UnderlyingValue – Beispiel (VC++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue-Eigenschaft (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Resync-Methode](../../../ado/reference/ado-api/resync-method.md)
