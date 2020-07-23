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
ms.openlocfilehash: fe7d97909a2d38e548a072245b08110b1d61eb3c
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86943162"
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

:::row:::
    :::column:::
        [GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)  
        [GetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)  
    :::column-end:::
    :::column:::
        [SetObjectOwner-Methode](../../../ado/reference/adox-api/setobjectowner-method.md)  
        [SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)  
    :::column-end:::
:::row-end:::
