---
description: Name-Eigenschaft (ADOX)
title: Name-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::PutName
- _Table::GetName
- _Key::Name
- _Key::get_Name
- _Column::GetName
- _Index::Name
- _Index::put_Name
- _Column::PutName
- _Key::put_Name
- _Table::put_Name
- _User25::PutName
- _Index::get_Name
- _Column::get_Name
- _Group25::Name
- _Group25::get_Name
- _Column::Name
- _User25::get_Name
- _Table::Name
- _Group25::GetName
- _Index::PutName
- _Column::put_Name
- _Key::GetName
- _Table::get_Name
- _User25::Name
- _User25::put_Name
- _Index::GetName
- _User25::GetName
helpviewer_keywords:
- Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
author: rothja
ms.author: jroth
ms.openlocfilehash: dd3a9fd328ce332c409d613ad468b96f0b94d31e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983911"
---
# <a name="name-property-adox"></a>Name-Eigenschaft (ADOX)
Gibt den Namen des Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Namen müssen innerhalb einer Sammlung nicht eindeutig sein.  
  
 Die **Name** -Eigenschaft ist Lese- [/Schreibzugriff](./table-object-adox.md)auf [Spalten](./column-object-adox.md)-, [Gruppen](./group-object-adox.md)-, [Schlüssel](./key-object-adox.md)-, [Index](./index-object-adox.md)-, Tabellen-und [Benutzer](./user-object-adox.md) Objekte. Die **Name** -Eigenschaft ist für [Katalog](./catalog-object-adox.md)-, [Prozedur](./procedure-object-adox.md)-und [Ansichts](./view-object-adox.md) Objekte schreibgeschützt.  
  
 Für Objekte mit Lese- **/Schreibzugriff** (**Spalten**-, **Gruppen**-, **Schlüssel**-, **Index**-, Tabellen-und **Benutzer** Objekte) ist der Standardwert eine leere Zeichenfolge ("").  
  
> [!NOTE]
>  Bei Schlüsseln ist diese Eigenschaft bei **Schlüssel** Objekten, die bereits an eine Auflistung angehängt wurden, schreibgeschützt. Bei Tabellen ist diese Eigenschaft für **Tabellen** Objekte, die bereits an eine Auflistung angehängt wurden, schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Column-Objekt (ADOX)](./column-object-adox.md)  
        [Group-Objekt (ADOX)](./group-object-adox.md)  
        [Index-Objekt (ADOX)](./index-object-adox.md)  
    :::column-end:::
    :::column:::
        [Key-Objekt (ADOX)](./key-object-adox.md)  
        [Procedure-Objekt (ADOX)](./procedure-object-adox.md)  
        [Property-Objekt (ADO)](../ado-api/property-object-ado.md)  
    :::column-end:::
    :::column:::
        [Table-Objekt (ADOX)](./table-object-adox.md)  
        [User-Objekt (ADOX)](./user-object-adox.md)  
        [View-Objekt (ADOX)](./view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog-Eigenschaft – Beispiel (VB)](./parentcatalog-property-example-vb.md)