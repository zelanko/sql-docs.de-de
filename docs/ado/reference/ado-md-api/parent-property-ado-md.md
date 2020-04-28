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
ms.openlocfilehash: 2f6d6e03dd3288a5b0ca71bb9e129e1a57abf7c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949322"
---
# <a name="parent-property-ado-md"></a>Parent-Eigenschaft (ADO MD)
Gibt das [Element an, das dem aktuellen Element](../../../ado/reference/ado-md-api/member-object-ado-md.md) in einer Hierarchie übergeordnet ist.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt ein [Element](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekt zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Member, der sich auf der obersten Ebene einer Hierarchie (dem Stamm) befindet, hat kein übergeordnetes Element. Diese Eigenschaft wird nur für **Member** -Objekte unterstützt, die zu einem [Ebenenobjekt](../../../ado/reference/ado-md-api/level-object-ado-md.md) gehören. Ein Fehler tritt auf, **Wenn von Element** Objekten, die zu einem [Positions](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt gehören, auf diese Eigenschaft verwiesen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Children-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
