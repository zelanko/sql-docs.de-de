---
description: Create-Methode (ADOX)
title: Create-Methode (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 588f73fcd2ced95be3cd7f8586faed864b38f8ad
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984841"
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
 Die **Create** -Methode erstellt eine neue ADO- [Verbindung](../ado-api/connection-object-ado.md) mit der in *ConnectString*angegebenen Datenquelle und öffnet diese. Bei erfolgreicher Ausführung wird das neue **Verbindungs** Objekt der [ActiveConnection](./activeconnection-property-adox.md) -Eigenschaft zugewiesen.  
  
 Wenn der Anbieter das Erstellen neuer Kataloge nicht unterstützt, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Catalog-Objekt (ADOX)](./catalog-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create Method-Beispiel (VB)](./create-method-example-vb.md)   
 [ActiveConnection-Eigenschaft (ADOX)](./activeconnection-property-adox.md)