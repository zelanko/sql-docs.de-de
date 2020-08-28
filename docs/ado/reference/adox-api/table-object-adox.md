---
description: Table-Objekt (ADOX)
title: Table-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table
helpviewer_keywords:
- Table object [ADOX]
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
author: rothja
ms.author: jroth
ms.openlocfilehash: f6803b4afc7f50a08f305a619e9c0ca328e5e988
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983251"
---
# <a name="table-object-adox"></a>Table-Objekt (ADOX)
Stellt eine Datenbanktabelle mit Spalten, Indizes und Schlüsseln dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Der folgende Code erstellt eine neue **Tabelle**:  
  
```  
Dim obj As New Table  
```  
  
 Mit den Eigenschaften und Auflistungen eines **Table** -Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie die Tabelle mit der Eigenschaft [Name Property (ADOX)](./name-property-adox.md) .  
  
-   Bestimmen Sie den Typ der Tabelle mit der Eigenschaft [Type Property (Table) (ADOX)](./type-property-table-adox.md) .  
  
-   Greifen Sie auf die Daten Bank Spalten der Tabelle mit der Auflistung [Columns Collection (ADOX)](./columns-collection-adox.md) zu.  
  
-   Greifen Sie mit der Indexes-Auflistung [(ADOX)](./indexes-collection-adox.md)auf die Indizes der Tabelle zu.  
  
-   Greifen Sie mit der Keys-Auflistung [(ADOX)](./keys-collection-adox.md)auf die Schlüssel der Tabelle zu.  
  
-   Geben Sie den Katalog, der die Tabelle besitzt, mit der Eigenschaft " [Eigenschaft (Eigenschaft)](./parentcatalog-property-adox.md) " an.  
  
-   Gibt Datumsinformationen mit den Eigenschaften der [DateCreated-Eigenschaft (ADOX)](./datecreated-property-adox.md) und der [DateModified-Eigenschaft (ADOX)](./datemodified-property-adox.md) zurück.  
  
-   Zugreifen auf anbieterspezifische Tabellen Eigenschaften mit der [Properties Collection (ADO)](../ado-api/properties-collection-ado.md) -Auflistung.  
  
> [!NOTE]
>  Der Datenanbieter unterstützt möglicherweise nicht alle Eigenschaften von **Tabellen** Objekten. Wenn Sie einen Wert für eine Eigenschaft festgelegt haben, die vom Anbieter nicht unterstützt wird, tritt ein Fehler auf. Bei neuen **Tabellen** Objekten tritt der Fehler auf, wenn das Objekt an die Auflistung angefügt wird. Bei vorhandenen Objekten tritt der Fehler auf, wenn die-Eigenschaft festgelegt wird.  
>   
>  Wenn Sie **Tabellen** Objekte erstellen, gewährleistet das vorhanden sein eines entsprechenden Standardwerts für eine optionale Eigenschaft nicht, dass der Anbieter die-Eigenschaft unterstützt. Weitere Informationen zu den Eigenschaften, die der Anbieter unterstützt, finden Sie in der Dokumentation des Anbieters.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Table-Objekt – Eigenschaften, Methoden und Ereignisse](./table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog ActiveConnection-Eigenschaft (Beispiel) (VB)](./catalog-activeconnection-property-example-vb.md)   
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB)](./connection-close-method-table-type-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Beispiel für eine Beispiel Katalog Eigenschaft (VB)](./parentcatalog-property-example-vb.md)   
 [Columns-Auflistung (ADOX)](./columns-collection-adox.md)   
 [Indexes-Auflistung (ADOX)](./indexes-collection-adox.md)   
 [Keys-Auflistung (ADOX)](./keys-collection-adox.md)   
 [Properties-Auflistung (ADO)](../ado-api/properties-collection-ado.md)   
 [Tables-Collection (ADOX)](./tables-collection-adox.md)