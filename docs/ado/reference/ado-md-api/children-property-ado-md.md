---
title: Children-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Children
- Children
helpviewer_keywords:
- Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 219aeba8cfc7e913a2febdd031c844aed922832e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709664"
---
# <a name="children-property-ado-md"></a>Children-Eigenschaft (ADO MD)
Gibt eine [Mitglieder](../../../ado/reference/ado-md-api/members-collection-ado-md.md) Sammlung, für die aktuellen [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) ist das übergeordnete Element in der Hierarchie.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Mitglieder** Auflistung ist schreibgeschützt.  
  
## <a name="remarks"></a>Hinweise  
 Die **untergeordnete Elemente** Eigenschaft enthält eine **Mitglieder** Sammlung, für die aktuellen **Member** ist das hierarchische übergeordnete Element. Untergeordnete Ebene **Member** Objekte verfügen über keine untergeordneten Elemente der **Mitglieder** Auflistung. Diese Eigenschaft wird nur unterstützt, auf **Member** Objekte für eine [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) Objekt. Ein Fehler auftritt, wenn diese Eigenschaft, von verwiesen wird **Member** Objekte für eine [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ChildCount-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
