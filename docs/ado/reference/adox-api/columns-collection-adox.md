---
description: Columns-Collection (ADOX)
title: Columns-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index::Columns
- Table::Columns
- Key::Columns
- Columns
helpviewer_keywords:
- Columns collection [ADOX]
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c0e37715077af500e0c5cc023021765a9e4978d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770979"
---
# <a name="columns-collection-adox"></a>Columns-Collection (ADOX)
Enthält alle [Spalten](./column-object-adox.md) Objekte einer Tabelle, eines Indexes oder eines Schlüssels.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Append](./append-method-adox-columns.md) -Methode für eine **Columns** -Auflistung ist für ADOX eindeutig. Ihre Möglichkeiten:  
  
-   Fügen Sie der Auflistung mithilfe der **Append** -Methode eine neue Spalte hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Ihre Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../ado-api/item-property-ado.md) -Eigenschaft auf eine Spalte in der Auflistung zu.  
  
-   Gibt die Anzahl der Spalten zurück, die in der Auflistung enthalten sind, mit der [count](../ado-api/count-property-ado.md) -Eigenschaft.  
  
-   Entfernen Sie eine Spalte aus der Sammlung mit der [Delete](./delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das Schema der aktuellen Datenbank mit [der Aktualisierungs Methode](../ado-api/refresh-method-ado.md) widerzuspiegeln.  
  
> [!NOTE]
>  Wenn eine **Spalte** an die **Columns** -Auflistung eines [Indexes](./index-object-adox.md) angefügt wird, tritt ein Fehler auf, wenn die **Spalte** nicht in einer [Tabelle](./table-object-adox.md) vorhanden ist, die bereits an die [Tabellen](./tables-collection-adox.md) Auflistung angehängt ist.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Columns-Collection – Eigenschaften, Methoden und Ereignisse](./columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB)](./connection-close-method-table-type-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Beispiel für eine Beispiel Katalog Eigenschaft (VB)](./parentcatalog-property-example-vb.md)   
 [Sortorider-Eigenschafts Beispiel (VB)](./sortorder-property-example-vb.md)   
 [Column-Objekt (ADOX)](./column-object-adox.md)