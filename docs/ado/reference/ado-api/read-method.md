---
title: Read-Methode | Microsoft-Dokumentation
ms.prod: sql
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 75b39b758d48a173bcfbe84e3fecbd20cce5ee12
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754270"
---
# <a name="read-method"></a>Read-Methode
Liest eine angegebene Anzahl von Bytes aus einem binären [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Parameter  
 *NumBytes*  
 Dies ist optional. Ein **Long** -Wert, der die Anzahl der Bytes angibt, die aus der Datei gelesen werden sollen, oder der streamleenumererwert **adleall**, der Standardwert ist. [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)  
  
## <a name="return-value"></a>Rückgabewert  
 Die **Read** -Methode liest eine angegebene Anzahl von Bytes oder den gesamten Stream aus einem **Streamobjekt** und gibt die resultierenden Daten als **Variante**zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn *numBytes* größer als die Anzahl der Bytes ist, die im **Stream**verbleiben, werden nur die verbleibenden Bytes zurückgegeben. Die gelesenen Daten werden nicht so aufgefüllt, dass Sie mit der von *numBytes*angegebenen Länge identisch sind. Wenn keine zu lesenden Bytes übrig sind, wird eine Variante mit einem NULL-Wert zurückgegeben. **Read** kann nicht zum Rück Lesen verwendet werden.  
  
> [!NOTE]
>  *NumBytes* misst immer bytes. Verwenden Sie für **textstreamobjekte** ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) : **adtypetext**) die Datei "read [Text](../../../ado/reference/ado-api/readtext-method.md)".  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ReadText-Methode](../../../ado/reference/ado-api/readtext-method.md)
