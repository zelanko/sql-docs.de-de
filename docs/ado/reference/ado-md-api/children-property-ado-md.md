---
description: Children-Eigenschaft (ADO MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 144e230b10ac6a73f88be7ab85e779bcda5f2cd0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441182"
---
# <a name="children-property-ado-md"></a>Children-Eigenschaft (ADO MD)
Gibt eine [Members](../../../ado/reference/ado-md-api/members-collection-ado-md.md) -Auflistung zurück, für die [das aktuelle Element](../../../ado/reference/ado-md-api/member-object-ado-md.md) das übergeordnete Element in der Hierarchie ist.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Members** -Auflistung zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Children** -Eigenschaft enthält eine **Members** -Auflistung, für die **das aktuelle Element** das hierarchische übergeordnete Element ist. Element Objekte **auf** Blatt Ebene verfügen über keine untergeordneten Elemente in der **Members** -Auflistung. Diese Eigenschaft wird nur für **Member** -Objekte unterstützt, die zu einem [Ebenenobjekt](../../../ado/reference/ado-md-api/level-object-ado-md.md) gehören. Ein Fehler tritt auf, **Wenn von Element** Objekten, die zu einem [Positions](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt gehören, auf diese Eigenschaft verwiesen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ChildCount-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
