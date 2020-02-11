---
title: FilterAxis-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d44ac908c04338f80c18699319f75a068370c3e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938457"
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis-Eigenschaft (ADO MD)
Gibt Filter Informationen zum aktuellen [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt ein [Achsen](../../../ado/reference/ado-md-api/axis-object-ado-md.md) Objekt zurück und ist schreibgeschützt.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der **FilterAxis** -Eigenschaft geben Sie Informationen zu den Dimensionen zurück, die zum Segmentieren der Daten verwendet wurden. Die [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) -Eigenschaft der **Achse** gibt die Anzahl der Slicerdimensionen zurück. Diese Achse weist in der Regel nur eine Zeile auf.  
  
 Die von **FilterAxis** zurückgegebene **Achse** ist nicht in der [Achsen](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) Auflistung für ein [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekt enthalten.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Axis-Objekt (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Dimensions Objekt (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
