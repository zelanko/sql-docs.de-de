---
title: AllowedRowsExpression-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f335861084f86fa509b8c2bc3f977332d5e1da7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291326"
---
# <a name="allowedrowsexpression-element-assl"></a>AllowedRowsExpression-Element (ASSL)
  Enthält einen DAX-Ausdruck (Data Analysis Expression) des booleschen Typs, der den Inhalt des übergeordneten Elements definiert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CellPermission](../objects/cellpermission-element-assl.md), [StandardAction](../data-type/action-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Für die `CellPermission` Element der `Expression` Element enthält einen logischen MDX-Ausdruck, der Zellen, die auf die angegebenen Rechte anwendbar identifiziert die [Zugriff](access-element-assl.md) Element der `CellPermission` Element. Wenn der Wert des ein `Expression` -Element für eine `CellPermission` -Element leer ist, die `CellPermission` Element wird ignoriert.  
  
 Beim Element `StandardAction` enthält das `Expression`-Element einen MDX-Ausdruck, der für die Inhalte der Aktion steht. Wenn der Wert des ein `Expression` -Element für eine `StandardAction` -Element leer ist, die `StandardAction` Element wird ignoriert.  
  
 Die Elemente, die den übergeordneten Elementen im AMO-Objektmodell (Analysis Management Objects) entsprechen, sind <xref:Microsoft.AnalysisServices.CellPermission> und <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
