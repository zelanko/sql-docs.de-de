---
title: Binding-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Binding Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.binding
- http://schemas.microsoft.com/analysisservices/2003/engine#Binding
- urn:schemas-microsoft-com:xml-analysis#Binding
helpviewer_keywords:
- Binding element
ms.assetid: d5acd8d4-8551-449a-ae30-d0ba828cc02d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 397e02a8aae8978d36be088b792df5edc163c63d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168250"
---
# <a name="binding-element-xmla"></a>Binding-Element (XMLA)
  Definiert eine Out-of-Line-Bindung für ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Objekt, z. B. ein Attribut in einer Dimension, für die [Bindungen](bindings-element-xmla.md) Auflistung von einem [Batch](../xml-elements-commands/batch-element-xmla.md) oder [ Prozess](../xml-elements-commands/process-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Bindings>  
   <Binding xsi:type="DimensionAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="MeasureGroupAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="PartitionBinding">...</Binding>  
</Bindings>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[DimensionAttributeBinding](../../scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md), [MeasureGroupAttributeBinding](../../scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [PartitionBinding](../../scripting/data-type/binding-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Bindungen](bindings-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 `Binding` -Elemente definieren Out-of-Line-Bindungen, abgesehen von Datenquellen und Datenquellensichten für [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Objekte zur Verarbeitung durch eine `Batch` oder `Process` Befehl. Weitere Informationen zur Verarbeitung von Objekten finden Sie unter [Verarbeiten von Objekten &#40;XMLA&#41;](../xml-elements-objects.md).  
  
 Weitere Informationen zur Out-of-Line-Bindungen finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
