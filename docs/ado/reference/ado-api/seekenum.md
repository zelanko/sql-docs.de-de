---
description: SeekEnum
title: Seekenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 345e6dff5c2bc372f06eb386a4546a61b9e5a1bb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989151"
---
# <a name="seekenum"></a>SeekEnum
Gibt den Typ des auszuführenden [Suchtyps](./seek-method.md) an.  
  
|Konstante|Wert|Beschreibung|  
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
 [Seek-Methode](./seek-method.md)