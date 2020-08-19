---
description: SetEOS-Methode
title: '*-Methode | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: fd1d0418fe0c6a0a475594605acc6f28851a777e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442122"
---
# <a name="seteos-method"></a>SetEOS-Methode
Legt die Position fest, die das Ende des Streams ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert der [EOS](../../../ado/reference/ado-api/eos-property.md) -Eigenschaft wird durch die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) am Ende des **Streams aktualisiert.** Alle Bytes oder Zeichen, die der aktuellen Position folgen, werden abgeschnitten.  
  
 Da [Write](../../../ado/reference/ado-api/write-method.md), Write- [Text](../../../ado/reference/ado-api/writetext-method.md)und [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) keine zusätzlichen Werte in vorhandenen **Streamobjekten** kürzen, können Sie diese Bytes oder Zeichen abschneiden, indem Sie die neue Streamende-Position mit **SetEOS**festlegen.  
  
> [!CAUTION]
>  Wenn Sie **EOS** auf eine Position vor dem eigentlichen Ende des Streams festlegen, verlieren Sie alle Daten nach der neuen **EOS** -Position.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
