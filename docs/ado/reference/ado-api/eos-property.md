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
ms.openlocfilehash: 5a19856c957ee0c003e934ff8b2632aa28e32d33
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918925"
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
