---
title: ForeignKeyColumns-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: faefae483593b1c4e4369d3e61347a5c7528c001
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153416"
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
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) des Typs [TableMiningStructureColumn](../data-type/tableminingstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|[ForeignKeyColumn](../objects/column-element-assl.md) des Typs [DataItem](../data-type/dataitem-data-type-assl.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [MiningStructure-Element &#40;ASSL&#41;](../objects/miningstructure-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
