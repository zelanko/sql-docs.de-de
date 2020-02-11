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
ms.openlocfilehash: f1175d2a70c376e3da1e079e4a3eb93a39235758
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938460"
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
