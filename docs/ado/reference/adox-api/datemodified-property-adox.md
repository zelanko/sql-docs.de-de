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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02731da2b023b7230b3407e0eb386fe8e5aaaf87
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786308"
---
# <a name="datemodified-property-adox"></a>DateModified-Eigenschaft (ADOX)
Gibt das Datum, das Objekt zuletzt geändert wurde.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Variant** Wert, der angibt, das Änderungsdatum. Der Wert ist null Wenn **DateModified** wird vom Anbieter nicht unterstützt.  
  
## <a name="remarks"></a>Hinweise  
 Die **DateModified** -Eigenschaft ist null für die neu angefügte Objekte. Nach dem Anfügen eines neuen [Ansicht](../../../ado/reference/adox-api/view-object-adox.md) oder [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md), rufen Sie die [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode der der [Ansichten](../../../ado/reference/adox-api/views-collection-adox.md) oder [Prozeduren ](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung abzurufenden Werte für die **DateModified** Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [DateCreated und DateModified Eigenschaften – Beispiel (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
