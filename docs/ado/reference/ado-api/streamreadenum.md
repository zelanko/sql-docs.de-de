---
title: StreamReadEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 37d2ba0834d2a4469d97a36f39677f407a5e61be
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66710672"
---
# <a name="streamreadenum"></a>StreamReadEnum
Gibt an, ob der gesamte Datenstrom oder die nächste Zeile aus gelesen werden sollen eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Standard. Liest alle Bytes aus dem Stream, aus der aktuellen Position oder höher auf dem [EOS](../../../ado/reference/ado-api/eos-property.md) Marker. Dies ist der einzige gültige **StreamReadEnum** Wert mit binären Datenströmen ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **AdTypeBinary**).|  
|**adReadLine**|-2|Liest die nächste Zeile aus dem Stream (gekennzeichnet durch die [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) Eigenschaft).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Read-Methode](../../../ado/reference/ado-api/read-method.md)|[ReadText-Methode](../../../ado/reference/ado-api/readtext-method.md)|
