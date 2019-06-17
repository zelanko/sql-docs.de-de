---
title: ChildCount-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8d9a0d746d88423c699907e266a93a2b3a08e031
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66709565"
---
# <a name="childcount-property-ado-md"></a>ChildCount-Eigenschaft (ADO MD)
Gibt die Anzahl der Elemente für den aktuellen [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekt ist das übergeordnete Element in einer Hierarchie.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **lange** ganze Zahl und ist schreibgeschützt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **ChildCount** Eigenschaft, um eine Schätzung der wie viele untergeordnete Elemente zurückgeben einer **Member** hat. Die tatsächliche untergeordneten Elemente ein **Member** zurückgegeben werden kann, indem die [untergeordnete Elemente](../../../ado/reference/ado-md-api/children-property-ado-md.md) Eigenschaft.  
  
 Für **Member** Objekte aus einer [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt ist, wird die maximale Anzahl zurückgegeben wird, 65536. Wenn die tatsächliche Anzahl der untergeordneten Elemente 65536 überschreitet, wird der zurückgegebene Wert immer noch 65536 sein. Aus diesem Grund sollte die Anwendung interpretieren eine **ChildCount** von 65536 als oder gleich 65536 untergeordnete Elemente.  
  
 Für **Member** Objekte aus einer [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) Objekt, das die Auflistung von ADO verwenden, [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) Eigenschaft der **untergeordnete Elemente** Auflistung, um zu bestimmen, die genaue Anzahl der untergeordneten Elemente. Bestimmen die genaue Anzahl der untergeordneten Elemente ist möglicherweise langsam, wenn die Anzahl der untergeordneten Elemente in der Auflistung groß ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Children-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count-Eigenschaft (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Members-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
