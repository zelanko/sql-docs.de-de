---
title: Column-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db2c2dbe6af2a50fc2507a9ade92d83e0502f2ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966912"
---
# <a name="column-object-adox"></a>Column-Objekt (ADOX)
Stellt eine Spalte aus einer Tabelle, einem Index oder einem Schlüssel dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Der folgende Code erstellt eine neue **Spalte**:  
  
 `Dim obj As New Column`  
  
 Mit den Eigenschaften und Auflistungen eines **Spalten** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie die Spalte mit der Eigenschaft [Name Property (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Geben Sie den Datentyp der Spalte mit der Eigenschaft [Type Property (Key) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md) an.  
  
-   Bestimmen Sie, ob die Spalte eine festgelegte Länge hat oder ob Sie NULL-Werte mit der Eigenschaft " [Attributeigenschaft" (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) enthalten kann.  
  
-   Geben Sie die maximale Größe der Spalte mit der Eigenschaft [DefinedSize (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) an.  
  
-   Geben Sie für numerische Datenwerte die Skala mit der Eigenschaft " [NumericScale Property (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) " an.  
  
-   Geben Sie als Wert für numerische Daten die maximale Genauigkeit mit der Eigenschaft für die [Precision-Eigenschaft (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) an.  
  
-   Geben Sie das [Catalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) an, das die Spalte besitzt, mit der Eigenschaft " [Eigenschaft" (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) .  
  
-   Geben Sie für Schlüssel Spalten den Namen der verknüpften Spalte in der verknüpften Tabelle mit der Eigenschaft [RelatedColumn-Eigenschaft (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) an.  
  
-   Geben Sie für Index Spalten an, ob die Sortierreihenfolge aufsteigend oder absteigend mit der Eigenschaft [sortor der Eigenschaft (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) ist.  
  
-   Zugreifen auf anbieterspezifische Eigenschaften mit der [Properties Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung.  
  
> [!NOTE]
>  Nicht alle Eigenschaften von **Spalten** Objekten können von Ihrem Datenanbieter unterstützt werden. Wenn Sie einen Wert für eine Eigenschaft festgelegt haben, die vom Anbieter nicht unterstützt wird, tritt ein Fehler auf. Bei neuen **Spalten** Objekten tritt der Fehler auf, wenn das Objekt an die Auflistung angefügt wird. Bei vorhandenen Objekten tritt der Fehler auf, wenn die-Eigenschaft festgelegt wird.  
>   
>  Beim Erstellen von **Spalten** Objekten garantiert das vorhanden sein eines entsprechenden Standardwerts für eine optionale Eigenschaft nicht, dass der Anbieter die-Eigenschaft unterstützt. Weitere Informationen zu den Eigenschaften, die der Anbieter unterstützt, finden Sie in der Dokumentation des Anbieters.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Column-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ADOX-Code Beispiel: Beispiel für NumericScale und Precision Properties (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Beispiel für eine Beispiel Katalog Eigenschaft (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Sortorider-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
