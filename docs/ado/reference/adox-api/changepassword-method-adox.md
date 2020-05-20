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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b5ebf8304e4826d04d971e91606f8e9b0f4ead9
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759426"
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
 [Groups and Users Append, ChangePassword Methods Example (VB) (Gruppen und Benutzer – Append-, ChangePassword-Methode – Beispiele (VB))](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
