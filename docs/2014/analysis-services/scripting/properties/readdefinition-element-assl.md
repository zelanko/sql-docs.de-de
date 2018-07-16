---
title: ReadDefinition-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ReadDefinition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReadDefinition
helpviewer_keywords:
- ReadDefinition element
ms.assetid: 1f250129-13b2-41b9-b083-b5aacddf0060
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fed91c75bd717e67dd624fc16f7091be24fb030c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297230"
---
# <a name="readdefinition-element-assl"></a>ReadDefinition-Element (ASSL)
  Bestimmt, ob Elemente die Datenbankdefinition oder die Definition der Objekte in der Datenbank lesen können.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Permission> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <ReadDefinition>...</ReadDefinition>  
   ...  
</Permission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Keine*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubePermission](../objects/cubepermission-element-assl.md), [DatabasePermission](../objects/databasepermission-element-assl.md), [DimensionPermission](../objects/dimensionpermission-element-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission ](../objects/miningstructurepermission-element-assl.md), [Berechtigung](../data-type/permission-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Keine*|Der Zugriff auf die Objektdefinition ist nicht zulässig.|  
|*Grundlegend*|Der grundlegende Zugriff auf die Objektdefinition ist nicht zulässig. **Hinweis:** diese Berechtigung ist erforderlich für lokale Cubes zu erstellen, verknüpfen Measuregruppen und Verknüpfen von Dimensionen.|  
|*Zulässig*|Der vollständige Zugriff auf die Objektdefinition ist nicht zulässig. **Hinweis:** diese Berechtigung ist erforderlich, für die Ausführung einer [Discover](../../xmla/xml-elements-methods-discover.md) XML for Analysis (XMLA) aufrufen, die mit dem DISCOVER_XML_METADATA-Parameter.|  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `ReadDefinition` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.CubePermission>, <xref:Microsoft.AnalysisServices.DatabasePermission>, <xref:Microsoft.AnalysisServices.DimensionPermission>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, <xref:Microsoft.AnalysisServices.MiningStructurePermission>, und <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Role-Element &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
