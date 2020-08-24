---
description: DateCreated-Eigenschaft (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ae2c0fcfdc164906f0216abb45f98f705de9cd4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770739"
---
# <a name="datecreated-property-adox"></a>DateCreated-Eigenschaft (ADOX)
Gibt das Datum an, an dem das Objekt erstellt wurde.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Variant** -Wert zurück, der das erstellte Datum angibt. Der Wert ist NULL, wenn **DateCreated** vom Anbieter nicht unterstützt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **DateCreated** -Eigenschaft ist für neu angefügte Objekte NULL. Nachdem Sie eine neue [Sicht](./view-object-adox.md) oder [Prozedur](./procedure-object-adox.md)angehängt haben, müssen Sie die [Refresh](../ado-api/refresh-method-ado.md) -Methode der [Sichten](./views-collection-adox.md) oder der [Prozeduren](./procedures-collection-adox.md) Auflistung aufrufen, um Werte für die **DateCreated** -Eigenschaft zu erhalten.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Procedure-Objekt (ADOX)](./procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table-Objekt (ADOX)](./table-object-adox.md)  
    :::column-end:::
    :::column:::
        [View-Objekt (ADOX)](./view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [DateCreated und DateModified-Eigenschaften (Beispiel) (VB)](./datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified-Eigenschaft (ADOX)](./datemodified-property-adox.md)