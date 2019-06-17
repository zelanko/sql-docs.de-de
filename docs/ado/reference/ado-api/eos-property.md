---
title: EOS-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 10b7ee78cb9903ccf0794a197a0679c226141641
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698257"
---
# <a name="eos-property"></a>EOS-Eigenschaft
Gibt an, ob die aktuelle Position am Ende der [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **booleschen** Wert, der angibt, ob die aktuelle Position am Ende des Streams ist. **EOS** gibt **"true"** stehen keine weiteren Bytes im Datenstrom; gibt **"false"** treten mehr Bytes, die nach der aktuellen Position.  
  
 Um das Ende des Streamposition festzulegen, verwenden die [SetEOS](../../../ado/reference/ado-api/seteos-method.md) Methode. Verwenden Sie zum Bestimmen der aktuellen Position der [Position](../../../ado/reference/ado-api/position-property-ado.md) Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [EOS- und LineSeparator-Eigenschaft und SkipLine-Methode – Beispiel (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
