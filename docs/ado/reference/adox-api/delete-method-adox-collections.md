---
title: Delete-Methode (ADOX-Auflistungen) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c3e398a48875f365dbe2fdc0b6540302d70f1da9
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763901"
---
# <a name="delete-method-adox-collections"></a>Delete-Methode (ADOX-Collections)
Entfernt ein-Objekt aus einer Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Parameter  
 *Name*  
 Eine **Variante** , die den Namen oder die Ordinalposition (Index) des zu löschenden Objekts angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der *Name* in der Auflistung nicht vorhanden ist, tritt ein Fehler auf.  
  
 Bei [Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md) -und [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) Sammlungen tritt ein Fehler auf, wenn der Anbieter das Löschen von Tabellen oder Benutzern nicht unterstützt. Für [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) und Ansichts [Auflistungen](../../../ado/reference/adox-api/views-collection-adox.md) schlägt **Delete** fehl, wenn der Anbieter das Beibehalten von Befehlen nicht unterstützt.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Auflistung von Indizes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys Collection (ADOX) (Keys-Auflistung (ADOX))](../../../ado/reference/adox-api/keys-collection-adox.md)|[Procedures Collection (ADOX) (Procedures-Auflistung (ADOX))](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prozeduren Delete-Methode (Beispiel) (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Views Delete-Methode – Beispiel (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
