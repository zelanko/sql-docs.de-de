---
description: ChildCount-Eigenschaft (ADO MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 713958259b274e779802828d1940cabf25c5c222
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441202"
---
# <a name="childcount-property-ado-md"></a>ChildCount-Eigenschaft (ADO MD)
Gibt die Anzahl der Elemente an, für die [das aktuelle Element](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekt das übergeordnete Element in einer Hierarchie ist.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **lange** ganze Zahl zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **childCount** -Eigenschaft, um eine Schätzung der Anzahl der untergeordneten **Elemente eines Members** zurückzugeben. Die untergeordneten **Elemente eines Members können von** der [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) -Eigenschaft zurückgegeben werden.  
  
 Bei **Element Objekten aus** einem [Positions](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt beträgt die maximale Anzahl, die zurückgegeben wird, 65536. Wenn die tatsächliche Anzahl der untergeordneten Elemente 65536 überschreitet, ist der zurückgegebene Wert weiterhin 65536. Daher sollte die Anwendung eine **childCount** von 65536 als gleich oder größer als 65536 untergeordnete Elemente interpretieren.  
  
 Verwenden **Sie für Element** Objekte aus einem [Ebenenobjekt](../../../ado/reference/ado-md-api/level-object-ado-md.md) die Eigenschaft ADO-Sammlungs [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) für die Auflistung **Children** , um die genaue Anzahl der untergeordneten Elemente zu ermitteln. Die genaue Anzahl von untergeordneten Elementen kann langsam sein, wenn die Anzahl der untergeordneten Elemente in der Auflistung groß ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Children-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count-Eigenschaft (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Members-Collection (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
