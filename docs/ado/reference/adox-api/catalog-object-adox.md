---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9843ad9ac0a456f7e38e741e08ce9b66f862fd9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967053"
---
# <a name="catalog-object-adox"></a>Catalog-Objekt (ADOX)
Enthält Sammlungen ([Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md), [Sichten](../../../ado/reference/adox-api/views-collection-adox.md), [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md), [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md)und [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md)), die den Schema Katalog einer Datenquelle beschreiben.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können das **Katalog** Objekt durch Hinzufügen oder Entfernen von Objekten oder durch Ändern vorhandener Objekte ändern. Einige Anbieter unterstützen möglicherweise nicht alle **Katalog** Objekte, oder Sie unterstützen die Anzeige von Schema Informationen.  
  
 Mit den Eigenschaften und Methoden eines **Katalog** Objekts können Sie folgende Aktionen ausführen:  
  
-   Öffnen Sie den Katalog, indem Sie die [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) -Eigenschaft auf ein ADO- [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt oder eine gültige Verbindungs Zeichenfolge festlegen.  
  
-   Erstellen Sie einen neuen Katalog mit der [Create](../../../ado/reference/adox-api/create-method-adox.md) -Methode.  
  
-   Bestimmen Sie die Besitzer der Objekte in einem **Katalog** mit der [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) -Methode und der [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) -Methode.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Error-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog ActiveConnection-Eigenschaft (Beispiel) (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Beispiel für Befehls-und CommandText-Eigenschaften (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Create Method-Beispiel (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Parameter Auflistung, Beispiel für Befehls Eigenschaft (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Beispiel für eine Beispiel Katalog Eigenschaft (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Prozeduren Append-Methode Beispiel (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Prozeduren Delete-Methode (Beispiel) (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Prozeduren Aktualisierungs Methode (Beispiel) (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Beispiel für Sichten und Fields-Auflistungen (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Beispiele für die Append-Methode (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views-Auflistung, CommandText-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Sichten Delete-Methode (Beispiel) (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Ansichten Aktualisierungs Methode (Beispiel) (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Prozeduren (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
