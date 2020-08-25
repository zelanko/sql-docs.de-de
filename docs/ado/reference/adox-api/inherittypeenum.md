---
description: InheritTypeEnum
title: Ererttypep | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: rothja
ms.author: jroth
ms.openlocfilehash: d1fed614d90bbf53fdb2198e3ddd657a1e44acd1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770119"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Gibt an, wie Objekte Berechtigungen erben, die mit [setberechtigungen](./setpermissions-method-adox.md)festgelegt sind.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adgeerbt both**|3|Beide Objekte und andere Container, die im primären Objekt enthalten sind, erben den Eintrag.|  
|**adgeerbt-Container**|2|Andere Container, die im primären Objekt enthalten sind, erben den Eintrag.|  
|**adgeerbt None**|0|Standard. Es erfolgt keine Vererbung.|  
|**advererbt nopropagate**|4|Die Flags **advereritobjects** und **adgeerbt Containers** werden nicht an einen geerbten Eintrag weitergegeben.|  
|**advereritobjects**|1|Nicht-Container-Objekte im Container erben die Berechtigungen.|  
  
## <a name="applies-to"></a>Gilt für  
 [SetPermissions-Methode (ADOX)](./setpermissions-method-adox.md)