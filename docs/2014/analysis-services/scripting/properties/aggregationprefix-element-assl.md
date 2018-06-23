---
title: AggregationPrefix-Element (ASSL) | Microsoft Docs
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
- AggregationPrefix Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationPrefix
helpviewer_keywords:
- AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 84f7b086e1cdc2516f0912a4580d0b3eb45132ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162132"
---
# <a name="aggregationprefix-element-assl"></a>AggregationPrefix-Element (ASSL)
  Definiert das gemeinsame Präfix, das innerhalb des zugeordneten übergeordneten Elements für die Aggregationsnamen verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube> <!-- or Database, MeasureGroup, Partition -->  
   ...  
   <AggregationPrefix>...</AggregationPrefix>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Cube](../objects/cube-element-assl.md), [Datenbank](../objects/database-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [Partition](../objects/partition-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Aggregationspräfixe generieren Aggregationsnamen in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], und generieren zusätzlich Tabellennamen in der relationalen Datenbank für Aggregationen, die in einer Partition, relationale OLAP (ROLAP) gespeichert.  
  
 Ein voll erweiterter Aggregationsname setzt sich aus folgenden Teilen zusammen:  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 Die ersten vier Teile des Aggregationsnamens bilden das Aggregationspräfix. Der Benutzer stellt die ersten vier Teile bereit:  
  
-   *DatabasePrefix* stellt den Wert der `AggregationPrefix` zugeordnete Element ein `Database` Element.  
  
-   *CubePrefix* stellt den Wert der `AggregationPrefix` zugeordnete Element ein `Cube` Element.  
  
-   *MeasureGroupPrefix* stellt den Wert der `AggregationPrefix` zugeordnete Element ein `MeasureGroup` Element.  
  
-   *PartitionPrefix* stellt den Wert der `AggregationPrefix` zugeordnete Element ein `Partition` Element.  
  
 Der fünfte Teil des Namens, *AggregationID*, ist eine systemdefinierte ID. Benutzer haben keinen Einfluss auf diesen Teil des Namens.  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `AggregationPrefix` im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup>, und <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  