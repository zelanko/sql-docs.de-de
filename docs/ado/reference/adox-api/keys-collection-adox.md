---
description: Keys-Collection (ADOX)
title: Keys-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table::Keys
- Keys
helpviewer_keywords:
- Keys collection [ADOX]
ms.assetid: cdb31c76-e559-475c-b33a-aac24f73e70e
author: rothja
ms.author: jroth
ms.openlocfilehash: 675584dd52cd1a403b9d9d44351b86e88caba382
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983981"
---
# <a name="keys-collection-adox"></a>Keys-Collection (ADOX)
Enthält alle [Schlüssel](./key-object-adox.md) Objekte einer [Tabelle](./table-object-adox.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Append](./append-method-adox-keys.md) -Methode für eine [Keys]() -Auflistung ist für ADOX eindeutig. Sie haben folgende Möglichkeiten:  
  
-   Fügen Sie der Auflistung mithilfe der [Append](./append-method-adox-keys.md) -Methode einen neuen Schlüssel hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Sie haben folgende Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../ado-api/item-property-ado.md) -Eigenschaft auf einen Schlüssel in der Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Schlüssel mit der [count](../ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernt einen Schlüssel aus der Auflistung mit der [Delete](./delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das Schema der aktuellen Datenbank mit [der Aktualisierungs Methode](../ado-api/refresh-method-ado.md) widerzuspiegeln.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Indexes-Collections – Eigenschaften, Methoden und Ereignisse](./indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Eigenschaften, Methoden und Ereignisse der Schlüssel Sammlung](./keys-collection-properties-methods-and-events.md)   
 [Key-Objekt (ADOX)](./key-object-adox.md)