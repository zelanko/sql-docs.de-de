---
title: Seekenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
author: rothja
ms.author: jroth
ms.openlocfilehash: dca33c975b3d25347b0cb9bb804b852ec5f93d7d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765391"
---
# <a name="seekenum"></a>SeekEnum
Gibt den Typ des auszuführenden [Suchtyps](../../../ado/reference/ado-api/seek-method.md) an.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adseekfirsteq**|1|Sucht den ersten Schlüssel, der mit *KeyValues*übereinstimmt.|  
|**adseeklasteq**|2|Sucht den letzten Schlüssel, der mit *KeyValues*übereinstimmt.|  
|**adseekaftereq**|4|Sucht entweder nach einem Schlüssel, der mit *KeyValues* identisch ist, oder direkt nach dem Speicherort der Übereinstimmung.|  
|**adseekafter**|8|Sucht direkt nach einem Schlüssel, nach dem eine Entsprechung mit *KeyValues* aufgetreten wäre.|  
|**adseekbeforeeq**|16|Sucht entweder nach einem Schlüssel, der mit *KeyValues*identisch ist, oder direkt vor dem, wo die Übereinstimmung aufgetreten wäre.|  
|**adseekbefore**|32|Sucht direkt vor der Suche nach einer Taste, bei der eine Entsprechung mit *KeyValues* aufgetreten wäre.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoerums. Seek. firsteq|  
|Adoerums. Seek. lasteq|  
|Adoerums. Seek. aftereq|  
|Adoerums. Seek. after|  
|Adoerums. Seek. beforeeq|  
|Adoerums. Seek. before|  
  
## <a name="applies-to"></a>Gilt für  
 [Seek-Methode](../../../ado/reference/ado-api/seek-method.md)
