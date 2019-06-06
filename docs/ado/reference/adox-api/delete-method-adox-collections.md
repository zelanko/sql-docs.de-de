---
title: Delete-Methode (ADOX Sammlungen) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::Delete
- Groups::Delete
- Indexes::raw_Delete
- Columns::raw_Delete
- Tables::Delete
- Keys::Delete
- Users::Delete
- Users::raw_Delete
- Keys::raw_Delete
- Procedures::raw_Delete
- Views::raw_Delete
- Indexes::Delete
- Procedures::Delete
- Groups::raw_Delete
- Tables::raw_Delete
- Columns::Delete
helpviewer_keywords:
- delete method [ADOX]
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 185c5cad38b19ca3f2aea83ec3a5216e83182fda
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66697115"
---
# <a name="delete-method-adox-collections"></a>Delete-Methode (ADOX-Collections)
Entfernt ein Objekt aus einer Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Ein **Variant** , der den Namen oder die Position (Index) des zu löschenden Objekts angibt.  
  
## <a name="remarks"></a>Hinweise  
 Es wird ein Fehler auftreten, wenn die *Namen* in der Auflistung nicht vorhanden.  
  
 Für [Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md) und [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) Auflistungen, wenn der Anbieter das Löschen von Tabellen oder Benutzern bzw. nicht unterstützt, wird ein Fehler auftreten. Für [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) und [Ansichten](../../../ado/reference/adox-api/views-collection-adox.md) Sammlungen **löschen** schlägt fehl, wenn der Anbieter keine persistenten Befehle unterstützt.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Auflistung von Indizes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys Collection (ADOX) (Keys-Auflistung (ADOX))](../../../ado/reference/adox-api/keys-collection-adox.md)|[Procedures Collection (ADOX) (Procedures-Auflistung (ADOX))](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>Siehe auch  
 [Prozeduren Delete-Methode – Beispiel (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Views Delete-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
