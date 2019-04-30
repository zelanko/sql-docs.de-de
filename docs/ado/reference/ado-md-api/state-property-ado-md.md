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
manager: craigg
ms.openlocfilehash: 812863395c2980f341ed2419eee1d9d661f19dd0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308599"
---
# <a name="state-property-ado-md"></a>State-Eigenschaft (ADO MD)
Gibt den aktuellen Zustand des das Cellset an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **lange** ganze Zahl, der angibt, der des aktuellen Zustand der der [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekt und ist schreibgeschützt. Die folgenden Werte sind gültig: **AdStateClosed** (0) und **AdStateOpen** (1).  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) Konstantennamen, benötigen Sie die ADO-Typbibliothek, die in Ihrem Projekt referenziert. Finden Sie unter [mithilfe von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) für Weitere Informationen.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Close-Methode (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Open-Methode (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
