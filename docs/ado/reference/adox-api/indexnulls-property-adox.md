---
description: IndexNulls-Eigenschaft (ADOX)
title: IndexNulls-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Index::get_IndexNulls
- _Index::GetIndexNulls
- _Index::put_IndexNulls
- _Index::PutIndexNulls
- _Index::IndexNulls
helpviewer_keywords:
- IndexNulls property [ADOX]
ms.assetid: 313b0bf7-3f37-4823-8fca-bd9c80e078a7
author: rothja
ms.author: jroth
ms.openlocfilehash: 055b873866758c4aede2a3f6364eb99036159427
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984151"
---
# <a name="indexnulls-property-adox"></a>IndexNulls-Eigenschaft (ADOX)
Gibt an, ob Datensätze mit NULL-Werten in ihren Indexfeldern Indexeinträge aufweisen.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [AllowNullsEnum](./allownullsenum.md) -Wert fest und gibt ihn zurück. Der Standardwert ist **adIndexNullsDisallow**.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft ist für [Index](./index-object-adox.md) Objekte, die bereits an eine Auflistung angehängt wurden, schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
 [Index-Objekt (ADOX)](./index-object-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [IndexNulls-Eigenschaft – Beispiel (VB)](./indexnulls-property-example-vb.md)