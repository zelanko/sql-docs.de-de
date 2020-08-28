---
description: Count-Eigenschaft (ADO)
title: Count-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
author: rothja
ms.author: jroth
ms.openlocfilehash: b478a9f88d33503c5eda98bda11cfe0e0fcc8d6b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974521"
---
# <a name="count-property-ado"></a>Count-Eigenschaft (ADO)
Gibt die Anzahl der-Objekte in einer Auflistung an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Long** -Wert zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **count** -Eigenschaft, um zu bestimmen, wie viele Objekte in einer bestimmten Sammlung sind.  
  
 Da die Nummerierung für Member einer Auflistung mit Null beginnt, sollten Sie immer Code Schleifen programmieren, die mit dem nullmember beginnen und mit dem Wert der **count** -Eigenschaft minus 1 enden. Wenn Sie Microsoft Visual Basic verwenden und die Mitglieder einer Auflistung durchlaufen möchten, ohne die **count** -Eigenschaft zu überprüfen, verwenden Sie die **for each-... Nächster** Befehl.  
  
 Wenn die **count** -Eigenschaft 0 (null) ist, sind keine Objekte in der Auflistung vorhanden.  
  
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
 [Beispiel für eine Count-Eigenschaft (VB)](./count-property-example-vb.md)   
 [Beispiel für eine Count-Eigenschaft (VC + +)](./count-property-example-vc.md)   
 [Refresh-Methode (ADO)](./refresh-method-ado.md)