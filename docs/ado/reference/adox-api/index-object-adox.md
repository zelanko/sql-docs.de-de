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
manager: jroth
ms.openlocfilehash: b6fd63de0b6147b86aa0d6b548669c56aefdcf20
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66706717"
---
# <a name="index-object-adox"></a>Index-Objekt (ADOX)
Stellt einen Index aus einer Datenbanktabelle dar.  
  
## <a name="remarks"></a>Hinweise  
 Der folgende Code erstellt ein neues **Index**:  
  
```  
Dim obj As New Index  
```  
  
 Mit den Eigenschaften und Auflistungen von einer **Index** Objekt ist, können Sie:  
  
-   Identifizieren Sie den Index mit der [Namen](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Zugreifen auf die Datenbankspalten des Index mit der [Spalten](../../../ado/reference/adox-api/columns-collection-adox.md) Auflistung.  
  
-   Gibt an, ob die Indexschlüssel eindeutig sein müssen die [Unique](../../../ado/reference/adox-api/unique-property-adox.md) Eigenschaft.  
  
-   Gibt an, ob der Index den primären Schlüssel für eine Tabelle ist die [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) Eigenschaft.  
  
-   Gibt an, ob die Datensätze, bei denen null-Werte in ihren Indexfeldern Indexeinträge verfügen die [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) Eigenschaft.  
  
-   Gibt an, ob der Index gruppiert ist, mit der [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) Eigenschaft.  
  
-   Zugriff auf die anbieterspezifischen Eigenschaften mit den [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
> [!NOTE]
>  Beim Anfügen, wird ein Fehler auftreten. ein [Spalte](../../../ado/reference/adox-api/column-object-adox.md) auf die **Spalten** Auflistung von ein **Index** Wenn die **Spalte** ist nicht in einem [Tabelle](../../../ado/reference/adox-api/table-object-adox.md) Objekt, das bereits angefügt, um die [Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md) Auflistung.  
  
> [!NOTE]
>  Datenanbieter unterstützen möglicherweise nicht alle Eigenschaften des **Index** Objekte. Wenn Sie einen Wert für eine Eigenschaft festgelegt haben, die vom Anbieter nicht unterstützt wird, wird ein Fehler auftreten. Für den neuen **Index** Objekte aufweist, wird der Fehler auftreten, wenn das Objekt, das die Auflistung angefügt wird. Für vorhandene Objekte tritt der Fehler beim Festlegen der Eigenschaft.  
  
> [!NOTE]
>  Beim Erstellen von **Index** Objekten, die das Vorhandensein einer entsprechenden Standardwert für eine optionale Eigenschaft garantiert nicht, dass es sich bei Ihren Anbieter für die Eigenschaft unterstützt. Weitere Informationen zu den Anbieter Eigenschaften unterstützten finden Sie unter der Dokumentation Ihres Anbieters.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Index-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Indizes Append-Methode – Beispiel (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [IndexNulls-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [PrimaryKey- und Unique-Eigenschaften – Beispiel (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [SortOrder-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Auflistung von Indizes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
