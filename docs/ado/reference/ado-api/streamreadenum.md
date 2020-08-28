---
description: StreamReadEnum
title: Streameinumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: d9f685a80d822950a159ddb3fbc9f148489a723e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988471"
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