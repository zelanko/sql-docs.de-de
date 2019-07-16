---
title: WriteText-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64b7d8fd3f2220562e3695d6e31c83261daa2e60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67947499"
---
# <a name="writetext-method"></a>WriteText-Methode
Schreibt eine Zeichenfolge angegebenen Text in einem [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Daten*  
 Ein **Zeichenfolge** Wert, der den Text im zu schreibender Zeichen enthält.  
  
 *Options*  
 Optional. Ein [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) Wert, der angibt, ob ein Zeilentrennzeichen am Ende der angegebenen Zeichenfolge geschrieben werden muss.  
  
## <a name="remarks"></a>Hinweise  
 Angegebene Zeichenfolgen werden geschrieben, um die **Stream** Objekt ohne dazwischenliegende Leerzeichen oder Zeichen zwischen den einzelnen Zeichenfolgen.  
  
 Die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) festgelegt ist, auf das Zeichen nach die geschriebenen Daten. Die **WriteText** -Methode werden die restlichen Daten in einem Datenstrom nicht abgeschnitten. Wenn diese Zeichen abgeschnitten werden sollen, rufen Sie [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Wenn Sie nach der aktuellen [EOS](../../../ado/reference/ado-api/eos-property.md) Position der [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) von der **Stream** wird vergrößert werden, um alle neuen Zeichen enthalten und **EOS** Wechselt in die neue letzte Byte in den **Stream**.  
  
> [!NOTE]
>  Die **WriteText** Methode wird verwendet, mit dem Text-Streams ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **AdTypeText**). Für binäre Datenströme (**Typ** ist **AdTypeBinary**), verwenden Sie [schreiben](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Write-Methode](../../../ado/reference/ado-api/write-method.md)
