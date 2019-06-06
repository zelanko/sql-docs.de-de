---
title: CopyTo-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_CopyTo
- _Stream::CopyTo
helpviewer_keywords:
- CopyTo method [ADO]
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cbfdff7c22152acfd0deb97a6e278bd5fd3f553f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698439"
---
# <a name="copyto-method-ado"></a>CopyTo-Methode (ADO)
Kopiert die angegebene Anzahl von Bytes oder Zeichen (je [Typ](../../../ado/reference/ado-api/type-property-ado-stream.md)) in der [Stream](../../../ado/reference/ado-api/stream-object-ado.md) in ein anderes **Stream** Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>Parameter  
 *DestStream*  
 Der Wert einer Objektvariable, die einen Verweis auf ein offenes enthält **Stream** Objekt. Die aktuelle **Stream** ist auf dem Zielserver kopiert **Stream** gemäß *DestStream*. Das Ziel **Stream** bereits geöffnet sein. Falls nicht, tritt ein Laufzeitfehler auf.  
  
> [!NOTE]
>  Die *DestStream* Parameter möglicherweise keinen Proxy **Stream** Objekt, da dies für den Zugriff auf eine private Schnittstelle erfordert die **Stream** -Objekt, das kann nicht remote auf werden die -Client.  
  
 *NumChars*  
 Optional. Ein **Ganzzahl** Wert, der angibt, die Anzahl von Bytes oder Zeichen aus der aktuellen Position in der Quelle kopiert werden **Stream** an das Ziel **Stream**. Der Standardwert ist-1 und gibt an, dass alle Zeichen oder Bytes, aus der aktuellen Position bis kopiert werden [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kopiert die angegebene Anzahl von Zeichen oder Bytes, beginnend mit der aktuellen Position, die gemäß der [Position](../../../ado/reference/ado-api/position-property-ado.md) Eigenschaft. Wenn die angegebene Anzahl größer als die verfügbare Anzahl von Bytes bis **EOS**, und klicken Sie dann nur die Zeichen oder Bytes aus der aktuellen Position bis **EOS** beim Übertragungsvorgang kopiert werden. Wenn der Wert des *"NUMCHARS"* ist-1, oder weggelassen wird, werden alle Zeichen oder Bytes, beginnend mit der aktuellen Position kopiert.  
  
 Wenn vorhandene Zeichen oder Bytes in den Zielstream, werden alle Inhalte über den Zeitpunkt, an dem der Kopiervorgang endet, hinaus bleiben, und werden nicht abgeschnitten. **Position** das Byte, die unmittelbar nach das letzte Byte kopiert wird. Wenn diese Bytes abgeschnitten werden sollen, rufen Sie [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 **CopyTo** sollte verwendet werden, um Daten in ein Ziel kopiert **Stream** des gleichen Typs wie die Quelle **Stream** (ihre **Typ** eigenschafteneinstellungen werden beide **AdTypeText** oder beides **AdTypeBinary**). Für den Text **Stream** Objekte aufweist, können Sie ändern die [Charset](../../../ado/reference/ado-api/charset-property-ado.md) Einstellung der Eigenschaft des Ziels **Stream** aus einem Zeichensatz in eine andere übersetzt. Darüber hinaus Text **Stream** Objekte können in das Binärformat erfolgreich kopiert werden **Stream** Objekte, sind aber binäre **Stream** Objekte können nicht kopiert werden, in Text **Stream**  Objekte.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
