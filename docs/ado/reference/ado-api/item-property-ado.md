---
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
ms.openlocfilehash: 2bc6cb28823a2b8faf79e4bf44fb405446e12514
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242660"
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
        [Axes-Collection (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)  
        [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
        [CubeDefs-Collection (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)  
        [Dimension-Collection (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)  
        [Errors-Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
        [Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
        [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Hierarchies-Collection (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)  
        [Auflistung von Indizes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
        [Keys Collection (ADOX) (Keys-Auflistung (ADOX))](../../../ado/reference/adox-api/keys-collection-adox.md)  
        [Levels-Collection (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)  
        [Members-Collection (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)  
        [Parameters-Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Positions-Collection (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)  
        [Procedures Collection (ADOX) (Procedures-Auflistung (ADOX))](../../../ado/reference/adox-api/procedures-collection-adox.md)  
        [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)  
        [Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)  
        [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
        [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Element Eigenschaft (VB)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Item-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/item-property-example-vc.md)   
