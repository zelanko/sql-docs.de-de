---
title: Group-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b4b3de5f445ddd09bf7d069b0b93d82c6f8de978
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966211"
---
# <a name="group-object-adox"></a>Group-Objekt (ADOX)
Stellt ein Gruppenkonto, das über Zugriffsberechtigungen in einer gesicherten Datenbank verfügt.  
  
## <a name="remarks"></a>Hinweise  
 Die [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md) Auflistung von einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md) Gruppenkonten alle des Katalogs darstellt. Die **Gruppen** Sammlung für einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) stellt nur die Gruppe, zu denen der Benutzer gehört.  
  
 Mit den Eigenschaften, die Auflistungen und die Methoden einer **Gruppe** Objekt ist, können Sie:  
  
-   Identifizieren Sie die Gruppe mit der [Namen](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Bestimmen, ob eine Gruppe gelesen hat, schreiben oder Löschen von Berechtigungen mit den [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) und [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) Methoden.  
  
-   Zugreifen auf die Benutzerkonten, die Mitgliedschaften in der Gruppe mit der [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) Auflistung.  
  
-   Zugriff auf die anbieterspezifischen Eigenschaften mit den [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Group-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
