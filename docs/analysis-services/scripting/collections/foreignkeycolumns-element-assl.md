---
title: ForeignKeyColumns-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 47fb825bee2d336ac6f8e5241947866f1e7c3bed
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031811"
---
# <a name="foreignkeycolumns-element-assl"></a>ForeignKeyColumns-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) des Typs [TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|[ForeignKeyColumn](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md) des Typs [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [MiningStructure-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
