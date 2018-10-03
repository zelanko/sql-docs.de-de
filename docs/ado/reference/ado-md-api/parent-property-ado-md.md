---
title: Parent-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3cb0b93ba1be2570ecd474ed1244bec16575180d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724348"
---
# <a name="parent-property-ado-md"></a>Parent-Eigenschaft (ADO MD)
Gibt das Element, das das übergeordnete Element des aktuellen ist [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) in einer Hierarchie.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) -Objekt und ist schreibgeschützt.  
  
## <a name="remarks"></a>Hinweise  
 Ein Member, auf der obersten Ebene einer Hierarchie (Stamm) besitzt kein übergeordnetes Element. Diese Eigenschaft wird nur unter unterstützt **Member** Objekte für eine [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) Objekt. Ein Fehler auftritt, wenn diese Eigenschaft, von verwiesen wird **Member** Objekte für eine [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Children-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
