---
title: SeekEnum | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6e044c4a2cda01fcc9cbba2667beaae75a12caf
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63459334"
---
# <a name="seekenum"></a>SeekEnum
Gibt den Typ der [Seek](../../../ado/reference/ado-api/seek-method.md) ausgeführt.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Sucht den ersten Schlüssel gleich *KeyValues*.|  
|**adSeekLastEQ**|2|Sucht den letzte Schlüssel gleich *KeyValues*.|  
|**adSeekAfterEQ**|4|Sucht entweder einen Schlüssel gleich *KeyValues* oder nach dem entsprechen, in denen aufgetreten wäre.|  
|**adSeekAfter**|8|Sucht einen Schlüssel nach dem Where eine Übereinstimmung mit *KeyValues* würde aufgetreten sind.|  
|**adSeekBeforeEQ**|16|Sucht entweder einen Schlüssel gleich *KeyValues*Markierung oder kurz vor, in denen diese Übereinstimmung aufgetreten wäre.|  
|**adSeekBefore**|32|Kurz vor dem Ausführen sucht einen Schlüssel, wenn eine Übereinstimmung mit *KeyValues* würde aufgetreten sind.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>Gilt für  
 [Seek-Methode](../../../ado/reference/ado-api/seek-method.md)
