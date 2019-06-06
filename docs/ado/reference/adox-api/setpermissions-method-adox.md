---
title: SetPermissions-Methode (ADOX) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fcc44037ac746621c044bca755fd9b957356dc38
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705792"
---
# <a name="setpermissions-method-adox"></a>SetPermissions-Methode (ADOX)
Gibt an, die Berechtigungen für eine [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) oder [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) für ein Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Zeichenfolge** -Wert, der den Namen des Objekts, für das zum Festlegen von Berechtigungen angibt.  
  
 *ObjectType*  
 Ein **lange** Wert möglich von der [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) Konstanten, der angibt, den Typ des Objekts, für das Berechtigungen zu erhalten.  
  
 *Aktion*  
 Ein **lange** Wert möglich von der [ActionEnum](../../../ado/reference/adox-api/actionenum.md) Konstanten, die den Typ der Aktion, die ausgeführt wird, beim Festlegen von Berechtigungen angibt.  
  
 *Rechte*  
 Ein **lange** Wert, der eine Bitmaske sein kann von einem oder mehreren der der [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) Konstanten, die die festzulegenden Rechte angibt.  
  
 *Erben*  
 Optional. Ein **lange** Wert möglich von der [InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md) Konstanten, der angibt, wie Objekte erben diese Berechtigungen. Der Standardwert ist **AdInheritNone**.  
  
 *ObjectTypeId*  
 Optional. Ein **Variant** Wert, der die GUID für einen Anbieter-Objekttyp angibt, die nicht vom OLE DB-Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* nastaven NA hodnotu **AdPermObjProviderSpecific**ist, andernfalls wird er nicht verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Anbieter das Festlegen von Zugriffsrechten für Gruppen oder Benutzer nicht unterstützt wird, tritt ein Fehler auf.  
  
> [!NOTE]
>  Beim Aufrufen von **SetPermissions**, Festlegen von Aktionen auf **AdAccessRevoke** überschreibt alle Einstellungen von der *Rechte* Parameter. Legen Sie nicht *Aktionen* zu **AdAccessRevoke** sollten Sie die Rechte, die im angegebenen die *Rechte* Parameter wirksam wird.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [GetPermissions und SetPermissions-Methoden – Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [GetPermissions-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
