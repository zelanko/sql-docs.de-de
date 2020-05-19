---
title: Indexes-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table::Indexes
- Indexes
helpviewer_keywords:
- Indexes collection [ADOX]
ms.assetid: 184cf536-455c-42be-bf1c-a5c25bade961
author: rothja
ms.author: jroth
ms.openlocfilehash: af209229519470b121e3c69ba857b145c0874e73
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763851"
---
# <a name="indexes-collection-adox"></a>Indexes-Collection (ADOX)
Enthält alle [Index](../../../ado/reference/adox-api/index-object-adox.md) Objekte einer Tabelle.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-indexes.md) -Methode für eine **Index** Sammlung ist für ADOX eindeutig. Ihre Möglichkeiten:  
  
-   Fügen Sie der Auflistung mithilfe der **Append** -Methode einen neuen Index hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Ihre Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../../../ado/reference/ado-api/item-property-ado.md) -Eigenschaft auf einen Index in der-Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Indizes mit der [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernen Sie einen Index aus der Sammlung mit der [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das aktuelle Datenbankschema mit der [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode widerzuspiegeln.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Indizes Auflistungseigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Index Append-Methode (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Index-Objekt (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)
