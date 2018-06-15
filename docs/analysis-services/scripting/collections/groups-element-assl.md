---
title: Groups-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 886263a1470d8ebc0c45cc6022e087ee434c3ff6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032021"
---
# <a name="groups-element-assl"></a>Groups-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung der Gruppen von Elementen, die an ein Attribut gebunden sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Binding xsi:type="UserDefinedGroupBinding">  
   ...  
   <Groups>  
      <Group>...</Group>  
   </Groups>  
   ...  
</Binding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Binden von](../../../analysis-services/scripting/data-type/binding-data-type-assl.md) des Typs [UserDefinedGroupBinding](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|  
|Untergeordnete Elemente|[Gruppieren](../../../analysis-services/scripting/objects/group-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.GroupCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen und-Bindungen &#40;SSAS – mehrdimensional&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
