---
title: Methode "-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: rothja
ms.author: jroth
ms.openlocfilehash: 615e62ad8a22c50851ea50a2a8511e0859b54652
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763311"
---
# <a name="setobjectowner-method"></a>SetObjectOwner-Methode
Gibt den Besitzer eines Objekts in einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md)an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parameter  
 *ObjectName*  
 Ein **Zeichen** folgen Wert, der den Namen des Objekts angibt, für das der Besitzer angegeben werden soll.  
  
 *ObjectType*  
 Ein **Long** -Wert, der eine der [objecttypeer](../../../ado/reference/adox-api/objecttypeenum.md) -Konstanten sein kann, die den Besitzertyp angibt.  
  
 *OwnerName*  
 Ein **Zeichen** folgen Wert, der den [Namen](../../../ado/reference/adox-api/name-property-adox.md) des [Benutzers](../../../ado/reference/adox-api/user-object-adox.md) oder der [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) angibt, der Besitzer des Objekts ist.  
  
 *ObjectTypeId*  
 Dies ist optional. Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Anbieter die Angabe von Objekt Besitzern nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die GetObjectOwner-und die-Methode der-Methode (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
