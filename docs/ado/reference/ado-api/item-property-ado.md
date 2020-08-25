---
description: Item-Eigenschaft (ADO)
title: Item-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bea35ef148aa2f5646420a1c2b46197ce66f0d6
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774679"
---
# <a name="item-property-ado"></a>Item-Eigenschaft (ADO)
Gibt einen bestimmten Member einer Auflistung anhand des Namens oder der Ordinalzahl an.  
  
## <a name="syntax"></a>Syntax  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen Objekt Verweis zurück.  
  
## <a name="parameters"></a>Parameter  
 *Index*  
 Ein **Variant** -Ausdruck, der entweder den Namen oder die Ordinalzahl eines Objekts in einer Auflistung ergibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Item** -Eigenschaft, um ein bestimmtes Objekt in einer Auflistung zurückzugeben. Wenn das **Element** ein Objekt in der Auflistung nicht finden kann, das dem *Index* Argument entspricht, tritt ein Fehler auf. Außerdem unterstützen einige Sammlungen benannte Objekte nicht. für diese Auflistungen müssen Sie Verweise auf Ordinalzahlen verwenden.  
  
 Die **Item** -Eigenschaft ist die Standard Eigenschaft für alle Auflistungen. Daher sind die folgenden Syntax Formen austauschbar:  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Axes-Collection (ADO MD)](../ado-md-api/axes-collection-ado-md.md)  
        [Columns-Collection (ADOX)](../adox-api/columns-collection-adox.md)  
        [CubeDefs-Collection (ADO MD)](../ado-md-api/cubedefs-collection-ado-md.md)  
        [Dimension-Collection (ADO MD)](../ado-md-api/dimensions-collection-ado-md.md)  
        [Errors-Collection (ADO)](./errors-collection-ado.md)  
        [Fields-Collection (ADO)](./fields-collection-ado.md)  
        [Groups-Collection (ADOX)](../adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Hierarchies-Collection (ADO MD)](../ado-md-api/hierarchies-collection-ado-md.md)  
        [Indexes-Collection (ADOX)](../adox-api/indexes-collection-adox.md)  
        [Keys-Collection (ADOX)](../adox-api/keys-collection-adox.md)  
        [Levels-Collection (ADO MD)](../ado-md-api/levels-collection-ado-md.md)  
        [Members-Collection (ADO MD)](../ado-md-api/members-collection-ado-md.md)  
        [Parameters-Collection (ADO)](./parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Positions-Collection (ADO MD)](../ado-md-api/positions-collection-ado-md.md)  
        [Procedures-Collection (ADOX)](../adox-api/procedures-collection-adox.md)  
        [Properties-Collection (ADO)](./properties-collection-ado.md)  
        [Tables-Collection (ADOX)](../adox-api/tables-collection-adox.md)  
        [Users-Collection (ADOX)](../adox-api/users-collection-adox.md)  
        [Views-Collection (ADOX)](../adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Element Eigenschaft (VB)](./item-property-example-vb.md)   
 [Item-Eigenschaft – Beispiel (VC++)](./item-property-example-vc.md)