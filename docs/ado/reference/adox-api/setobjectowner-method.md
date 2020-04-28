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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50a02898c1694fa43b8bf522a1a1bca65300efda
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965238"
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
 (Optional) Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Anbieter die Angabe von Objekt Besitzern nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die GetObjectOwner-und die-Methode der-Methode (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
