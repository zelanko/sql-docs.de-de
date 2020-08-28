---
description: Parent-Eigenschaft (ADO MD)
title: Parent-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 93d7d550c4d70f207c3ab0fdeea0fa4ab0812c79
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986211"
---
# <a name="parent-property-ado-md"></a>Parent-Eigenschaft (ADO MD)
Gibt das [Element an, das dem aktuellen Element](./member-object-ado-md.md) in einer Hierarchie übergeordnet ist.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt ein [Element](./member-object-ado-md.md) Objekt zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Member, der sich auf der obersten Ebene einer Hierarchie (dem Stamm) befindet, hat kein übergeordnetes Element. Diese Eigenschaft wird nur für **Member** -Objekte unterstützt, die zu einem [Ebenenobjekt](./level-object-ado-md.md) gehören. Ein Fehler tritt auf, **Wenn von Element** Objekten, die zu einem [Positions](./position-object-ado-md.md) Objekt gehören, auf diese Eigenschaft verwiesen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Children-Eigenschaft (ADO MD)](./children-property-ado-md.md)