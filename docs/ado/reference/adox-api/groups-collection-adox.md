---
title: Groups-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6b8aea077af67c882830220da9ce24b802e25e5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63288301"
---
# <a name="groups-collection-adox"></a>Groups-Collection (ADOX)
Enthält alle gespeicherten [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) Objekte eines Katalogs oder Benutzer.  
  
## <a name="remarks"></a>Hinweise  
 Die **Gruppen** Auflistung von einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md) aller Gruppenkonten des Katalogs darstellt. Die **Gruppen** Sammlung für einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) stellt nur die Gruppe, zu denen der Benutzer gehört.  
  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) -Methode für eine **Gruppen** Auflistung für ADOX eindeutig ist. Folgende Aktionen sind möglich:  
  
-   Fügen Sie eine neue Sicherheitsgruppe in der Auflistung der **Append** Methode.  
  
 Die übrigen Eigenschaften und Methoden sind standard in ADO-Collections. Folgende Aktionen sind möglich:  
  
-   Zugreifen auf eine Gruppe in der Auflistung mit den [Element](../../../ado/reference/ado-api/item-property-ado.md) Eigenschaft.  
  
-   Zurückgeben der Anzahl der Gruppen, die in der Auflistung mit den [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) Eigenschaft.  
  
-   Entfernen Sie eine Gruppe aus der Auflistung mit den [löschen](../../../ado/reference/adox-api/delete-method-adox-collections.md) Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung entsprechend der aktuellen Datenbankschema mit dem [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode.  
  
> [!NOTE]
>  Vor dem Anfügen einer **Gruppe** -Objekt die **Gruppen** Auflistung von einer **Benutzer** -Objekt, eine **Gruppe** Objekt mit demselben [ Namen](../../../ado/reference/adox-api/name-property-adox.md) wie diejenige, die angefügt werden im bereits vorhanden sind, muss die **Gruppen** Auflistung von der **Katalog**.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Groups Collection Properties, Methods, and Events (Groups-Auflistung – Eigenschaften, Methoden und Ereignisse)](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
