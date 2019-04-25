---
title: Write-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 52561b6d240a58e59490d607c8729b5d878b96a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642427"
---
# <a name="write-method"></a>Write-Methode
Schreibt binäre Daten in einem [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Parameter  
 *Buffer*  
 Ein **Variant** , die ein Array von zu schreibenden Bytes enthält.  
  
## <a name="remarks"></a>Hinweise  
 In die angegebenen Bytes geschrieben werden die **Stream** -Objekts ohne Leerzeichen zwischen den einzelnen Bytes.  
  
 Die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) festgelegt ist, auf das Byte, die geschriebenen Daten folgt. Die **schreiben** -Methode werden die restlichen Daten in einem Datenstrom nicht abgeschnitten. Wenn diese Bytes abgeschnitten werden sollen, rufen Sie [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Wenn Sie nach der aktuellen [EOS](../../../ado/reference/ado-api/eos-property.md) Position der [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) von der **Stream** wird vergrößert werden, um neue Bytes, und **EOS** wird verschoben um die neue letzte Byte in den **Stream**.  
  
> [!NOTE]
>  Die **schreiben** Methode wird verwendet, mit binären Datenströmen ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **AdTypeBinary**). Für Textstreams (**Typ** ist **AdTypeText**), verwenden Sie [WriteText](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [WriteText-Methode](../../../ado/reference/ado-api/writetext-method.md)
