---
title: SetObjectOwner-Methode | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 43f325382cc556d75d7ab08c5b3dbdc94f68704f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281769"
---
# <a name="setobjectowner-method"></a>SetObjectOwner-Methode
Gibt den Besitzer eines Objekts in eine [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parameter  
 *ObjectName*  
 Ein **Zeichenfolge** -Wert, der den Namen des Objekts, für das an den Besitzer angibt.  
  
 *ObjectType*  
 Ein **lange** Wert möglich von der [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) Konstanten, der den Besitzer angibt.  
  
 *OwnerName*  
 Ein **Zeichenfolge** Wert, der angibt, die [Namen](../../../ado/reference/adox-api/name-property-adox.md) von der [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) oder [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) zum Besitzer des Objekts sein.  
  
 *ObjectTypeId*  
 Dies ist optional. Ein **Variant** Wert, der die GUID für einen Anbieter-Objekttyp angibt, die nicht vom OLE DB-Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* nastaven NA hodnotu **AdPermObjProviderSpecific**ist, andernfalls wird er nicht verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Anbieter die Angabe von Objektbesitzern nicht unterstützt wird, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetObjectOwner- und SetObjectOwner-Methoden – Beispiel (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
