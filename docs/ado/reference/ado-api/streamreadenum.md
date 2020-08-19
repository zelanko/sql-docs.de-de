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
ms.openlocfilehash: 1aa8ff80f02d84aaa69904d914e0e40da44da930
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441812"
---
# <a name="streamreadenum"></a>StreamReadEnum
Gibt an, ob der gesamte Stream oder die nächste Zeile aus einem [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) gelesen werden soll.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**ADRead all**|-1|Standard. Liest alle Bytes aus dem Stream von der aktuellen Position bis zum [EOS](../../../ado/reference/ado-api/eos-property.md) Marker. Dies ist der einzige gültige **streamRead** -Enumerationswert mit binären Datenströmen ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) : **adTypeBinary**).|  
|**"ADRead Line"**|-2|Liest die nächste Zeile aus dem Stream (festgelegt durch die [lineseparser](../../../ado/reference/ado-api/lineseparator-property-ado.md) -Eigenschaft).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Read-Methode](../../../ado/reference/ado-api/read-method.md)  
    :::column-end:::
    :::column:::
        [ReadText-Methode](../../../ado/reference/ado-api/readtext-method.md)  
    :::column-end:::
:::row-end:::
