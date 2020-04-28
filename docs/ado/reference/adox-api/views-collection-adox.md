---
title: Views-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog::Views
- Views
helpviewer_keywords:
- Views collection [ADOX]
ms.assetid: a55d380c-2b7b-4b57-af74-8ba0b3de0db9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0cec2462f8726e7c580a7d6755394c6c3f07c85b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964770"
---
# <a name="views-collection-adox"></a>Views-Collection (ADOX)
Enthält alle [Ansichts](../../../ado/reference/adox-api/view-object-adox.md) Objekte eines Katalogs.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-views.md) -Methode für eine **views** -Auflistung ist für ADOX eindeutig. Sie haben folgende Möglichkeiten:  
  
-   Fügen Sie der Auflistung mithilfe der **Append** -Methode eine neue Ansicht hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Sie haben folgende Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../../../ado/reference/ado-api/item-property-ado.md) -Eigenschaft auf eine Ansicht in der Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Sichten mit der [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernen Sie eine Ansicht aus der Auflistung mit der [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das aktuelle Datenbankschema mit der [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode widerzuspiegeln.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Views Collection Properties, Methods, and Events (Views-Auflistung – Eigenschaften, Methoden und Ereignisse)](../../../ado/reference/adox-api/views-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Sichten und Fields-Auflistungen (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Beispiele für die Append-Methode (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views-Auflistung, CommandText-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Sichten Delete-Methode (Beispiel) (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Ansichten Aktualisierungs Methode (Beispiel) (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Catalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)
