---
title: NamedParameters-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c63fb598630a30fd2616722146bb6737f17b82b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242404"
---
# <a name="namedparameters-property-ado"></a>NamedParameters-Eigenschaft (ADO)
Gibt an, ob Parameternamen an den Anbieter übergeben werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Eigenschaft auf "true" festgelegt ist, wird ADO übergibt den Wert von der **Namen** Eigenschaft der einzelnen Parameter in der **Parameter** Sammlung für die [Command-Objekt](../../../ado/reference/ado-api/command-object-ado.md). Der Anbieter verwendet einen Parameternamen ein Parameter entsprechend der **CommandText** oder **' CommandStream '** Eigenschaften. Wenn diese Eigenschaft auf "false" festgelegt ist (Standardeinstellung), Parameternamen werden ignoriert und der Anbieter verwendet die Reihenfolge der Parameter entsprechend der Werte für Parameter in der **CommandText** oder **' CommandStream '** Eigenschaften.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandStream-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Parameters-Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
