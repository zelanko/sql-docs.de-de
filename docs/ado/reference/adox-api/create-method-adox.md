---
title: Create-Methode (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
author: rothja
ms.author: jroth
ms.openlocfilehash: 15ea5cf8b565a943f4905a890cb08ba0afed202f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759266"
---
# <a name="create-method-adox"></a>Create-Methode (ADOX)
Erstellt einen neuen Katalog.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectString*  
 Ein **Zeichen** folgen Wert, der für die Verbindung mit der Datenquelle verwendet wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Create** -Methode erstellt eine neue ADO- [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) mit der in *ConnectString*angegebenen Datenquelle und öffnet diese. Bei erfolgreicher Ausführung wird das neue **Verbindungs** Objekt der [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) -Eigenschaft zugewiesen.  
  
 Wenn der Anbieter das Erstellen neuer Kataloge nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create Method-Beispiel (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection-Eigenschaft (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
