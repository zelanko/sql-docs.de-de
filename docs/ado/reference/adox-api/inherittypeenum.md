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
ms.openlocfilehash: aef8f768dd991e4e6ed740cc56600a6f1a8020e0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965951"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Gibt an, wie Objekte mit festgelegten Berechtigungen erben [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Sowohl Objekte als auch andere Container, der das primäre Objekt enthalten sind, erben den Eintrag.|  
|**adInheritContainers**|2|Andere Container, die das primäre Objekt enthalten sind, erben den Eintrag.|  
|**adInheritNone**|0|Standard. Es tritt keine Vererbung auf.|  
|**adInheritNoPropagate**|4|Die **AdInheritObjects** und **AdInheritContainers** Flags werden nicht an einen geerbten Eintrag weitergegeben.|  
|**adInheritObjects**|1|Nicht-Container-Objekte im Container erben die Berechtigungen.|  
  
## <a name="applies-to"></a>Gilt für  
 [SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
