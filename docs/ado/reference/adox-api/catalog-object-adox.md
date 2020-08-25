---
description: Catalog-Objekt (ADOX)
title: Catalog-Objekt (ADOX) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 968142adb0cb633a19a574c2d0994360faa3fadb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771199"
---
# <a name="catalog-object-adox"></a>Catalog-Objekt (ADOX)
Enthält Sammlungen ([Tabellen](./tables-collection-adox.md), [Sichten](./views-collection-adox.md), [Benutzer](./users-collection-adox.md), [Gruppen](./groups-collection-adox.md)und [Prozeduren](./procedures-collection-adox.md)), die den Schema Katalog einer Datenquelle beschreiben.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können das **Katalog** Objekt durch Hinzufügen oder Entfernen von Objekten oder durch Ändern vorhandener Objekte ändern. Einige Anbieter unterstützen möglicherweise nicht alle **Katalog** Objekte, oder Sie unterstützen die Anzeige von Schema Informationen.  
  
 Mit den Eigenschaften und Methoden eines **Katalog** Objekts können Sie folgende Aktionen ausführen:  
  
-   Öffnen Sie den Katalog, indem Sie die [ActiveConnection](./activeconnection-property-adox.md) -Eigenschaft auf ein ADO- [Verbindungs](../ado-api/connection-object-ado.md) Objekt oder eine gültige Verbindungs Zeichenfolge festlegen.  
  
-   Erstellen Sie einen neuen Katalog mit der [Create](./create-method-adox.md) -Methode.  
  
-   Bestimmen Sie die Besitzer der Objekte in einem **Katalog** mit der [GetObjectOwner](./getobjectowner-method-adox.md) -Methode und der [SetObjectOwner](./setobjectowner-method.md) -Methode.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Catalog-Objekt – Eigenschaften, Methoden und Ereignisse](./catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog ActiveConnection-Eigenschaft (Beispiel) (VB)](./catalog-activeconnection-property-example-vb.md)   
 [Beispiel für Befehls-und CommandText-Eigenschaften (VB)](./command-and-commandtext-properties-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB)](./connection-close-method-table-type-property-example-vb.md)   
 [Create Method-Beispiel (VB)](./create-method-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Parameter Auflistung, Beispiel für Befehls Eigenschaft (VB)](./parameters-collection-command-property-example-vb.md)   
 [Beispiel für eine Beispiel Katalog Eigenschaft (VB)](./parentcatalog-property-example-vb.md)   
 [Prozeduren Append-Methode Beispiel (VB)](./procedures-append-method-example-vb.md)   
 [Prozeduren Delete-Methode (Beispiel) (VB)](./procedures-delete-method-example-vb.md)   
 [Prozeduren Aktualisierungs Methode (Beispiel) (VB)](./procedures-refresh-method-example-vb.md)   
 [Beispiel für Sichten und Fields-Auflistungen (VB)](./views-and-fields-collections-example-vb.md)   
 [Beispiele für die Append-Methode (VB)](./views-append-method-example-vb.md)   
 [Views-Auflistung, CommandText-Eigenschafts Beispiel (VB)](./views-collection-commandtext-property-example-vb.md)   
 [Sichten Delete-Methode (Beispiel) (VB)](./views-delete-method-example-vb.md)   
 [Ansichten Aktualisierungs Methode (Beispiel) (VB)](./views-refresh-method-example-vb.md)   
 [Groups-Auflistung (ADOX)](./groups-collection-adox.md)   
 [Prozeduren (ADOX)](./procedures-collection-adox.md)   
 [Tables-Auflistung (ADOX)](./tables-collection-adox.md)   
 [Users-Auflistung (ADOX)](./users-collection-adox.md)   
 [Views-Collection (ADOX)](./views-collection-adox.md)