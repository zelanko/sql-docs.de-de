---
title: Write Text-Methode | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67947499"
---
# <a name="writetext-method"></a>WriteText-Methode
Schreibt eine angegebene Text Zeichenfolge in ein Daten [Strom](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Daten*  
 Ein **Zeichen** folgen Wert, der den Text in zu schreibenden Zeichen enthält.  
  
 *Optionen*  
 (Optional) Ein [streamschreibwert](../../../ado/reference/ado-api/streamwriteenum.md) , der angibt, ob ein Zeilen Trennzeichen am Ende der angegebenen Zeichenfolge geschrieben werden muss.  
  
## <a name="remarks"></a>Bemerkungen  
 Angegebene Zeichen folgen werden in das **Stream** -Objekt geschrieben, ohne dass dazwischen liegende Leerzeichen oder Zeichen zwischen den einzelnen Zeichen folgen liegen  
  
 Die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) wird auf das Zeichen festgelegt, das den geschriebenen Daten folgt. Die Methode " **Write Text** " schneidet den Rest der Daten in einem Stream nicht ab. Wenn Sie diese Zeichen abschneiden möchten [, nennen Sie](../../../ado/reference/ado-api/seteos-method.md)"*".  
  
 Wenn Sie über die aktuelle [EOS](../../../ado/reference/ado-api/eos-property.md) -Position hinaus schreiben, wird die [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) des **Streams** um alle neuen Zeichen erweitert, und **EOS** wechselt zum neuen letzten Byte im **Stream**.  
  
> [!NOTE]
>  Die Methode " **Write Text** " wird mit Textstreams verwendet ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) : **adtypetext**). Verwenden Sie für binäre Datenströme (**Typ** : **adTypeBinary**) " [Write](../../../ado/reference/ado-api/write-method.md)".  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Write-Methode](../../../ado/reference/ado-api/write-method.md)
