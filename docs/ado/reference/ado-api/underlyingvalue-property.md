---
description: UnderlyingValue-Eigenschaft
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 869daa9afc840e7580e6498510ef07d4be002802
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777079"
---
# <a name="underlyingvalue-property"></a>UnderlyingValue-Eigenschaft
Gibt den aktuellen Wert eines [Feld](./field-object.md) Objekts in der Datenbank an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Variant** -Wert zurück, der den Wert des **Felds**angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **UnderlyingValue** -Eigenschaft, um den aktuellen Feldwert aus der Datenbank zurückzugeben. Der Feldwert in der **UnderlyingValue** -Eigenschaft ist der Wert, der für die Transaktion sichtbar ist und möglicherweise das Ergebnis einer aktuellen Aktualisierung durch eine andere Transaktion ist. Dies kann sich von der [OriginalValue](./originalvalue-property-ado.md) -Eigenschaft unterscheiden, die den Wert angibt, der ursprünglich an das [Recordset](./recordset-object-ado.md)zurückgegeben wurde.  
  
 Dies ähnelt der Verwendung der [Resync](./resync-method.md) -Methode, aber die **UnderlyingValue** -Eigenschaft gibt nur den Wert für ein bestimmtes Feld aus dem aktuellen Datensatz zurück. Dies ist derselbe Wert, den die [Resync](./resync-method.md) -Methode verwendet, um die [value](./value-property-ado.md) -Eigenschaft zu ersetzen.  
  
 Wenn Sie diese Eigenschaft mit der **OriginalValue** -Eigenschaft verwenden, können Sie Konflikte lösen, die sich aus Batch Updates ergeben.  
  
## <a name="record"></a>Datensatz  
 Bei [Datensatz](./record-object-ado.md) -Objekten ist diese Eigenschaft für Felder, die vor dem Aufruf von [Update](./update-method.md) hinzugefügt werden, leer.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](./field-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OriginalValue-und UnderlyingValue-Eigenschaften (Beispiel) (VB)](./originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue-und UnderlyingValue-Eigenschaften Beispiel (VC + +)](./originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue-Eigenschaft (ADO)](./originalvalue-property-ado.md)   
 [Resync-Methode](./resync-method.md)