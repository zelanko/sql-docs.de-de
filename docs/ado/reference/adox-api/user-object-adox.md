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
ms.openlocfilehash: 3c81caba440367712e5743bc1e224bd3968a2990
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439392"
---
# <a name="user-object-adox"></a>User-Objekt (ADOX)
Stellt ein Benutzerkonto dar, das über Zugriffsberechtigungen in einer gesicherten Datenbank verfügt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) Sammlung eines [Katalogs](../../../ado/reference/adox-api/catalog-object-adox.md) stellt alle Benutzer des Katalogs dar. Die **Benutzer** Sammlung für eine [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) stellt nur die Benutzer der jeweiligen Gruppe dar.  
  
 Mit den Eigenschaften, Auflistungen und Methoden eines **Benutzer** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie den Benutzer mit der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft.  
  
-   Ändern Sie das Kennwort für einen Benutzer mit der [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) -Methode.  
  
-   Bestimmen Sie, ob ein Benutzer über Lese-, Schreib-oder Lösch Berechtigungen für die [getberechtigungs](../../../ado/reference/adox-api/getpermissions-method-adox.md) -und [setberechtigungs](../../../ado/reference/adox-api/setpermissions-method-adox.md) -Methoden verfügt.  
  
-   Greifen Sie auf die Gruppen zu, zu denen ein Benutzer gehört, zu der [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md) Auflistung.  
  
-   Greifen Sie mit der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung auf anbieterspezifische Eigenschaften zu.  
  
-   Bestimmen Sie den [parametricatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) für einen Benutzer.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [User-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Getberechtigungs-und setberechtigungs-Methoden Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
