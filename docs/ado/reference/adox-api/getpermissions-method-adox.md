---
description: GetPermissions-Methode (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d9533ca5260a8e5dc900a28d883f66994d7a9669
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770459"
---
# <a name="getpermissions-method-adox"></a>GetPermissions-Methode (ADOX)
Gibt die Berechtigungen für eine [Gruppe](./group-object-adox.md) oder einen [Benutzer](./user-object-adox.md) für ein Objekt oder einen Objekt Container zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Long** -Wert zurück, der eine Bitmaske mit den Berechtigungen angibt, die die Gruppe oder der Benutzer für das Objekt besitzt. Bei diesem Wert kann es sich um eine oder mehrere der [RightsEnum](./rightsenum.md) -Konstanten handeln.  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Variant** -Wert, der den Namen des Objekts angibt, für das Berechtigungen festgelegt werden sollen. Legen Sie *Name* auf einen NULL-Wert fest, wenn Sie die Berechtigungen für den Objekt Container erhalten möchten.  
  
 *ObjectType*  
 Ein **Long** -Wert, bei dem es sich um eine der [objecttypeer](./objecttypeenum.md) -Konstanten handeln kann, die den Typ des Objekts angibt, für das Berechtigungen abzurufen sind.  
  
 *ObjectTypeId*  
 Optional. Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert wird. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Group-Objekt (ADOX)](./group-object-adox.md)  
    :::column-end:::
    :::column:::
        [User-Objekt (ADOX)](./user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [Name-Eigenschaft (ADOX)](./name-property-adox.md)   
 [SetPermissions-Methode (ADOX)](./setpermissions-method-adox.md)