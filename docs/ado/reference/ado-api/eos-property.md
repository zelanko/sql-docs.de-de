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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9199563f2a5d6ce594b88577cfb69766cf311492
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765531"
---
# <a name="eos-property"></a>EOS-Eigenschaft
Gibt an, ob sich die aktuelle Position am Ende des [Streams](../../../ado/reference/ado-api/stream-object-ado.md)befindet.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **booleschen** Wert zurück, der angibt, ob sich die aktuelle Position am Ende des Streams befindet. **EOS** gibt **true** zurück, wenn keine weiteren Bytes im Stream vorhanden sind. gibt **false** zurück, wenn nach der aktuellen Position mehr Bytes vorhanden sind.  
  
 Verwenden Sie die [SetEOS](../../../ado/reference/ado-api/seteos-method.md) -Methode, um das Ende der Streamposition festzulegen. Verwenden Sie zum Bestimmen der aktuellen Position die [Position](../../../ado/reference/ado-api/position-property-ado.md) -Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaften von EOS und lineseparser und SkipLine-Methode (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
