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
manager: jroth
ms.openlocfilehash: cd7300a493067ced23a38e423befe0e77e6f0512
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709325"
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis-Eigenschaft (ADO MD)
Gibt Informationen über die aktuelle [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine [Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md) -Objekt und ist schreibgeschützt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **FilterAxis** -Eigenschaft zum Zurückgeben von Informationen zu den Dimensionen, die verwendet wurden, um die Daten in Slices aufzuteilen. Die [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) Eigenschaft der **Achse** gibt die Anzahl der Dimensionen zurück. Diese Achse ist in der Regel nur eine Zeile.  
  
 Die **Achse** zurückgegebenes **FilterAxis** befindet sich nicht der [Achsen](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) Sammlung für einen [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Axis-Objekt (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Dimension-Objekt (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
