---
description: Append-Methode (ADOX-Benutzer)
title: Append-Methode (ADOX-Benutzer) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 14b0c573b3ccf8a03b1c2f6513cdac67303fb4bf
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985431"
---
# <a name="append-method-adox-users"></a>Append-Methode (ADOX-Benutzer)
Fügt der [Benutzer](./users-collection-adox.md) Auflistung ein neues [Benutzer](./user-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Benutzer*  
 Ein **Variant** -Wert, der das anzufügende **Benutzer** Objekt oder den Namen des Benutzers enthält, der erstellt und angefügt werden soll.  
  
 *Kennwort*  
 Optional. Ein **Zeichen** folgen Wert, der das Kennwort für den Benutzer enthält. Der *Password* -Parameter entspricht dem Wert, der von der [ChangePassword](./changepassword-method-adox.md) -Methode eines **User** -Objekts angegeben wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Benutzer** Sammlung eines [Katalogs](./catalog-object-adox.md) stellt alle Benutzer des Katalogs dar. Die **Benutzer** Sammlung für eine [Gruppe](./group-object-adox.md) stellt nur die Benutzer dar, die über eine Mitgliedschaft in einer bestimmten Gruppe verfügen.  
  
 Wenn der Anbieter das Erstellen von Benutzern nicht unterstützt, tritt ein Fehler auf.  
  
> [!NOTE]
>  Bevor ein Benutzerobjekt an die **Users** -Auflistung eines **Group** -Objekts angefügt wird, muss ein **Benutzer** Objekt mit demselben [Namen](./name-property-adox.md) wie das angefügte **-Objekt in** der **Benutzer** Auflistung des **Katalogs**bereits vorhanden sein.  
  
## <a name="applies-to"></a>Gilt für  
 [Users-Collection (ADOX)](./users-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anfügen von Gruppen und Benutzern, ChangePassword-Methoden (Beispiel) (VB)](./groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](./append-method-adox-columns.md)   
 [Append-Methode (ADOX-Gruppen)](./append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](./append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](./append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](./append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](./append-method-adox-tables.md)   
 [Append-Methode (ADOX-Sichten)](./append-method-adox-views.md)