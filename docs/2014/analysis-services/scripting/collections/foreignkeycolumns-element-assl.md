---
title: ForeignKeyColumns-Element (ASSL) | Microsoft Docs
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
- ForeignKeyColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForeignKeyColumns
helpviewer_keywords:
- ForeignKeyColumns element
ms.assetid: 0a673c1a-73dd-4217-aa41-56b340b5e1ab
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: da17077a4a75efc53de65b2168a5332db137bfd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061024"
---
# <a name="foreignkeycolumns-element-assl"></a>ForeignKeyColumns-Element (ASSL)
  Enthält die Sammlung der Spalten, die den Join mit der übergeordneten Tabelle für eine relationale Datenquelle identifizieren.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructureColumn xsi:type="TableMiningStructureColumn">  
   ...  
   <ForeignKeyColumns>  
      <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
...</ForeignKeyColumns>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) des Typs [TableMiningStructureColumn](../data-type/tableminingstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|[ForeignKeyColumn](../objects/column-element-assl.md) des Typs [DataItem](../data-type/dataitem-data-type-assl.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [MiningStructure-Element &#40;ASSL&#41;](../objects/miningstructure-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  