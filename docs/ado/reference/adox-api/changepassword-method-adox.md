---
title: ChangePassword-Methode (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de8baf504a76407037322fd6b799f6d63584eae7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967039"
---
# <a name="changepassword-method-adox"></a>ChangePassword-Methode (ADOX)
Ändert das Kennwort für ein [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) Konto.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>Parameter  
 *OldPassword*  
 Ein **Zeichen** folgen Wert, der das vorhandene Kennwort des Benutzers angibt. Wenn der Benutzer zurzeit kein Kennwort hat, verwenden Sie eine leere Zeichenfolge ("") für *oldPassword*.  
  
 *NewPassword*  
 Ein **Zeichen** folgen Wert, der das neue Kennwort angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Aus Sicherheitsgründen muss das alte Kennwort zusätzlich zum neuen Kennwort angegeben werden.  
  
 Wenn der Anbieter die Verwaltung von Vertrauens nehmer-Eigenschaften nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Append- und ChangePassword-Methoden für Gruppen und Benutzer – Beispiel (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
