---
description: User-Objekt (ADOX)
title: User-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 6e83bd40c226f1d5b5948c6475b259c799907866
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983050"
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