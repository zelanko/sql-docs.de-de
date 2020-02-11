---
title: State-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c11bb74b62d54b1e2489cba5dd7cd35ee376a41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949159"
---
# <a name="state-property-ado-md"></a>State-Eigenschaft (ADO MD)
Gibt den aktuellen Status des Cellsets an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Long** Integer-Wert zurück, der die aktuelle Bedingung des [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekts angibt und schreibgeschützt ist. Die folgenden Werte sind gültig: **adstateclosed** (0) und **adstateopen** (1).  
  
## <a name="remarks"></a>Bemerkungen  
 Um die Konstanten Namen von [objectstateenum](../../../ado/reference/ado-api/objectstateenum.md) verwenden zu können, muss auf die ADO-Typbibliothek in Ihrem Projekt verwiesen werden. Weitere Informationen finden [Sie unter Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) .  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Close-Methode (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Open-Methode (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
