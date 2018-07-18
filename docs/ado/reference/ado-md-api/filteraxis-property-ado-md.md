---
title: FilterAxis-Eigenschaft (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f59eeff4dc01e2f881712ca2309a83e80d785b27
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283929"
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis-Eigenschaft (ADO MD)
Gibt Informationen zu den aktuellen an [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine [Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md) Objekt, und ist schreibgeschützt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **FilterAxis** -Eigenschaft zum Zurückgeben von Informationen zu den Dimensionen, die verwendet wurden, um die Daten in Slices aufzuteilen. Die [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) Eigenschaft von der **Achse** gibt die Anzahl der Dimensionen zurück. Diese Achse verfügt normalerweise nur eine Zeile.  
  
 Die **Achse** zurückgegebenes **FilterAxis** ist nicht Bestandteil der [Achsen](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) Auflistung für einen [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Achsenobjekt (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Dimensionsobjekt (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
