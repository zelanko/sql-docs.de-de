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
ms.openlocfilehash: 7560f7f2c487f42d26d83236d824bf997b4f49d1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778149"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown-Eigenschaft (ADO MD)
Gibt an, ob untergeordnete Elemente unmittelbar auf den [Member](./member-object-ado-md.md) auf der Achse folgen.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **booleschen** Wert zurück und ist schreibgeschützt. **DrilledDown** gibt **true** zurück, wenn keine untergeordneten Elemente des aktuellen Elements auf der Achse vorhanden sind. **DrilledDown** gibt **false** zurück, wenn das aktuelle Element über mindestens ein untergeordnetes Element auf der Achse verfügt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **DrilledDown** -Eigenschaft, um zu bestimmen, ob mindestens ein untergeordnetes Element dieses Elements auf der Achse unmittelbar nach diesem Member vorhanden ist. Diese Informationen sind nützlich, wenn Sie den Member anzeigen.  
  
 Diese Eigenschaft wird nur für [Member](./member-object-ado-md.md) -Objekte unterstützt, die zu einem [Positions](./position-object-ado-md.md) Objekt gehören. Ein Fehler tritt auf, wenn von **Element Objekten,** die zu einem [Ebenenobjekt](./level-object-ado-md.md) gehören, auf diese Eigenschaft verwiesen wird.  
  
## <a name="applies-to"></a>Gilt für  
 [Member-Objekt (ADO MD)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ParentSameAsPrev-Eigenschaft (ADO MD)](./parentsameasprev-property-ado-md.md)