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
ms.openlocfilehash: 84e10e8edb6cca3c4e56ac1dd0106b3c641af872
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67945907"
---
# <a name="write-method"></a>Write-Methode
Schreibt Binärdaten in ein Daten [Strom](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Parameter  
 *Ert*  
 Ein **Variant** -Wert, der ein Array von zu schreibenden Bytes enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Die angegebenen Bytes werden in das **Stream** -Objekt geschrieben, ohne dass zwischen den einzelnen Bytes dazwischen liegende Leerzeichen stehen.  
  
 Die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) wird auf das Byte festgelegt, das den geschriebenen Daten folgt. Die **Write** -Methode schneidet den Rest der Daten in einem Stream nicht ab. Wenn Sie diese Bytes abschneiden möchten [, wenden Sie](../../../ado/reference/ado-api/seteos-method.md)sich an.  
  
 Wenn Sie über die aktuelle [EOS](../../../ado/reference/ado-api/eos-property.md) -Position hinaus schreiben, wird die [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) des **Streams** um alle neuen Bytes angehoben, und **EOS** wechselt zum neuen letzten Byte im **Stream**.  
  
> [!NOTE]
>  Die **Write** -Methode wird mit binären Datenströmen verwendet ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) : **adTypeBinary**). Verwenden Sie für Textstreams (**Typ** : **adtypetext**) " [Write Text](../../../ado/reference/ado-api/writetext-method.md)".  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [WriteText-Methode](../../../ado/reference/ado-api/writetext-method.md)
