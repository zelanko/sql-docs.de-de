---
title: Table-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5af59dbc50f6e1a2cd95cbdf99874d860eceeb1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622338"
---
# <a name="table-object-adox"></a>Table-Objekt (ADOX)
Stellt eine Datenbanktabelle, einschließlich Spalten, Indizes und Schlüssel dar.  
  
## <a name="remarks"></a>Hinweise  
 Der folgende Code erstellt ein neues **Tabelle**:  
  
```  
Dim obj As New Table  
```  
  
 Mit den Eigenschaften und Auflistungen von einem **Tabelle** Objekt ist, können Sie:  
  
-   Identifizieren Sie die Tabelle mit den [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Bestimmen Sie den Typ der Tabelle mit den [Type-Eigenschaft (Tabelle) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md) Eigenschaft.  
  
-   Zugriff auf die Datenbankspalten der Tabelle mit den [Spalten Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md) Auflistung.  
  
-   Zugreifen auf die Indizes der Tabelle mit den [Indizes-Auflistung (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md).  
  
-   Zugreifen auf die Schlüssel der Tabelle mit den [Keys-Auflistung (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md).  
  
-   Geben Sie den Katalog, der die Tabelle besitzt die [ParentCatalog-Eigenschaft (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) Eigenschaft.  
  
-   Zurückgeben von Datumsinformationen der [DateCreated-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md) und [DateModified-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md) Eigenschaften.  
  
-   Zugriff auf die anbieterspezifischen Eigenschaften mit den [Eigenschaften-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
> [!NOTE]
>  Datenanbieter unterstützen möglicherweise nicht alle Eigenschaften des **Tabelle** Objekte. Wenn Sie einen Wert für eine Eigenschaft festgelegt haben, die der Anbieter nicht unterstützt wird, tritt ein Fehler auf. Für den neuen **Tabelle** Objekte aufweist, wird der Fehler auftreten, wenn das Objekt, das die Auflistung angefügt wird. Für vorhandene Objekte tritt der Fehler beim Festlegen der Eigenschaft.  
>   
>  Beim Erstellen von **Tabelle** Objekten, die das Vorhandensein einer entsprechenden Standardwert für eine optionale Eigenschaft garantiert nicht, dass es sich bei Ihren Anbieter für die Eigenschaft unterstützt. Weitere Informationen zu den Anbieter Eigenschaften unterstützten finden Sie unter der Dokumentation Ihres Anbieters.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Table-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Katalog ActiveConnection-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Spalten und Tabellen Append-Methode, Name-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Connection Close-Methode, Table Type-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Keys Append-Methode, Typ des Schlüssels, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Auflistung von Indizes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Keys-Auflistung (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
