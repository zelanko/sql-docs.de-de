---
description: Append-Methode (ADOX-Gruppen)
title: Append-Methode (ADOX-Gruppen) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups::raw_Append
- Groups::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 56b94fc6-7ef0-4e4a-82a3-033b94c46036
author: rothja
ms.author: jroth
ms.openlocfilehash: 2dc46d1c0d44ec175b442df943ce72a38ec2b761
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440492"
---
# <a name="append-method-adox-groups"></a>Append-Methode (ADOX-Gruppen)
Fügt der [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md) Auflistung ein neues [Gruppen](../../../ado/reference/adox-api/group-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Parameter  
 *Gruppieren*  
 Das anzufügende **Gruppen** Objekt oder der Name der Gruppe, die erstellt und angefügt werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Groups** -Sammlung eines [Katalogs](../../../ado/reference/adox-api/catalog-object-adox.md) stellt alle Gruppenkonten des Katalogs dar. Die **Groups** -Sammlung für einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) stellt nur die Gruppe dar, zu der der Benutzer gehört.  
  
 Wenn der Anbieter das Erstellen von Gruppen nicht unterstützt, tritt ein Fehler auf.  
  
> [!NOTE]
>  Vor dem Anhängen eines **Group** -Objekts an die **Groups** -Auflistung eines **User** -Objekts muss bereits ein **Gruppen** Objekt mit demselben [Namen](../../../ado/reference/adox-api/name-property-adox.md) wie das angefügte-Objekt in der **Groups** -Auflistung des **Katalogs**vorhanden sein.  
  
## <a name="applies-to"></a>Gilt für  
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anfügen von Gruppen und Benutzern, ChangePassword-Methoden (Beispiel) (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
