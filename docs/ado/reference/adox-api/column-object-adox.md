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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966912"
---
# <a name="column-object-adox"></a>Column-Objekt (ADOX)
Stellt eine Spalte aus einer Tabelle, Index oder Schlüssel.  
  
## <a name="remarks"></a>Hinweise  
 Der folgende Code erstellt ein neues **Spalte**:  
  
 `Dim obj As New Column`  
  
 Mit den Eigenschaften und Auflistungen von einem **Spalte** Objekt ist, können Sie:  
  
-   Identifizieren Sie die Spalte mit dem [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Geben Sie den Datentyp der Spalte mit dem [Type-Eigenschaft (Schlüssel) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md) Eigenschaft.  
  
-   Bestimmen, ob die Spalte mit fester Länge ist, oder wenn es mit null-Werte enthält, kann die [Attribute-Eigenschaft (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) Eigenschaft.  
  
-   Geben Sie die maximale Größe der Spalte mit dem [DefinedSize-Eigenschaft (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) Eigenschaft.  
  
-   Geben Sie für numerische Werte, mit der [NumericScale-Eigenschaft (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) Eigenschaft.  
  
-   Geben Sie mit die maximale Genauigkeit für numerische Daten-Wert, der [Precision-Eigenschaft (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) Eigenschaft.  
  
-   Geben Sie die [Katalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) , die die Spalte mit dem Besitzer der [ParentCatalog-Eigenschaft (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) Eigenschaft.  
  
-   Für Schlüsselspalten, geben Sie den Namen der verknüpften Spalte, in der verknüpften Tabelle mit den [RelatedColumn-Eigenschaft (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) Eigenschaft.  
  
-   Für Indexspalten angeben, ob die Sortierreihenfolge ist aufsteigend oder absteigend mit der [SortOrder-Eigenschaft (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) Eigenschaft.  
  
-   Zugriff auf die anbieterspezifischen Eigenschaften mit den [Eigenschaften-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
> [!NOTE]
>  Nicht alle Eigenschaften der **Spalte** Objekte können vom Datenanbieter unterstützt werden. Wenn Sie einen Wert für eine Eigenschaft festgelegt haben, die der Anbieter nicht unterstützt wird, tritt ein Fehler auf. Für den neuen **Spalte** Objekte aufweist, wird der Fehler auftreten, wenn das Objekt, das die Auflistung angefügt wird. Für vorhandene Objekte tritt der Fehler beim Festlegen der Eigenschaft.  
>   
>  Beim Erstellen von **Spalte** Objekten, die das Vorhandensein einer entsprechenden Standardwert für eine optionale Eigenschaft garantiert nicht, dass es sich bei Ihren Anbieter für die Eigenschaft unterstützt. Weitere Informationen zu den Anbieter Eigenschaften unterstützten finden Sie unter der Dokumentation Ihres Anbieters.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Column-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Spalten und Tabellen Append-Methode, Name-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append-Methode, Typ des Schlüssels, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ADOX-Codebeispiel: NumericScale- und Precision-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [ParentCatalog-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [SortOrder-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
