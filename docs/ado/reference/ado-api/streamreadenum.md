---
description: StreamReadEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c0a0e8d93742574e9a2975b99d15c18500684e60
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777179"
---
# <a name="streamreadenum"></a>StreamReadEnum
Gibt an, ob der gesamte Stream oder die nächste Zeile aus einem [Streamobjekt](./stream-object-ado.md) gelesen werden soll.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**ADRead all**|-1|Standard. Liest alle Bytes aus dem Stream von der aktuellen Position bis zum [EOS](./eos-property.md) Marker. Dies ist der einzige gültige **streamRead** -Enumerationswert mit binären Datenströmen ([Typ](./type-property-ado-stream.md) : **adTypeBinary**).|  
|**"ADRead Line"**|-2|Liest die nächste Zeile aus dem Stream (festgelegt durch die [lineseparser](./lineseparator-property-ado.md) -Eigenschaft).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Read-Methode](./read-method.md)  
    :::column-end:::
    :::column:::
        [ReadText-Methode](./readtext-method.md)  
    :::column-end:::
:::row-end:::