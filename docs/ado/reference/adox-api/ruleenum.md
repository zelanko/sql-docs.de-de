---
description: RuleEnum
title: Ruleumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RuleEnum
helpviewer_keywords:
- RuleEnum enumeration [ADOX]
ms.assetid: 738fd3ff-3daf-483d-a0b9-88bef1be54c1
author: rothja
ms.author: jroth
ms.openlocfilehash: da49bbacf8ba59ba12f59fb072e9b5ec8c2ec2ea
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769459"
---
# <a name="ruleenum"></a>RuleEnum
Gibt die Regel an, die befolgt werden soll, wenn eine [Taste](./key-object-adox.md) gelöscht wird.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adricascade**|1|Kaskadierte Änderungen.|  
|**adrinone**|0|Standard. Es wird keine Aktion ausgeführt.|  
|**adrisetdefault**|3|Der Fremdschlüssel Wert wird auf den Standardwert festgelegt.|  
|**adrisetnull**|2|Der Fremdschlüssel Wert ist auf NULL festgelegt.|  
  
## <a name="applies-to"></a>Gilt für  
 [DeleteRule-Eigenschaft (ADOX)](./deleterule-property-adox.md)