---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 171aaa250930d5563d8ce6ec3b08b5939710b881
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63206344"
---
# <a name="append-method-adox-groups"></a>Append-Methode (ADOX-Gruppen)
Fügt ein neues [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) -Objekt an die [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Parameter  
 *Gruppieren*  
 Die **Gruppe** anzufügende Objekt oder den Namen der Gruppe erstellen und anfügen.  
  
## <a name="remarks"></a>Hinweise  
 Die **Gruppen** Auflistung von einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md) aller Gruppenkonten des Katalogs darstellt. Die **Gruppen** Sammlung für einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) stellt nur die Gruppe, zu denen der Benutzer gehört.  
  
 Wenn der Anbieter das Erstellen von Gruppen nicht unterstützt wird, tritt ein Fehler auf.  
  
> [!NOTE]
>  Vor dem Anfügen einer **Gruppe** -Objekt die **Gruppen** Auflistung von einer **Benutzer** -Objekt, eine **Gruppe** Objekt mit demselben [ Namen](../../../ado/reference/adox-api/name-property-adox.md) wie diejenige, die angefügt werden im bereits vorhanden sind, muss die **Gruppen** Auflistung von der **Katalog**.  
  
## <a name="applies-to"></a>Gilt für  
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Gruppen und Benutzer Append, ChangePassword Methods Example (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
