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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ca88f95882da8e900e7695f81570b46977db9c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789658"
---
# <a name="create-method-adox"></a>Create-Methode (ADOX)
Erstellt einen neuen Katalog an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectString*  
 Ein **Zeichenfolge** Wert, der für die Verbindung mit der Datenquelle verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Die **erstellen** Methode erstellt und öffnet ein neues ADO- [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) an die Datenquelle, die im angegebenen *ConnectString*. Bei erfolgreicher Ausführung der neuen **Verbindung** Objekt zugewiesen ist die [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) Eigenschaft.  
  
 Wenn der Anbieter das Erstellen neuer Kataloge nicht unterstützt wird, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie die Methode – Beispiel (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection-Eigenschaft (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
