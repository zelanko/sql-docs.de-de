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
manager: craigg
ms.openlocfilehash: 96268fac4b81230fcb63db6b48ef4ef794abb9c7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788708"
---
# <a name="changepassword-method-adox"></a>ChangePassword-Methode (ADOX)
Ändert das Kennwort für ein [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) Konto.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>Parameter  
 *OldPassword*  
 Ein **Zeichenfolge** Wert, der das Kennwort des Benutzers vorhandene angibt. Wenn der Benutzer derzeit nicht über ein Kennwort verfügt, verwenden Sie eine leere Zeichenfolge ("") für *OldPassword*.  
  
 *NewPassword*  
 Ein **Zeichenfolge** -Wert, der das neue Kennwort angibt.  
  
## <a name="remarks"></a>Hinweise  
 Aus Sicherheitsgründen muss das alte Kennwort neben dem neuen Kennwort angegeben werden.  
  
 Wenn der Anbieter die Verwaltung des Vertrauensnehmers Eigenschaften nicht unterstützt wird, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Groups and Users Append, ChangePassword Methods Example (VB) (Gruppen und Benutzer – Append-, ChangePassword-Methode – Beispiele (VB))](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
