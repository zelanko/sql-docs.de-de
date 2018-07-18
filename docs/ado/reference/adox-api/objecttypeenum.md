---
title: ObjectTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9cb6239cee3bd6416e587dc77d55e287da68e4
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286759"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Gibt den Typ des Datenbankobjekts für das Berechtigungen oder Besitzer festgelegt.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|Das Objekt ist eine Spalte an.|  
|**adPermObjDatabase**|3|Das Objekt ist eine Datenbank.|  
|**adPermObjProcedure**|4|Das Objekt ist eine Prozedur.|  
|**adPermObjProviderSpecific**|-1|Das Objekt ist ein Typ, der vom Anbieter definiert. Es wird eine Fehlermeldung angezeigt, wenn die *ObjectType* Parameter ist **AdPermObjProviderSpecific** und ein *ObjectTypeId* nicht angegeben wird.|  
|**adPermObjTable**|1|Das Objekt ist eine Tabelle.|  
|**adPermObjView**|5|Das Objekt ist eine Sicht.|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[GetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[SetObjectOwner-Methode](../../../ado/reference/adox-api/setobjectowner-method.md)|[SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
