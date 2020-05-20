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
author: rothja
ms.author: jroth
ms.openlocfilehash: b0cd75780abe01edc6f2e90258cc7d24f5eae016
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763321"
---
# <a name="group-object-adox"></a>Group-Objekt (ADOX)
Stellt ein Gruppenkonto dar, das über Zugriffsberechtigungen in einer gesicherten Datenbank verfügt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Groups](../../../ado/reference/adox-api/groups-collection-adox.md) -Sammlung eines [Katalogs](../../../ado/reference/adox-api/catalog-object-adox.md) stellt alle Gruppenkonten des Katalogs dar. Die **Groups** -Sammlung für einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) stellt nur die Gruppe dar, zu der der Benutzer gehört.  
  
 Mit den Eigenschaften, Auflistungen und Methoden eines **Group** -Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie die Gruppe mit der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft.  
  
-   Stellen Sie fest, ob eine Gruppe über Lese-, Schreib-oder Lösch Berechtigungen mit den Methoden [getberechtigungen](../../../ado/reference/adox-api/getpermissions-method-adox.md) und [setberechtigungs](../../../ado/reference/adox-api/setpermissions-method-adox.md) Berechtigungen verfügt.  
  
-   Greifen Sie auf die Benutzerkonten zu, die über Mitgliedschaften in der Gruppe mit der [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) Sammlung verfügen.  
  
-   Greifen Sie mit der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung auf anbieterspezifische Eigenschaften zu.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Group-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
