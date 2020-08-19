---
description: Name-Eigenschaft (ADOX)
title: Name-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: dbd0d9088ea39d604c53c462448ae1c94b3a9052
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439782"
---
# <a name="name-property-adox"></a>Name-Eigenschaft (ADOX)
Gibt den Namen des Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Namen müssen innerhalb einer Sammlung nicht eindeutig sein.  
  
 Die **Name** -Eigenschaft ist Lese- [/Schreibzugriff](../../../ado/reference/adox-api/table-object-adox.md)auf [Spalten](../../../ado/reference/adox-api/column-object-adox.md)-, [Gruppen](../../../ado/reference/adox-api/group-object-adox.md)-, [Schlüssel](../../../ado/reference/adox-api/key-object-adox.md)-, [Index](../../../ado/reference/adox-api/index-object-adox.md)-, Tabellen-und [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) Objekte. Die **Name** -Eigenschaft ist für [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md)-, [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md)-und [Ansichts](../../../ado/reference/adox-api/view-object-adox.md) Objekte schreibgeschützt.  
  
 Für Objekte mit Lese- **/Schreibzugriff** (**Spalten**-, **Gruppen**-, **Schlüssel**-, **Index**-, Tabellen-und **Benutzer** Objekte) ist der Standardwert eine leere Zeichenfolge ("").  
  
> [!NOTE]
>  Bei Schlüsseln ist diese Eigenschaft bei **Schlüssel** Objekten, die bereits an eine Auflistung angehängt wurden, schreibgeschützt. Bei Tabellen ist diese Eigenschaft für **Tabellen** Objekte, die bereits an eine Auflistung angehängt wurden, schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
        [Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)  
        [Index-Objekt (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)  
    :::column-end:::
    :::column:::
        [Key-Objekt (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)  
        [Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)  
        [Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)  
    :::column-end:::
    :::column:::
        [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
        [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
        [View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
