---
description: Read-Methode
title: Read-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.technology: ado
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
ms.openlocfilehash: 6d4b0ab7c3cc77c1f83eac4c3a30e9f637d950ba
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989901"
---
# <a name="read-method"></a>Read-Methode
Liest eine angegebene Anzahl von Bytes aus einem binären [Streamobjekt](./stream-object-ado.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Parameter  
 *NumBytes*  
 Optional. Ein **Long** -Wert, der die Anzahl der Bytes angibt, die aus der Datei gelesen werden sollen, oder der streamleenumererwert **adleall**, der Standardwert ist. [StreamReadEnum](./streamreadenum.md)  
  
## <a name="return-value"></a>Rückgabewert  
 Die **Read** -Methode liest eine angegebene Anzahl von Bytes oder den gesamten Stream aus einem **Streamobjekt** und gibt die resultierenden Daten als **Variante**zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn *numBytes* größer als die Anzahl der Bytes ist, die im **Stream**verbleiben, werden nur die verbleibenden Bytes zurückgegeben. Die gelesenen Daten werden nicht so aufgefüllt, dass Sie mit der von *numBytes*angegebenen Länge identisch sind. Wenn keine zu lesenden Bytes übrig sind, wird eine Variante mit einem NULL-Wert zurückgegeben. **Read** kann nicht zum Rück Lesen verwendet werden.  
  
> [!NOTE]
>  *NumBytes* misst immer bytes. Verwenden Sie für **textstreamobjekte** ([Typ](./type-property-ado-stream.md) : **adtypetext**) die Datei "read [Text](./readtext-method.md)".  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ReadText-Methode](./readtext-method.md)