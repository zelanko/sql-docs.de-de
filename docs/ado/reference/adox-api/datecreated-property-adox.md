---
title: DateCreated-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0151b6388a19fc95227cbfa55a571e0a797d0acc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966570"
---
# <a name="datecreated-property-adox"></a>DateCreated-Eigenschaft (ADOX)
Gibt das Datum an, an dem das Objekt erstellt wurde.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Variant** -Wert zurück, der das erstellte Datum angibt. Der Wert ist NULL, wenn **DateCreated** vom Anbieter nicht unterstützt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **DateCreated** -Eigenschaft ist für neu angefügte Objekte NULL. Nachdem Sie eine neue [Sicht](../../../ado/reference/adox-api/view-object-adox.md) oder [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md)angehängt haben, müssen Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode der [Sichten](../../../ado/reference/adox-api/views-collection-adox.md) oder der [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung aufrufen, um Werte für die **DateCreated** -Eigenschaft zu erhalten.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [DateCreated und DateModified-Eigenschaften (Beispiel) (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
