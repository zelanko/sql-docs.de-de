---
description: ParentCatalog-Eigenschaft (ADOX)
title: Para Catalog-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User::get_ParentCatalog
- _Column::ParentCatalog
- _Table::put_ParentCatalog
- _Group::put_ParentCatalog
- _Column::get_ParentCatalog
- _Table::PutParentCatalog
- _Group::putref_ParentCatalog
- _Group::ParentCatalog
- _Column::PutParentCatalog
- _Column::put_ParentCatalog
- _Group::get_ParentCatalog
- _User::put_ParentCatalog
- _User::putref_ParentCatalog
- _Table::get_ParentCatalog
- _Group::PutParentCatalog
- _Table::ParentCatalog
- _Column::GetParentCatalog
- _Table::PutRefParentCatalog
- _User::GetParentCatalog
- _Table::GetParentCatalog
- _Table::putref_ParentCatalog
- _User::PutParentCatalog
- _User::ParentCatalog
- _User::PutRefParentCatalog
- _Group::GetParentCatalog
- _Group::PutRefParentCatalog
helpviewer_keywords:
- ParentCatalog property [ADOX]
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
author: rothja
ms.author: jroth
ms.openlocfilehash: 93d15cdac3d8f7a47c74a783d176d806271f68a3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439722"
---
# <a name="parentcatalog-property-adox"></a>ParentCatalog-Eigenschaft (ADOX)
Gibt den übergeordneten Katalog einer Tabelle, eines Benutzers oder eines Spalten Objekts an, um Zugriff auf anbieterspezifische Eigenschaften bereitzustellen.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt ein [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md) Objekt fest und gibt dieses zurück. Durch Festlegen von " **parametricatalog** " auf einen geöffneten **Katalog** wird der Zugriff auf anbieterspezifische Eigenschaften ermöglicht, bevor eine Tabelle oder Spalte an eine **Katalog** Auflistung angehängt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Einige Datenanbieter erlauben, dass anbieterspezifische Eigenschaftswerte nur bei der Erstellung geschrieben werden, d. h., wenn eine Tabelle oder Spalte an die zugehörige **Katalog** Auflistung angefügt wird. Wenn Sie auf diese Eigenschaften zugreifen möchten, bevor Sie diese Objekte an einen **Katalog**anfügen, geben Sie zuerst den **Katalog** in der Eigenschaft " **parametricatalog** " an.  
  
 Ein Fehler tritt auf, wenn die Tabelle oder die Spalte an einen anderen **Katalog** angefügt wird als der " **parametricatalog**".  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [ParentCatalog-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
