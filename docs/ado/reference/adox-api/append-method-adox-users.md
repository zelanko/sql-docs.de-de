---
description: Append-Methode (ADOX-Benutzer)
title: Append-Methode (ADOX-Benutzer) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Users::raw_Append
- Users::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
author: rothja
ms.author: jroth
ms.openlocfilehash: e774ab590e3f405cab157293405eba5e575ecb52
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440462"
---
# <a name="append-method-adox-users"></a>Append-Methode (ADOX-Benutzer)
Fügt der [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) Auflistung ein neues [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Benutzer*  
 Ein **Variant** -Wert, der das anzufügende **Benutzer** Objekt oder den Namen des Benutzers enthält, der erstellt und angefügt werden soll.  
  
 *Kennwort*  
 Optional. Ein **Zeichen** folgen Wert, der das Kennwort für den Benutzer enthält. Der *Password* -Parameter entspricht dem Wert, der von der [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) -Methode eines **User** -Objekts angegeben wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Benutzer** Sammlung eines [Katalogs](../../../ado/reference/adox-api/catalog-object-adox.md) stellt alle Benutzer des Katalogs dar. Die **Benutzer** Sammlung für eine [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) stellt nur die Benutzer dar, die über eine Mitgliedschaft in einer bestimmten Gruppe verfügen.  
  
 Wenn der Anbieter das Erstellen von Benutzern nicht unterstützt, tritt ein Fehler auf.  
  
> [!NOTE]
>  Bevor ein Benutzerobjekt an die **Users** -Auflistung eines **Group** -Objekts angefügt wird, muss ein **Benutzer** Objekt mit demselben [Namen](../../../ado/reference/adox-api/name-property-adox.md) wie das angefügte **-Objekt in** der **Benutzer** Auflistung des **Katalogs**bereits vorhanden sein.  
  
## <a name="applies-to"></a>Gilt für  
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anfügen von Gruppen und Benutzern, ChangePassword-Methoden (Beispiel) (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
