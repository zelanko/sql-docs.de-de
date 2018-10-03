---
title: MeasureGroupHierarchy-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroupHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupHierarchy
helpviewer_keywords:
- MeasureGroupHierarchy data type
ms.assetid: 63c2fd97-d7ad-4715-8c49-24d684bc92d7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d2dafbeb5f423836c444490c21134cc64a402e6c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133350"
---
# <a name="measuregrouphierarchy-data-type-assl"></a>MeasureGroupHierarchy-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der Informationen über eine Hierarchie in einer Measuregruppe darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroupHierarchy>  
   <HierarchyID>...</HierarchyID>  
      <Annotations>...</Annotations>  
</MeasureGroupHierarchy>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [HierarchyID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|[Hierarchie](../objects/hierarchy-element-assl.md) ([Hierarchien](../collections/hierarchies-element-assl.md) -Auflistung von [RegularMeasureGroupDimension](dimension-data-type-assl.md))|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
