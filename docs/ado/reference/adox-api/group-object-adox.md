---
description: Group-Objekt (ADOX)
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
ms.openlocfilehash: 0442ca3bd785269fed49dc86d982971a8feec4ea
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770419"
---
# <a name="group-object-adox"></a>Group-Objekt (ADOX)
Stellt ein Gruppenkonto dar, das über Zugriffsberechtigungen in einer gesicherten Datenbank verfügt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Groups](./groups-collection-adox.md) -Sammlung eines [Katalogs](./catalog-object-adox.md) stellt alle Gruppenkonten des Katalogs dar. Die **Groups** -Sammlung für einen [Benutzer](./user-object-adox.md) stellt nur die Gruppe dar, zu der der Benutzer gehört.  
  
 Mit den Eigenschaften, Auflistungen und Methoden eines **Group** -Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie die Gruppe mit der [Name](./name-property-adox.md) -Eigenschaft.  
  
-   Stellen Sie fest, ob eine Gruppe über Lese-, Schreib-oder Lösch Berechtigungen mit den Methoden [getberechtigungen](./getpermissions-method-adox.md) und [setberechtigungs](./setpermissions-method-adox.md) Berechtigungen verfügt.  
  
-   Greifen Sie auf die Benutzerkonten zu, die über Mitgliedschaften in der Gruppe mit der [Benutzer](./users-collection-adox.md) Sammlung verfügen.  
  
-   Greifen Sie mit der [Properties](../ado-api/properties-collection-ado.md) -Auflistung auf anbieterspezifische Eigenschaften zu.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Group-Objekt – Eigenschaften, Methoden und Ereignisse](./group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Groups-Auflistung (ADOX)](./groups-collection-adox.md)   
 [Users-Collection (ADOX)](./users-collection-adox.md)