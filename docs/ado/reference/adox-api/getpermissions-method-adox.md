---
title: GetPermissions-Methode (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8bff406485266af99a1c2538a4df237fd5bf43bb
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712089"
---
# <a name="getpermissions-method-adox"></a>GetPermissions-Methode (ADOX)
Gibt zurück, die Berechtigungen für eine [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) oder [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) für ein Objekt oder ein Objektcontainer.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **lange** Wert, der eine Bitmaske, die mit den Berechtigungen, die die Gruppen- oder Benutzernamen für das Objekt angibt. Dieser Wert kann sein, mindestens die [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) Konstanten.  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Variant** -Wert, der den Namen des Objekts, für das zum Festlegen von Berechtigungen angibt. Legen Sie *Namen* auf einen null-Wert, wenn die Berechtigungen für den Container des Objekts abgerufen werden soll.  
  
 *ObjectType*  
 Ein **lange** Wert möglich von der [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) Konstanten, der angibt, den Typ des Objekts, für das Berechtigungen zu erhalten.  
  
 *ObjectTypeId*  
 Optional. Ein **Variant** Wert, der angibt, die GUID für eine Anbieterobjekttyp nicht durch OLE DB-Spezifikation definiert. Dieser Parameter ist erforderlich, wenn *ObjectType* nastaven NA hodnotu **AdPermObjProviderSpecific**ist, andernfalls wird er nicht verwendet.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [GetPermissions und SetPermissions-Methoden – Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
