---
title: Tables-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
author: rothja
ms.author: jroth
ms.openlocfilehash: f788376d76692f3dc86011cc1d35b293116250a3
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763281"
---
# <a name="tables-collection-adox"></a>Tables-Collection (ADOX)
Enthält alle [Tabellen](../../../ado/reference/adox-api/table-object-adox.md) Objekte eines Katalogs.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-tables.md) -Methode für eine **Tabellen** Sammlung ist für ADOX eindeutig. Ihre Möglichkeiten:  
  
-   Fügen Sie der Auflistung mithilfe der **Append** -Methode eine neue Tabelle hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Ihre Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../../../ado/reference/ado-api/item-property-ado.md) -Eigenschaft auf eine Tabelle in der-Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Tabellen mit der [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernen Sie eine Tabelle aus der Sammlung mit der [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das aktuelle Datenbankschema mit der [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode widerzuspiegeln.  
  
 Einige Anbieter geben möglicherweise andere Schema Objekte, z. b. eine Sicht, in der **Tables** -Auflistung zurück. Daher können einige ADOX-Auflistungen mehrere Verweise auf dasselbe Objekt enthalten. Wenn Sie das Objekt aus einer Auflistung löschen, ist die Änderung in einer anderen Sammlung, die auf das gelöschte Objekt verweist, erst dann sichtbar, wenn die **Aktualisierungs** Methode für die Auflistung aufgerufen wird. Beispielsweise werden mit dem OLE DB-Anbieter für Microsoft Jet Sichten mit der **Tables** -Auflistung zurückgegeben. Wenn Sie eine Ansicht löschen, müssen Sie die **Tabellen** Auflistung aktualisieren, bevor die Sammlung die Änderung widerspiegelt.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Tables Collection Properties, Methods, and Events (Tables-Auflistung – Eigenschaften, Methoden und Ereignisse)](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog ActiveConnection-Eigenschaft (Beispiel) (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Catalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
