---
description: DrilledDown-Eigenschaft (ADO MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 132b1a7210a9fd37866f1a150430f0d1a6d29606
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441042"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown-Eigenschaft (ADO MD)
Gibt an, ob untergeordnete Elemente unmittelbar auf den [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) auf der Achse folgen.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **booleschen** Wert zurück und ist schreibgeschützt. **DrilledDown** gibt **true** zurück, wenn keine untergeordneten Elemente des aktuellen Elements auf der Achse vorhanden sind. **DrilledDown** gibt **false** zurück, wenn das aktuelle Element über mindestens ein untergeordnetes Element auf der Achse verfügt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **DrilledDown** -Eigenschaft, um zu bestimmen, ob mindestens ein untergeordnetes Element dieses Elements auf der Achse unmittelbar nach diesem Member vorhanden ist. Diese Informationen sind nützlich, wenn Sie den Member anzeigen.  
  
 Diese Eigenschaft wird nur für [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) -Objekte unterstützt, die zu einem [Positions](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt gehören. Ein Fehler tritt auf, wenn von **Element Objekten,** die zu einem [Ebenenobjekt](../../../ado/reference/ado-md-api/level-object-ado-md.md) gehören, auf diese Eigenschaft verwiesen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ParentSameAsPrev-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
