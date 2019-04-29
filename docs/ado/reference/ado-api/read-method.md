---
title: Read-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b5bbc04c94d491c096db047d574cc3b5fd8ee38
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156631"
---
# <a name="read-method"></a>Read-Methode
Liest eine angegebene Anzahl von Bytes aus einer Binärdatei [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Parameter  
 *NumBytes*  
 Dies ist optional. Ein **lange** Wert, der angibt, die Anzahl der Bytes, die aus der Datei gelesen oder [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) Wert **AdReadAll**, dies ist die Standardeinstellung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die **lesen** Methode liest eine angegebene Anzahl von Bytes oder der gesamte Stream, aus einem **Stream** Objekt und gibt die resultierenden Daten als eine **Variant**.  
  
## <a name="remarks"></a>Hinweise  
 Wenn *NumBytes* bleibt mehr als die Anzahl der Bytes in den **Stream**, nur die verbliebenen Bytes werden zurückgegeben. Die gelesenen Daten ist nicht entsprechend die vom angegebenen Länge aufgefüllt *NumBytes*. Wenn es keine sind um zu lesenden Bytes, wird eine Variante mit dem Wert null zurückgegeben. **Lesen** kann nicht verwendet werden, um rückwärts zu lesen.  
  
> [!NOTE]
>  *NumBytes* immer misst Bytes. Für den Text **Stream** Objekte ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **AdTypeText**), verwenden Sie [ReadText](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ReadText-Methode](../../../ado/reference/ado-api/readtext-method.md)
