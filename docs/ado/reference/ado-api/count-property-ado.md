---
title: Count-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 292a4a8c26b3b10aa47fcbe7046a5897f601ed9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919356"
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
  
||||  
|-|-|-|  
|[Axes-Collection (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns-Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs-Collection (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimension-Collection (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors-Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups-Collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies-Collection (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes-Collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys-Collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels-Collection (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members-Collection (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters-Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Positions-Collection (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures-Collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables-Collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Users-Collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views-Collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Count-Eigenschaft (VB)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Beispiel für eine Count-Eigenschaft (VC + +)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Refresh-Methode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
