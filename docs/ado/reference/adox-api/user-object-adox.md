---
description: User-Objekt (ADOX)
title: User-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3576c64d620956b69dbd33113a3d114ff55b4a79
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769100"
---
# <a name="user-object-adox"></a>User-Objekt (ADOX)
Stellt ein Benutzerkonto dar, das über Zugriffsberechtigungen in einer gesicherten Datenbank verfügt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Benutzer](./users-collection-adox.md) Sammlung eines [Katalogs](./catalog-object-adox.md) stellt alle Benutzer des Katalogs dar. Die **Benutzer** Sammlung für eine [Gruppe](./group-object-adox.md) stellt nur die Benutzer der jeweiligen Gruppe dar.  
  
 Mit den Eigenschaften, Auflistungen und Methoden eines **Benutzer** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie den Benutzer mit der [Name](./name-property-adox.md) -Eigenschaft.  
  
-   Ändern Sie das Kennwort für einen Benutzer mit der [ChangePassword](./changepassword-method-adox.md) -Methode.  
  
-   Bestimmen Sie, ob ein Benutzer über Lese-, Schreib-oder Lösch Berechtigungen für die [getberechtigungs](./getpermissions-method-adox.md) -und [setberechtigungs](./setpermissions-method-adox.md) -Methoden verfügt.  
  
-   Greifen Sie auf die Gruppen zu, zu denen ein Benutzer gehört, zu der [Gruppen](./groups-collection-adox.md) Auflistung.  
  
-   Greifen Sie mit der [Properties](../ado-api/properties-collection-ado.md) -Auflistung auf anbieterspezifische Eigenschaften zu.  
  
-   Bestimmen Sie den [parametricatalog](./parentcatalog-property-adox.md) für einen Benutzer.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [User-Objekt – Eigenschaften, Methoden und Ereignisse](./user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [Groups-Auflistung (ADOX)](./groups-collection-adox.md)   
 [Users-Collection (ADOX)](./users-collection-adox.md)