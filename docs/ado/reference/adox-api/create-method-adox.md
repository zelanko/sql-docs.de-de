---
description: Create-Methode (ADOX)
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
ms.openlocfilehash: b291651caa93e93999d87a926c9abe391e71d21e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440212"
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
