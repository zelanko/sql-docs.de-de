---
description: Procedure-Objekt (ADOX)
title: Procedure-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b41e83033ab86810c4e26ff3c15fa4d9d1ea97ae
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983631"
---
# <a name="procedure-object-adox"></a>Procedure-Objekt (ADOX)
Stellt eine gespeicherte Prozedur dar. Bei Verwendung in Verbindung mit dem ADO- [Befehls](../ado-api/command-object-ado.md) Objekt kann das **Prozedur** Objekt zum Hinzufügen, löschen oder Ändern gespeicherter Prozeduren verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Das **Prozedur** Objekt ermöglicht es Ihnen, eine gespeicherte Prozedur zu erstellen, ohne die "CREATE PROCEDURE"-Syntax des Anbieters kennen oder verwenden zu müssen.  
  
 Mit den Eigenschaften eines **Prozedur** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie die Prozedur mit der [Name](./name-property-adox.md) -Eigenschaft.  
  
-   Geben Sie das ADO- **Befehls** Objekt an, das verwendet werden kann, um die Prozedur mit der [Command](./command-property-adox.md) -Eigenschaft zu erstellen oder auszuführen.  
  
-   Gibt Datumsinformationen mit den Eigenschaften [DateCreated](./datecreated-property-adox.md) und [DateModified](./datemodified-property-adox.md) zurück.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Procedure-Objekt – Eigenschaften, Methoden und Ereignisse](./procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Befehls-und CommandText-Eigenschaften (VB)](./command-and-commandtext-properties-example-vb.md)   
 [Parameter Auflistung, Beispiel für Befehls Eigenschaft (VB)](./parameters-collection-command-property-example-vb.md)   
 [Prozeduren Append-Methode Beispiel (VB)](./procedures-append-method-example-vb.md)   
 [Prozeduren Delete-Methode (Beispiel) (VB)](./procedures-delete-method-example-vb.md)   
 [Procedures-Collection (ADOX)](./procedures-collection-adox.md)