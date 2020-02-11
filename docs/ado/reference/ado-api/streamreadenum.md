---
title: Streameinumum | Microsoft-Dokumentation
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
ms.openlocfilehash: 7700fc1ddc3cc619db224ac46006370898af1d62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928661"
---
# <a name="streamreadenum"></a>StreamReadEnum
Gibt an, ob der gesamte Stream oder die nächste Zeile aus einem [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) gelesen werden soll.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**ADRead all**|-1|Default. Liest alle Bytes aus dem Stream von der aktuellen Position bis zum [EOS](../../../ado/reference/ado-api/eos-property.md) Marker. Dies ist der einzige gültige **streamRead** -Enumerationswert mit binären Datenströmen ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) : **adTypeBinary**).|  
|**"ADRead Line"**|-2|Liest die nächste Zeile aus dem Stream (festgelegt durch die [lineseparser](../../../ado/reference/ado-api/lineseparator-property-ado.md) -Eigenschaft).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Read-Methode](../../../ado/reference/ado-api/read-method.md)|[ReadText-Methode](../../../ado/reference/ado-api/readtext-method.md)|
