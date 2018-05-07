---
title: StandardAction-Datentyp (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 343a45c1b0e74fc4fd81cf603ab1a53903625b63
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="standardaction-data-type-assl"></a>StandardAction-Datentyp (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert einen abgeleiteten Datentyp, der ein beliebiges [Action](../../../analysis-services/scripting/objects/action-element-assl.md) -Element darstellt, außer einem [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md) -Element oder einem [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) -Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<StandardAction>  
   <!-- The following elements extend Action -->  
   <Expression>...</Expression>  
</StandardAction>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Basisdatentypen|[Aktion](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|  
|Abgeleitete Datentypen|Keine|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|Keine|  
|Untergeordnete Elemente|[Ausdruck](../../../analysis-services/scripting/properties/expression-element-assl.md)|  
|Abgeleitete Elemente|[Aktion](../../../analysis-services/scripting/objects/action-element-assl.md) ([Aktionen](../../../analysis-services/scripting/collections/actions-element-assl.md) Auflistung von [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) oder [Perspektive](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
