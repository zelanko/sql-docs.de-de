---
title: Anzeigen von Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d87b56716ed1876acc6ac139e7804036d5cdfb86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718810"
---
# <a name="view-object-adox"></a>View-Objekt (ADOX)
Stellt einen gefilterten Satz von Datensätzen oder eine virtuelle Tabelle dar. Bei der Verwendung in Verbindung mit dem ADO [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, das **Ansicht** Objekt kann zum Hinzufügen, löschen oder Ändern von Sichten verwendet werden.  
  
## <a name="remarks"></a>Hinweise  
 Eine Sicht ist eine virtuelle Tabelle, die aus anderen Datenbanktabellen oder-Ansichten erstellt wurde. Die **Ansicht** Objekt können Sie eine Ansicht erstellen, ohne zu wissen, oder verwenden Sie "CREATE VIEW"-Syntax des Anbieters.  
  
 Mit den Eigenschaften einer **Ansicht** Objekt ist, können Sie:  
  
-   Wählen Sie die Ansicht mit den [Namen](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Geben Sie den ADO **Befehl** -Objekt, das verwendet werden kann, hinzufügen, löschen oder Ändern von Sichten mit der [Befehl](../../../ado/reference/adox-api/command-property-adox.md) Eigenschaft.  
  
-   Zurückgeben von Datumsinformationen der [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) und [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) Eigenschaften.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [View-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ansichten und Felder Auflistungen – Beispiel (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Ansichten Append-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views Collection, CommandText-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Views Delete-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
