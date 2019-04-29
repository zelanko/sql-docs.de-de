---
title: InheritTypeEnum | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 249616f2f08b8b8f6138ce13621d26c5f7af9e1e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213346"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Gibt an, wie Objekte mit festgelegten Berechtigungen erben [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Sowohl Objekte als auch andere Container, der das primäre Objekt enthalten sind, erben den Eintrag.|  
|**adInheritContainers**|2|Andere Container, die das primäre Objekt enthalten sind, erben den Eintrag.|  
|**adInheritNone**|0|Standard. Es tritt keine Vererbung auf.|  
|**adInheritNoPropagate**|4|Die **AdInheritObjects** und **AdInheritContainers** Flags werden nicht an einen geerbten Eintrag weitergegeben.|  
|**adInheritObjects**|1|Nicht-Container-Objekte im Container erben die Berechtigungen.|  
  
## <a name="applies-to"></a>Gilt für  
 [SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
