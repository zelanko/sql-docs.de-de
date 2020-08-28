---
description: Write-Methode
title: Write-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 90f67c0804424e15d51cc8538413f3c4464ff775
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987751"
---
# <a name="write-method"></a>Write-Methode
Schreibt Binärdaten in ein Daten [Strom](./stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Parameter  
 *Buffer*  
 Ein **Variant** -Wert, der ein Array von zu schreibenden Bytes enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Die angegebenen Bytes werden in das **Stream** -Objekt geschrieben, ohne dass zwischen den einzelnen Bytes dazwischen liegende Leerzeichen stehen.  
  
 Die aktuelle [Position](./position-property-ado.md) wird auf das Byte festgelegt, das den geschriebenen Daten folgt. Die **Write** -Methode schneidet den Rest der Daten in einem Stream nicht ab. Wenn Sie diese Bytes abschneiden möchten [, wenden Sie](./seteos-method.md)sich an.  
  
 Wenn Sie über die aktuelle [EOS](./eos-property.md) -Position hinaus schreiben, wird die [Größe](./size-property-ado-stream.md) des **Streams** um alle neuen Bytes angehoben, und **EOS** wechselt zum neuen letzten Byte im **Stream**.  
  
> [!NOTE]
>  Die **Write** -Methode wird mit binären Datenströmen verwendet ([Typ](./type-property-ado-stream.md) : **adTypeBinary**). Verwenden Sie für Textstreams (**Typ** : **adtypetext**) " [Write Text](./writetext-method.md)".  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [WriteText-Methode](./writetext-method.md)