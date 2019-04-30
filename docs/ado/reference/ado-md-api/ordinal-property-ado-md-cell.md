---
title: Ordinal-Eigenschaft (ADO MD Cell) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae4b9a3c623fdcb22d7665e4242ce2f58397b2a1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281928"
---
# <a name="ordinal-property-ado-md-cell"></a>Ordinal-Eigenschaft (ADO MD Cell)
Identifiziert eindeutig einen [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md) durch ihre Position innerhalb eines cellSets dar.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **lange** ganze Zahl und ist schreibgeschützt.  
  
## <a name="remarks"></a>Hinweise  
 Eindeutig identifiziert den Wert der Zelle Ordnungszahl die Zelle innerhalb eines cellSets dar. Grundsätzlich werden Zellen in einem Cellset nummeriert, als wäre das Cellset ein *p*-, eindimensionales Array, in denen *p* ist die Anzahl der [Achsen](../../../ado/reference/ado-md-api/axes-collection-ado-md.md). Die Zellen werden beginnend mit 0 (null) in zeilengerichteter Reihenfolge nummeriert. So sieht die Formel zum Berechnen der Ordinalzahl einer Zelle aus:  
  
 Ordnungswert der Zelle kann verwendet werden, mit der [Element](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) Eigenschaft der [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekt, das schnelle Abrufen der [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Cell-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Achse-Beispiel (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Item-Eigenschaft (ADO MD Cellset)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Ordinal-Eigenschaft (ADO MD Position)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)
