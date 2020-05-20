---
title: Objecttypeer-ID | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d493218f31965c04b5a64321c4a1bf87a2518f6f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763791"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Gibt den Typ des Datenbankobjekts an, für das Berechtigungen oder den Besitz festgelegt werden sollen.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|Das-Objekt ist eine-Spalte.|  
|**adPermObjDatabase**|3|Das-Objekt ist eine-Datenbank.|  
|**adPermObjProcedure**|4|Das-Objekt ist eine-Prozedur.|  
|**adPermObjProviderSpecific**|-1|Das-Objekt ist ein vom Anbieter definiertes Typ. Wenn der *ObjectType* -Parameter **adpermubjproviderspecific** ist und keine *ObjectTypeId* angegeben wurde, tritt ein Fehler auf.|  
|**adPermObjTable**|1|Das-Objekt ist eine Tabelle.|  
|**adPermObjView**|5|Das-Objekt ist eine Sicht.|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[GetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[SetObjectOwner-Methode](../../../ado/reference/adox-api/setobjectowner-method.md)|[SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
