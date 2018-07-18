---
title: EOS-Eigenschaft | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c029efee5c4a938ff28e5cfefb5172d6b6219eeb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277959"
---
# <a name="eos-property"></a>EOS-Eigenschaft
Gibt an, ob die aktuelle Position am Ende der [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **booleschen** -Wert, der angibt, ob die aktuelle Position am Ende des Streams ist. **EOS** gibt **"true"** es sind keine weitere Bytes im Datenstrom; gibt **"false"** treten mehr Bytes, die nach der aktuellen Position.  
  
 Um das Ende des Streamposition festzulegen, verwenden die [SetEOS](../../../ado/reference/ado-api/seteos-method.md) Methode. Verwenden Sie zum Bestimmen der aktuellen Position der [Position](../../../ado/reference/ado-api/position-property-ado.md) Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [EOS und Zeilentrennzeichen Eigenschaften und SkipLine-Methode (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
