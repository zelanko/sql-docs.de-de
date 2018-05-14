---
title: AllowedRowsExpression-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3b1a25e02e987c86dd07ed618e481ddf8fcadf9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="allowedrowsexpression-element-assl"></a>AllowedRowsExpression-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Für die **CellPermission** Element, das **Ausdruck** Element enthält einen logischen MDX-Ausdruck, der Zellen, die auf den angegebenen Rechte anwendbar identifiziert die [Zugriff](../../../analysis-services/scripting/properties/access-element-assl.md) Element von der **CellPermission** Element. Wenn der Wert eines **Expression** -Elements für ein **CellPermission** -Element leer ist, wird das **CellPermission** -Element ignoriert.  
  
 Beim Element **StandardAction** enthält das **Expression** -Element einen MDX-Ausdruck, der für die Inhalte der Aktion steht. Wenn der Wert eines **Expression** -Elements für ein **StandardAction** -Element leer ist, wird das **StandardAction** -Element ignoriert.  
  
 Die Elemente, die den übergeordneten Elementen im AMO-Objektmodell (Analysis Management Objects) entsprechen, sind <xref:Microsoft.AnalysisServices.CellPermission> und <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
