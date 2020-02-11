---
title: Ordinal-Eigenschaft (ADO MD Zelle) | Microsoft-Dokumentation
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
ms.openlocfilehash: 194b72ce66eb2efdc3a246f24948b01c790f7b8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949379"
---
# <a name="ordinal-property-ado-md-cell"></a>Ordinal-Eigenschaft (ADO MD Cell)
Identifiziert eine [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md) eindeutig anhand ihrer Position in einem CellSet.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **lange** ganze Zahl zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Ordinalwert der Zelle identifiziert die Zelle innerhalb eines Cellsets eindeutig. Konzeptionell werden Zellen in einem CellSet nummeriert, als ob das Cellset ein *p*-dimensionales Array wäre, wobei *p* für die Anzahl der [Achsen](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)steht. Zellen werden beginnend mit 0 (null) in der Reihenfolge der Reihenfolge nummeriert. Dies ist die Formel zum Berechnen der Ordinalzahl einer Zelle:  
  
 Der Ordinalwert der Zelle kann mit der [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) -Eigenschaft des [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekts verwendet werden, um die [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md)schnell abzurufen.  
  
## <a name="applies-to"></a>Gilt für  
 [Cell-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Achsen Beispiel (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [CellSet-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Item-Eigenschaft (ADO MD Cellset)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Ordinal-Eigenschaft (ADO MD Position)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)
