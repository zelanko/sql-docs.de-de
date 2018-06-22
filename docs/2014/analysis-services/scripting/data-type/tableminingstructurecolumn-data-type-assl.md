---
title: TableMiningStructureColumn-Datentyp (ASSL) | Microsoft Docs
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
- TableMiningStructureColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableMiningStructureColumn
helpviewer_keywords:
- TableMiningStructureColumn data type
ms.assetid: 350358b0-f2fc-43c3-957d-884c59fa879e
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9a57859ca60ae7fa83ec4bb4ea8f6a4e742a74f3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046527"
---
# <a name="tableminingstructurecolumn-data-type-assl"></a>TableMiningStructureColumn-Datentyp (ASSL)
  Definiert einen abgeleiteten Datentyp, der darstellt eine [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) Element, das im Gegensatz zu den skalaren Werten, die zugeordneten geschachtelte Tabellen enthalten die [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md) Element Skalare Werte enthält.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<TableMiningStructureColumn>  
   <!-- The following elements extend MiningStructureColumn -->  
   <ForeignKeyColumn>..</ForeignKeyColumn>  
   <SourceMeasureGroup>..</SourceMeasureGroup>  
   <Columns>..</Columns>  
   <Translations>..</Translations>  
</TableMiningStructureColumn>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|[Miningstructurecolumn-Objekt](miningstructurecolumn-data-type-assl.md)|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[Spalten](../collections/columns-element-assl.md), [ForeignKeyColumn](../objects/column-element-assl.md), [SourceMeasureGroup](../objects/group-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
|Abgeleitete Elemente|[Spalte](../objects/column-element-assl.md) ([Spalten](../collections/columns-element-assl.md) Auflistung von [MiningStructure](../objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  