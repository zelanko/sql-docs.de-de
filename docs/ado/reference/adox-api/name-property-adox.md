---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f078f8664ce0386bba6069d771ba880b1c02e026
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743036"
---
# <a name="name-property-adox"></a>Name-Eigenschaft (ADOX)
Gibt den Namen des Objekts.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert.  
  
## <a name="remarks"></a>Hinweise  
 Namen müssen nicht in einer Auflistung eindeutig sein.  
  
 Die **Namen** Eigenschaft ist Lese-/Schreibzugriff in [Spalte](../../../ado/reference/adox-api/column-object-adox.md), [Gruppe](../../../ado/reference/adox-api/group-object-adox.md), [Schlüssel](../../../ado/reference/adox-api/key-object-adox.md), [Index](../../../ado/reference/adox-api/index-object-adox.md), [ Tabelle](../../../ado/reference/adox-api/table-object-adox.md), und [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) Objekte. Die **Namen** Eigenschaft ist schreibgeschützt und auf [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md), [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md), und [Ansicht](../../../ado/reference/adox-api/view-object-adox.md) Objekte.  
  
 Für Lese-/Schreibzugriff-Objekte (**Spalte**, **Gruppe**, **Schlüssel**, **Index**, **Tabelle** und  **Benutzer** Objekte), der Standardwert ist eine leere Zeichenfolge ("").  
  
> [!NOTE]
>  Für Schlüssel, diese Eigenschaft ist schreibgeschützt und auf **Schlüssel** Objekte, die bereits an eine Auflistung angefügt. Bei Tabellen wird diese Eigenschaft ist nur Lesezugriff für **Tabelle** Objekte, die bereits an eine Auflistung angefügt.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Index-Objekt (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Key-Objekt (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)|[Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Spalten und Tabellen Append-Methode, Name-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append-Methode, Typ des Schlüssels, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
