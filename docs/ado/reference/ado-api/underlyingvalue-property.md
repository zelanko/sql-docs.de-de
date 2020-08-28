---
description: UnderlyingValue-Eigenschaft
title: UnderlyingValue-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: a96924a682a0c916da8c6834ea7b290b88b6f690
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988171"
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