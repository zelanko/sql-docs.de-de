---
description: State-Eigenschaft (ADO MD)
title: State-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 78b96e242cc27d27326d97f51cf378d9c5cbb51e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985981"
---
# <a name="state-property-ado-md"></a>State-Eigenschaft (ADO MD)
Gibt den aktuellen Status des Cellsets an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Long** Integer-Wert zurück, der die aktuelle Bedingung des [Cellset](./cellset-object-ado-md.md) -Objekts angibt und schreibgeschützt ist. Die folgenden Werte sind gültig: **adstateclosed** (0) und **adstateopen** (1).  
  
## <a name="remarks"></a>Bemerkungen  
 Um die Konstanten Namen von [objectstateenum](../ado-api/objectstateenum.md) verwenden zu können, muss auf die ADO-Typbibliothek in Ihrem Projekt verwiesen werden. Weitere Informationen finden [Sie unter Verwenden von ADO mit ADO MD](../../guide/multidimensional/using-ado-with-ado-md.md) .  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Close-Methode (ADO MD)](./close-method-ado-md.md)   
 [Open-Methode (ADO MD)](./open-method-ado-md.md)