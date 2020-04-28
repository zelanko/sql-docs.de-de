---
title: GetObjectOwner-Methode (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff85491cf7ca30e3f95526aa7043f321a65cccc5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966276"
---
# <a name="getobjectowner-method-adox"></a>GetObjectOwner-Methode (ADOX)
Gibt den Besitzer eines Objekts in einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md)zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Zeichen** folgen Wert zurück, der den [Namen](../../../ado/reference/adox-api/name-property-adox.md) des [Benutzers](../../../ado/reference/adox-api/user-object-adox.md) oder der [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) angibt, der das Objekt besitzt.  
  
#### <a name="parameters"></a>Parameter  
 *ObjectName*  
 Ein **Zeichen** folgen Wert, der den Namen des Objekts angibt, für das der Besitzer zurückgegeben werden soll.  
  
 *ObjectType*  
 Ein **Long** -Wert, bei dem es sich um eine der [objecttypeer](../../../ado/reference/adox-api/objecttypeenum.md) -Konstanten handeln kann, die den Typ des Objekts angibt, für das der Besitzer bestimmt werden soll.  
  
 *ObjectTypeId*  
 (Optional) Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert wird. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Anbieter das Zurückgeben von Objekt Besitzern nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die GetObjectOwner-und die-Methode der-Methode (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [SetObjectOwner-Methode](../../../ado/reference/adox-api/setobjectowner-method.md)
