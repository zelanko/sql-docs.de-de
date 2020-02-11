---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aef8f768dd991e4e6ed740cc56600a6f1a8020e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965951"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Gibt an, wie Objekte Berechtigungen erben, die mit [setberechtigungen](../../../ado/reference/adox-api/setpermissions-method-adox.md)festgelegt sind.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adgeerbt both**|3|Beide Objekte und andere Container, die im primären Objekt enthalten sind, erben den Eintrag.|  
|**adgeerbt-Container**|2|Andere Container, die im primären Objekt enthalten sind, erben den Eintrag.|  
|**adgeerbt None**|0|Default. Es erfolgt keine Vererbung.|  
|**advererbt nopropagate**|4|Die Flags **advereritobjects** und **adgeerbt Containers** werden nicht an einen geerbten Eintrag weitergegeben.|  
|**advereritobjects**|1|Nicht-Container-Objekte im Container erben die Berechtigungen.|  
  
## <a name="applies-to"></a>Gilt für  
 [SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
