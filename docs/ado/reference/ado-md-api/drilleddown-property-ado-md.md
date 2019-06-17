---
title: DrilledDown-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 83db7cfc6cac6dde34ca8d2a974c9d926ba9f086
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66709445"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown-Eigenschaft (ADO MD)
Gibt an, ob die untergeordneten Elemente unmittelbar folgen der [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) auf der Achse.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **booleschen** Wert und ist schreibgeschützt. **DrilledDown** gibt **"true"** , wenn keine untergeordneten Elemente des aktuellen Elements auf der Achse vorhanden sind. **DrilledDown** gibt **"false"** verfügt das aktuelle Element einen oder mehrere untergeordnete Elemente auf der Achse.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **DrilledDown** Eigenschaft, um zu bestimmen, ob mindestens ein untergeordnetes Element dieses Elements auf der Achse, die direkt nach diesem Element vorhanden ist. Diese Informationen sind hilfreich, wenn das Element angezeigt.  
  
 Diese Eigenschaft wird nur unterstützt, auf [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekte für eine [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt. Ein Fehler auftritt, wenn diese Eigenschaft, von verwiesen wird **Member** Objekte für eine [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ParentSameAsPrev-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
