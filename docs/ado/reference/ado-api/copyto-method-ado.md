---
description: CopyTo-Methode (ADO)
title: CopyTo-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bbb394810ebbfe8d8c0e1d598641a1e77e7d204
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974551"
---
# <a name="copyto-method-ado"></a>CopyTo-Methode (ADO)
Kopiert die angegebene Anzahl von Zeichen oder bytes (abhängig vom [Typ](./type-property-ado-stream.md)) im [Stream](./stream-object-ado.md) in ein anderes **Streamobjekt** .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>Parameter  
 *DestStream*  
 Ein Objektvariablen Wert, der einen Verweis auf ein geöffnetes **Streamobjekt** enthält. Der aktuelle **Stream** wird in den **Zielstream** kopiert, der von *DestStream*angegeben wird. Der **Zielstream** muss bereits geöffnet sein. Wenn dies nicht der Fall ist, tritt ein Laufzeitfehler auf.  
  
> [!NOTE]
>  Der *DestStream* -Parameter ist möglicherweise kein Proxy des Daten **Strom** Objekts, da hierfür der Zugriff auf eine private Schnittstelle für das Daten **Strom** Objekt erforderlich ist, das nicht Remote an den Client übergeben werden kann.  
  
 *NumChars*  
 Optional. Ein **ganzzahliger** Wert, der die Anzahl der Bytes oder Zeichen angibt, die von der aktuellen Position im Quelldaten **Strom** in den **Zielstream**kopiert werden sollen. Der Standardwert ist-1 und gibt an, dass alle Zeichen oder Bytes von der aktuellen Position in [EOS](./eos-property.md)kopiert werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode kopiert die angegebene Anzahl von Zeichen oder bytes, beginnend bei der aktuellen Position, die durch die [Positions](./position-property-ado.md) Eigenschaft angegeben wird. Wenn die angegebene Anzahl größer als die verfügbare Anzahl von Bytes bis **EOS**ist, werden nur die Zeichen oder Bytes von der aktuellen Position zu **EOS** kopiert. Wenn der Wert von " *NumChars* "-1 ist oder weggelassen wird, werden alle Zeichen oder bytes, die von der aktuellen Position beginnen, kopiert.  
  
 Wenn sich im Zielstream vorhandene Zeichen oder Bytes befinden, bleiben alle Inhalte außerhalb des Punkts, an dem der Kopiervorgang endet, und werden nicht abgeschnitten. **Position** wird das Byte, das unmittelbar auf das letzte kopierte Byte folgt. Wenn Sie diese Bytes abschneiden möchten [, wenden Sie](./seteos-method.md)sich an.  
  
 **CopyTo** sollte verwendet werden, um Daten in einen **Zielstream** desselben Typs wie den Quelldaten **Strom** zu kopieren (Ihre **typeigenschafts** Einstellungen lauten sowohl **adtypetext** als auch **adTypeBinary**). Bei **textstreamobjekten** können Sie die [CharSet](./charset-property-ado.md) -Eigenschafts Einstellung des **zielstreams** so ändern, dass Sie von einem Zeichensatz in einen anderen übersetzt wird. Außerdem können **textstreamobjekte** erfolgreich in binäre **Streamobjekte** kopiert werden, aber binäre **Streamobjekte** können nicht in **textstreamobjekte** kopiert werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)