---
title: ObjectTypeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4239cd2e62db43b4316bad5edbf989f29709213a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66706235"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Gibt den Typ des Datenbankobjekts für das Berechtigungen oder Besitzer festgelegt.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|Das Objekt ist eine Spalte an.|  
|**adPermObjDatabase**|3|Das Objekt ist eine Datenbank.|  
|**adPermObjProcedure**|4|Das Objekt ist eine Prozedur an.|  
|**adPermObjProviderSpecific**|-1|Das Objekt ist ein Typ, der vom Anbieter definiert. Es wird ein Fehler auftreten, wenn die *ObjectType* -Parameter ist **AdPermObjProviderSpecific** und *ObjectTypeId* nicht angegeben wird.|  
|**adPermObjTable**|1|Das Objekt ist eine Tabelle.|  
|**adPermObjView**|5|Das Objekt ist eine Ansicht.|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[GetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[SetObjectOwner-Methode](../../../ado/reference/adox-api/setobjectowner-method.md)|[SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
