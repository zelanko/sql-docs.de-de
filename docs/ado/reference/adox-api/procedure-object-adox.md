---
title: Procedure-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1681001dd42026c1a1fce04814b094047a475a0f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965485"
---
# <a name="procedure-object-adox"></a>Procedure-Objekt (ADOX)
Stellt eine gespeicherte Prozedur dar. Bei Verwendung in Verbindung mit dem ADO- [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt kann das **Prozedur** Objekt zum Hinzufügen, löschen oder Ändern gespeicherter Prozeduren verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Das **Prozedur** Objekt ermöglicht es Ihnen, eine gespeicherte Prozedur zu erstellen, ohne die "CREATE PROCEDURE"-Syntax des Anbieters kennen oder verwenden zu müssen.  
  
 Mit den Eigenschaften eines **Prozedur** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie die Prozedur mit der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft.  
  
-   Geben Sie das ADO- **Befehls** Objekt an, das verwendet werden kann, um die Prozedur mit der [Command](../../../ado/reference/adox-api/command-property-adox.md) -Eigenschaft zu erstellen oder auszuführen.  
  
-   Gibt Datumsinformationen mit den Eigenschaften [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) und [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) zurück.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Procedure-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Befehls-und CommandText-Eigenschaften (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Parameter Auflistung, Beispiel für Befehls Eigenschaft (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Prozeduren Append-Methode Beispiel (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Prozeduren Delete-Methode (Beispiel) (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedures Collection (ADOX) (Procedures-Auflistung (ADOX))](../../../ado/reference/adox-api/procedures-collection-adox.md)
