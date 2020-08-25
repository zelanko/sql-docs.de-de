---
description: SetObjectOwner-Methode
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
ms.openlocfilehash: acefd94f29b030a6bee724686e11023a354d8921
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769409"
---
# <a name="setobjectowner-method"></a>SetObjectOwner-Methode
Gibt den Besitzer eines Objekts in einem [Katalog](./catalog-object-adox.md)an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parameter  
 *ObjectName*  
 Ein **Zeichen** folgen Wert, der den Namen des Objekts angibt, für das der Besitzer angegeben werden soll.  
  
 *ObjectType*  
 Ein **Long** -Wert, der eine der [objecttypeer](./objecttypeenum.md) -Konstanten sein kann, die den Besitzertyp angibt.  
  
 *OwnerName*  
 Ein **Zeichen** folgen Wert, der den [Namen](./name-property-adox.md) des [Benutzers](./user-object-adox.md) oder der [Gruppe](./group-object-adox.md) angibt, der Besitzer des Objekts ist.  
  
 *ObjectTypeId*  
 Optional. Ein **Variant** -Wert, der die GUID für einen Anbieter Objekttyp angibt, der nicht von der OLE DB Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* auf **adpermubjproviderspecific**festgelegt ist. Andernfalls wird Sie nicht verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Anbieter die Angabe von Objekt Besitzern nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Catalog-Objekt (ADOX)](./catalog-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die GetObjectOwner-und die-Methode der-Methode (VB)](./getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner-Methode (ADOX)](./getobjectowner-method-adox.md)