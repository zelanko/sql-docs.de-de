---
title: Index-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7bff462b7c9ffe115cdfd52d1ec1f0a810a50531
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966082"
---
# <a name="index-object-adox"></a>Index-Objekt (ADOX)
Stellt einen Index aus einer Datenbanktabelle dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit dem folgenden Code wird ein neuer **Index**erstellt:  
  
```  
Dim obj As New Index  
```  
  
 Mit den Eigenschaften und Auflistungen eines **Index** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie den Index mit der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft.  
  
-   Greifen Sie auf die Daten Bank Spalten des Indexes mit der [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) -Auflistung zu.  
  
-   Geben Sie an, ob die Index Schlüssel mit der [Unique](../../../ado/reference/adox-api/unique-property-adox.md) -Eigenschaft eindeutig sein müssen.  
  
-   Geben Sie an, ob der Index der Primärschlüssel für eine Tabelle mit der [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) -Eigenschaft ist.  
  
-   Geben Sie an, ob Datensätze mit NULL-Werten in ihren Indexfeldern Indexeinträge mit der [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) -Eigenschaft aufweisen.  
  
-   Geben Sie an, ob der Index mit der [gruppierten](../../../ado/reference/adox-api/clustered-property-adox.md) Eigenschaft gruppiert wird.  
  
-   Greifen Sie mit der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung auf anbieterspezifische Index Eigenschaften zu.  
  
> [!NOTE]
>  Wenn eine [Spalte](../../../ado/reference/adox-api/column-object-adox.md) an die **Columns** -Auflistung eines **Indexes** angefügt wird, tritt ein Fehler auf, wenn die **Spalte** nicht in einem [Tabellen](../../../ado/reference/adox-api/table-object-adox.md) Objekt vorhanden ist, das bereits an die [Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md) Auflistung angehängt ist.  
  
> [!NOTE]
>  Der Datenanbieter unterstützt möglicherweise nicht alle Eigenschaften von **Index** Objekten. Wenn Sie einen Wert für eine Eigenschaft festgelegt haben, die nicht vom Anbieter unterstützt wird, tritt ein Fehler auf. Bei neuen **Index** Objekten tritt der Fehler auf, wenn das Objekt an die Auflistung angefügt wird. Bei vorhandenen Objekten tritt der Fehler auf, wenn die-Eigenschaft festgelegt wird.  
  
> [!NOTE]
>  Wenn Sie **Index** Objekte erstellen, gewährleistet das vorhanden sein eines entsprechenden Standardwerts für eine optionale Eigenschaft nicht, dass der Anbieter die-Eigenschaft unterstützt. Weitere Informationen zu den Eigenschaften, die der Anbieter unterstützt, finden Sie in der Dokumentation des Anbieters.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Index-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Index Append-Methode (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Beispiel für IndexNulls-Eigenschaft (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [Beispiel für PrimaryKey und Unique Properties (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [Sortorider-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Indexes-Auflistung (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
