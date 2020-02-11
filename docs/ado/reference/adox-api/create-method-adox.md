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
ms.openlocfilehash: aafcab3ad379dc25a2681a5d4f0d3f5e8d6eab5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966672"
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
 [Catalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create Method-Beispiel (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection-Eigenschaft (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
