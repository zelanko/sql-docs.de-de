---
title: AggregationPrefix-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 224c954186bff2b8e08375bfccf43ad980209f87
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
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
  
  
