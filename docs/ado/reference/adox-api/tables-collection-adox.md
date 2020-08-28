---
description: Tables-Collection (ADOX)
title: Tables-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 0b6d580dd6f56f78947ff1a881db1bff28c3e2b8
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983261"
---
# <a name="tables-collection-adox"></a>Tables-Collection (ADOX)
Enthält alle [Tabellen](./table-object-adox.md) Objekte eines Katalogs.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Append](./append-method-adox-tables.md) -Methode für eine **Tabellen** Sammlung ist für ADOX eindeutig. Sie haben folgende Möglichkeiten:  
  
-   Fügen Sie der Auflistung mithilfe der **Append** -Methode eine neue Tabelle hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Sie haben folgende Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../ado-api/item-property-ado.md) -Eigenschaft auf eine Tabelle in der-Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Tabellen mit der [count](../ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernen Sie eine Tabelle aus der Sammlung mit der [Delete](./delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das aktuelle Datenbankschema mit der [Refresh](../ado-api/refresh-method-ado.md) -Methode widerzuspiegeln.  
  
 Einige Anbieter geben möglicherweise andere Schema Objekte, z. b. eine Sicht, in der **Tables** -Auflistung zurück. Daher können einige ADOX-Auflistungen mehrere Verweise auf dasselbe Objekt enthalten. Wenn Sie das Objekt aus einer Auflistung löschen, ist die Änderung in einer anderen Sammlung, die auf das gelöschte Objekt verweist, erst dann sichtbar, wenn die **Aktualisierungs** Methode für die Auflistung aufgerufen wird. Beispielsweise werden mit dem OLE DB-Anbieter für Microsoft Jet Sichten mit der **Tables** -Auflistung zurückgegeben. Wenn Sie eine Ansicht löschen, müssen Sie die **Tabellen** Auflistung aktualisieren, bevor die Sammlung die Änderung widerspiegelt.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Tables-Collection – Eigenschaften, Methoden und Ereignisse](./tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog ActiveConnection-Eigenschaft (Beispiel) (VB)](./catalog-activeconnection-property-example-vb.md)   
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB)](./connection-close-method-table-type-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Catalog-Objekt (ADOX)](./catalog-object-adox.md)   
 [Table-Objekt (ADOX)](./table-object-adox.md)