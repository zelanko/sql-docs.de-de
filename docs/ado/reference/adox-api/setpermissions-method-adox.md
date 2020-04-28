---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50a609d0cebe70ea5127ed448e57a70881e35097
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965229"
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
 (Optional) Ein **Long** -Wert, bei dem es sich [um eine der Vererbungs](../../../ado/reference/adox-api/inherittypeenum.md) Konstanten handelt, die angibt, wie Objekte diese Berechtigungen erben. Der Standardwert ist " **adgeerbt None**".  
  
 *ObjectTypeId*  
 (Optional) Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Anbieter das Festlegen von Zugriffsrechten für Gruppen oder Benutzer nicht unterstützt, tritt ein Fehler auf.  
  
> [!NOTE]
>  Wenn Sie **setberechtigungen**aufrufen, überschreibt das Festlegen von Aktionen auf **adaccessrevoalle** Einstellungen des *Rights* -Parameters. Legen Sie *Aktionen* nicht auf **adaccessrevofest** , wenn Sie möchten, dass die im *Rights* -Parameter angegebenen Rechte wirksam werden.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Getberechtigungs-Methode (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
