---
title: SetEOS-Methode | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0db8c7972d6b647cdd021d43dbb3cdee1ba0452
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678528"
---
# <a name="seteos-method"></a>SetEOS-Methode
Legt fest, der die Position das Ende des Streams.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Hinweise  
 **SetEOS** aktualisiert den Wert der [EOS](../../../ado/reference/ado-api/eos-property.md) Eigenschaft, indem Sie die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) das Ende des Streams. Alle Bytes oder Zeichen, die nach der aktuellen Position werden abgeschnitten.  
  
 Da [schreiben](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), und [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) werden nicht abgeschnitten werden, alle zusätzlichen Werte in vorhandenen **Stream** Objekte aufweist, können Sie diese kürzen Bytes oder Zeichen durch die neue Position der End-of-Stream mit festlegen **SetEOS**.  
  
> [!CAUTION]
>  Setzen Sie **EOS** an eine Position vor dem tatsächlichen Ende des Streams, verlieren Sie alle Daten nach neuen **EOS** Position.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
