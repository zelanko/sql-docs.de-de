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
manager: craigg
ms.openlocfilehash: f489a87573dabbd091f5d2dce8a084b53cc5771e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62653536"
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
