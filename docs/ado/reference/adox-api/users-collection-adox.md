---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a6146a942e572e28692ceaafd77d6958cdab9dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964953"
---
# <a name="users-collection-adox"></a>Users-Collection (ADOX)
Enthält alle gespeicherten [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) Objekte eines [Katalogs](../../../ado/reference/adox-api/catalog-object-adox.md) oder einer [Gruppe](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Benutzer** Sammlung eines [Katalogs](../../../ado/reference/adox-api/catalog-object-adox.md) stellt alle Benutzer des Katalogs dar. Die **Benutzer** Sammlung für eine [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) stellt nur die Benutzer dar, die über eine Mitgliedschaft in einer bestimmten Gruppe verfügen.  
  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-users.md) -Methode für eine **Benutzer** Sammlung ist für ADOX eindeutig. Ihre Möglichkeiten:  
  
-   Fügen Sie der Sammlung mithilfe der **Append** -Methode einen neuen Benutzer hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Ihre Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../../../ado/reference/ado-api/item-property-ado.md) -Eigenschaft auf einen Benutzer in der Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Benutzer mit der [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernen Sie einen Benutzer aus der Sammlung mit der [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das Schema der aktuellen Datenbank mit [der Aktualisierungs Methode](../../../ado/reference/ado-api/refresh-method-ado.md) widerzuspiegeln.  
  
> [!NOTE]
>  Bevor ein Benutzerobjekt an die **Users** -Auflistung eines **Group** -Objekts angefügt wird, muss ein **Benutzer** Objekt mit demselben [Namen](../../../ado/reference/adox-api/name-property-adox.md) wie das angefügte **-Objekt in** der **Benutzer** Auflistung des **Katalogs**bereits vorhanden sein.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Users-Collection – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Catalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
