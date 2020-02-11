---
title: Getberechtigungs-Methode (ADOX) | Microsoft-Dokumentation
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
ms.openlocfilehash: 5f5b2a5170b499f5e88d4caac4822d2998691eea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966222"
---
# <a name="getpermissions-method-adox"></a>GetPermissions-Methode (ADOX)
Gibt die Berechtigungen für eine [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) oder einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) für ein Objekt oder einen Objekt Container zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Long** -Wert zurück, der eine Bitmaske mit den Berechtigungen angibt, die die Gruppe oder der Benutzer für das Objekt besitzt. Bei diesem Wert kann es sich um eine oder mehrere der [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) -Konstanten handeln.  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Variant** -Wert, der den Namen des Objekts angibt, für das Berechtigungen festgelegt werden sollen. Legen Sie *Name* auf einen NULL-Wert fest, wenn Sie die Berechtigungen für den Objekt Container erhalten möchten.  
  
 *ObjectType*  
 Ein **Long** -Wert, bei dem es sich um eine der [objecttypeer](../../../ado/reference/adox-api/objecttypeenum.md) -Konstanten handeln kann, die den Typ des Objekts angibt, für das Berechtigungen abzurufen sind.  
  
 *ObjectTypeId*  
 Optional. Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert wird. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [SetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
