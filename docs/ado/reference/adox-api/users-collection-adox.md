---
description: Users-Collection (ADOX)
title: Users-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d452075b3659d3ad01ba28540217b8447950084
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769039"
---
# <a name="users-collection-adox"></a>Users-Collection (ADOX)
Enthält alle gespeicherten [Benutzer](./user-object-adox.md) Objekte eines [Katalogs](./catalog-object-adox.md) oder einer [Gruppe](./group-object-adox.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Benutzer** Sammlung eines [Katalogs](./catalog-object-adox.md) stellt alle Benutzer des Katalogs dar. Die **Benutzer** Sammlung für eine [Gruppe](./group-object-adox.md) stellt nur die Benutzer dar, die über eine Mitgliedschaft in einer bestimmten Gruppe verfügen.  
  
 Die [Append](./append-method-adox-users.md) -Methode für eine **Benutzer** Sammlung ist für ADOX eindeutig. Ihre Möglichkeiten:  
  
-   Fügen Sie der Sammlung mithilfe der **Append** -Methode einen neuen Benutzer hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Ihre Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../ado-api/item-property-ado.md) -Eigenschaft auf einen Benutzer in der Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Benutzer mit der [count](../ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernen Sie einen Benutzer aus der Sammlung mit der [Delete](./delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das Schema der aktuellen Datenbank mit [der Aktualisierungs Methode](../ado-api/refresh-method-ado.md) widerzuspiegeln.  
  
> [!NOTE]
>  Bevor ein Benutzerobjekt an die **Users** -Auflistung eines **Group** -Objekts angefügt wird, muss ein **Benutzer** Objekt mit demselben [Namen](./name-property-adox.md) wie das angefügte **-Objekt in** der **Benutzer** Auflistung des **Katalogs**bereits vorhanden sein.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Users-Collection – Eigenschaften, Methoden und Ereignisse](./users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [Catalog-Objekt (ADOX)](./catalog-object-adox.md)   
 [User-Objekt (ADOX)](./user-object-adox.md)