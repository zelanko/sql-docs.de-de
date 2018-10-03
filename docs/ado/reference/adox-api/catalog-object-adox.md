---
title: Katalogobjekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5547090443e2f22a135234853b76480fb8295e14
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634418"
---
# <a name="catalog-object-adox"></a>Catalog-Objekt (ADOX)
Enthält Auflistungen ([Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md), [Ansichten](../../../ado/reference/adox-api/views-collection-adox.md), [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md), [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md), und [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md)), Beschreiben Sie den Schema-Katalog für die Datenquelle an.  
  
## <a name="remarks"></a>Hinweise  
 Sie können die **Katalog** Objekt durch Hinzufügen oder Entfernen von Objekten oder durch Ändern von vorhandenen Objekten. Einige Anbieter unterstützen möglicherweise nicht alle von der **Katalog** Objekte oder unterstützen nur das Anzeigen von Schemainformationen.  
  
 Mit den Eigenschaften und Methoden einer **Katalog** Objekt ist, können Sie:  
  
-   Öffnen Sie den Katalog durch Festlegen der [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) Eigenschaft, um ein ADO [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt oder eine gültige Verbindungszeichenfolge.  
  
-   Erstellen Sie einen neuen Katalog mit den [erstellen](../../../ado/reference/adox-api/create-method-adox.md) Methode.  
  
-   Bestimmen der Besitzer der Objekte in einem **Katalog** mit der [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) und [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) Methoden.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Error-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Katalog ActiveConnection-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Befehl und CommandText-Eigenschaft-Beispiel (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Erstellen Sie die Methode – Beispiel (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Keys Append-Methode, Typ des Schlüssels, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Parameters-Auflistung, Command-Eigenschaft-Beispiel (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [ParentCatalog-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Prozeduren Append-Methode – Beispiel (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Prozeduren Delete-Methode – Beispiel (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Prozeduren Refresh-Methode – Beispiel (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Ansichten und Felder Auflistungen – Beispiel (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Ansichten Append-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views Collection, CommandText-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Views Delete-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views Refresh-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Procedures-Auflistung (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
