---
description: SetPermissions-Methode (ADOX)
title: Setberechtigungs-Methode (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d5af996442e0451a80265b7fbd9fb31450f9475
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439522"
---
# <a name="setpermissions-method-adox"></a>SetPermissions-Methode (ADOX)
Gibt die Berechtigungen für eine [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) oder einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) für ein Objekt an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Zeichen** folgen Wert, der den Namen des Objekts angibt, für das Berechtigungen festgelegt werden sollen.  
  
 *ObjectType*  
 Ein **Long** -Wert, bei dem es sich um eine der [objecttypeer](../../../ado/reference/adox-api/objecttypeenum.md) -Konstanten handeln kann, die den Typ des Objekts angibt, für das Berechtigungen abzurufen sind.  
  
 *Aktion*  
 Ein **Long** -Wert, der eine der [Action](../../../ado/reference/adox-api/actionenum.md) Enumerationskonstanten sein kann, die den Typ der Aktion angibt, die beim Festlegen von Berechtigungen ausgeführt werden soll.  
  
 *Rechte*  
 Ein **Long** -Wert, der eine Bitmaske einer oder mehrerer [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) -Konstanten sein kann, die die festzulegenden Rechte angibt.  
  
 *Ver*  
 Optional. Ein **Long** -Wert, bei dem es sich [um eine der Vererbungs](../../../ado/reference/adox-api/inherittypeenum.md) Konstanten handelt, die angibt, wie Objekte diese Berechtigungen erben. Der Standardwert ist " **adgeerbt None**".  
  
 *ObjectTypeId*  
 Optional. Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Anbieter das Festlegen von Zugriffsrechten für Gruppen oder Benutzer nicht unterstützt, tritt ein Fehler auf.  
  
> [!NOTE]
>  Wenn Sie **setberechtigungen**aufrufen, überschreibt das Festlegen von Aktionen auf **adaccessrevoalle** Einstellungen des *Rights* -Parameters. Legen Sie *Aktionen* nicht auf **adaccessrevofest** , wenn Sie möchten, dass die im *Rights* -Parameter angegebenen Rechte wirksam werden.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)  
    :::column-end:::
    :::column:::
        [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Getberechtigungs-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
