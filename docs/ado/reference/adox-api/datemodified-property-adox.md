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
ms.openlocfilehash: 1c3a2a8ba0890dd50621fac143aa102091abcc19
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942712"
---
# <a name="datemodified-property-adox"></a>DateModified-Eigenschaft (ADOX)
Gibt das Datum an, an dem das Objekt zuletzt geändert wurde.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Variant** -Wert zurück, der das geänderte Datum angibt. Der Wert ist NULL, wenn **DateModified** vom Anbieter nicht unterstützt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **DateModified** -Eigenschaft ist für neu angefügte Objekte NULL. Nachdem Sie eine neue [Sicht](../../../ado/reference/adox-api/view-object-adox.md) oder [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md)angehängt haben, müssen Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode der [Sichten](../../../ado/reference/adox-api/views-collection-adox.md) oder der [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung aufrufen, um Werte für die **DateModified** -Eigenschaft zu erhalten.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [DateCreated und DateModified-Eigenschaften (Beispiel) (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
