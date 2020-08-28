---
description: SetEOS-Methode
title: '*-Methode | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ebf47bdae6a879a3afe699be36081eb136b700e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989131"
---
# <a name="seteos-method"></a>SetEOS-Methode
Legt die Position fest, die das Ende des Streams ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert der [EOS](./eos-property.md) -Eigenschaft wird durch die aktuelle [Position](./position-property-ado.md) am Ende des **Streams aktualisiert.** Alle Bytes oder Zeichen, die der aktuellen Position folgen, werden abgeschnitten.  
  
 Da [Write](./write-method.md), Write- [Text](./writetext-method.md)und [CopyTo](./copyto-method-ado.md) keine zusätzlichen Werte in vorhandenen **Streamobjekten** kürzen, können Sie diese Bytes oder Zeichen abschneiden, indem Sie die neue Streamende-Position mit **SetEOS**festlegen.  
  
> [!CAUTION]
>  Wenn Sie **EOS** auf eine Position vor dem eigentlichen Ende des Streams festlegen, verlieren Sie alle Daten nach der neuen **EOS** -Position.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)