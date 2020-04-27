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
ms.openlocfilehash: cbec9733044127d23e75364697a41ccd7e8910e4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67911521"
---
# <a name="children-property-ado-md"></a>Children-Eigenschaft (ADO MD)
Gibt eine [Members](../../../ado/reference/ado-md-api/members-collection-ado-md.md) -Auflistung zurück, für die [das aktuelle Element](../../../ado/reference/ado-md-api/member-object-ado-md.md) das übergeordnete Element in der Hierarchie ist.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Members** -Auflistung zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Children** -Eigenschaft enthält eine **Members** -Auflistung, für die **das aktuelle Element** das hierarchische übergeordnete Element ist. Element Objekte **auf** Blatt Ebene verfügen über keine untergeordneten Elemente in der **Members** -Auflistung. Diese Eigenschaft wird nur für **Member** -Objekte unterstützt, die zu einem [Ebenenobjekt](../../../ado/reference/ado-md-api/level-object-ado-md.md) gehören. Ein Fehler tritt auf, **Wenn von Element** Objekten, die zu einem [Positions](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt gehören, auf diese Eigenschaft verwiesen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ChildCount-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
