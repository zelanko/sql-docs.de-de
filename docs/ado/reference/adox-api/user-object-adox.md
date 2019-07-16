---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf454e28e7a823eb643b5bbd92b0396fac15a028
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67964979"
---
# <a name="user-object-adox"></a>User-Objekt (ADOX)
Stellt ein Benutzerkonto, das über Zugriffsberechtigungen in einer gesicherten Datenbank verfügt.  
  
## <a name="remarks"></a>Hinweise  
 Die [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) Auflistung von einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md) Benutzer alle des Katalogs darstellt. Die **Benutzer** Sammlung für einen [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) nur die Benutzer dieser Gruppe darstellt.  
  
 Mit den Eigenschaften, die Auflistungen und die Methoden einer **Benutzer** Objekt ist, können Sie:  
  
-   Identifizieren den Benutzer mit der [Namen](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Ändern Sie das Kennwort für einen Benutzer mit der [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) Methode.  
  
-   Bestimmen, ob ein Benutzer gelesen hat, schreiben oder Löschen von Berechtigungen mit den [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) und [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) Methoden.  
  
-   Zugriff auf die Gruppen, denen ein Benutzer angehört, mit, der [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md) Auflistung.  
  
-   Zugriff auf die anbieterspezifischen Eigenschaften mit den [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
-   Bestimmen der [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) für einen Benutzer.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [User-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetPermissions und SetPermissions-Methoden – Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
