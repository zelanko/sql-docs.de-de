---
title: MeasureGroupAttributeBinding-Datentyp (Out-of-Line) (ASSL) | Microsoft-Dokumentation
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
- MeasureGroupAttributeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MeasureGroupAttributeBinding data type
ms.assetid: bfe09a95-4e04-4f93-9389-7dd0b4c8f5e4
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 244656b0ae951ec5f8274f11e58153faef80957d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218210"
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>MeasureGroupAttributeBinding-Datentyp (Out-of-Line) (ASSL)
  Definiert einen abgeleiteten Datentyp, der die Out-of-Line-Bindung eines Attributs in einer Dimension, die in einer Measuregruppe enthalten ist, darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Bindung](binding-data-type-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[CubeID](../properties/id-element-assl.md), [DatabaseID](../../xmla/xml-elements-properties/id-element-xmla.md), [MeasureGroupID](../properties/measuregroupid-element-assl.md), [GranularityAttributeID](../properties/attributeid-element-assl.md), [Quelle](../properties/source-element-binding-assl.md)|  
|Abgeleitete Elemente|[Binden von](../../xmla/xml-elements-properties/binding-element-xmla.md) ([Bindungen](../collections/attributes-element-assl.md) Auflistung von XML for Analysis (XMLA) [Batch](../../xmla/xml-elements-commands/batch-element-xmla.md) und [Prozess](../../xmla/xml-elements-commands/process-element-xmla.md) Befehle)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Out-of-Line-Bindungen finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
