---
title: DateModified-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
author: rothja
ms.author: jroth
ms.openlocfilehash: ccd916a8b9e9c500d3b718371b01831cc0ef292f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759206"
---
# <a name="datemodified-property-adox"></a>DateModified-Eigenschaft (ADOX)
Gibt das Datum an, an dem das Objekt zuletzt geändert wurde.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Variant** -Wert zurück, der das geänderte Datum angibt. Der Wert ist NULL, wenn **DateModified** vom Anbieter nicht unterstützt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **DateModified** -Eigenschaft ist für neu angefügte Objekte NULL. Nachdem Sie eine neue [Sicht](../../../ado/reference/adox-api/view-object-adox.md) oder [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md)angehängt haben, müssen Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode der [Sichten](../../../ado/reference/adox-api/views-collection-adox.md) oder der [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung aufrufen, um Werte für die **DateModified** -Eigenschaft zu erhalten.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [DateCreated und DateModified-Eigenschaften (Beispiel) (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
