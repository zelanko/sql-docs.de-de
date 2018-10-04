---
title: ReadDefinition-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 176f1fa1f1a9f4fca3e773d65a5fda01c2f6752d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218110"
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
|Untergeordnete Elemente|None|  
  
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
  
  
