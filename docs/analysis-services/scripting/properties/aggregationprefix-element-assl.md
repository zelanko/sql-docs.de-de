---
title: AggregationPrefix-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b23721728f8e196c47ab326024a6f514631c3b6f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031491"
---
# <a name="aggregationprefix-element-assl"></a>AggregationPrefix-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), [Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Aggregationspräfixe generieren Aggregationsnamen in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], und generieren zusätzlich Tabellennamen in der relationalen Datenbank für Aggregationen, die in einer Partition, relationale OLAP (ROLAP) gespeichert.  
  
 Ein voll erweiterter Aggregationsname setzt sich aus folgenden Teilen zusammen:  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 Die ersten vier Teile des Aggregationsnamens bilden das Aggregationspräfix. Der Benutzer stellt die ersten vier Teile bereit:  
  
-   *DatabasePrefix* stellt den Wert des einem **AggregationPrefix** -Element zugeordneten **Database** -Elements dar.  
  
-   *CubePrefix* stellt den Wert des einem **AggregationPrefix** -Element zugeordneten **Cube** -Elements dar.  
  
-   *MeasureGroupPrefix* stellt den Wert des einem **AggregationPrefix** -Element zugeordneten **MeasureGroup** -Elements dar.  
  
-   *PartitionPrefix* stellt den Wert des einem **AggregationPrefix** -Element zugeordneten **Partition** -Elements dar.  
  
 Der fünfte Teil des Namens, *AggregationID*, ist eine systemdefinierte ID. Benutzer haben keinen Einfluss auf diesen Teil des Namens.  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen **AggregationPrefix** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup>, und <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
