---
title: Zusammenführen von Partitionen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c459fcb3efc86566eef046df30d2d8ad9ea601b4
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145842"
---
# <a name="merging-partitions-xmla"></a>Zusammenführen von Partitionen (XMLA)
  Wenn Partitionen, die dasselbe Aggregationsdesign und die Struktur verfügen, können Sie die Partition zusammenführen, mit der [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) -Befehl in XML for Analysis (XMLA) verwenden. Das Zusammenführen von Partitionen ist ein wichtiger Vorgang, wenn Sie Partitionen verwalten, insbesondere wenn es sich hierbei um Partitionen mit Vergangenheitsdaten handelt, die nach Datum partitioniert sind.  
  
 Beispielsweise verwendet ein finanzieller Cube möglicherweise zwei Partitionen:  
  
-   Eine Partition stellt die finanziellen Daten für das aktuelle Jahr dar und verwendet relationale OLAP-(ROLAP-)Speichereinstellungen in Echtzeit für die Leistung.  
  
-   Eine andere Partition enthält finanzielle Daten für vergangene Jahre und verwendet mehrdimensionale OLAP-(MOLAP-)Speichereinstellungen für die Speicherung.  
  
 Beide Partitionen verwenden andere Speichereinstellungen, jedoch den gleichen Aggregationsentwurf. Anstatt den Cube am Ende des Jahres mit Vergangenheitsdaten zahlreicher Jahre zu verarbeiten, können Sie auch den `MergePartitions`-Befehl verwenden, um die Partition für das aktuelle Jahr mit der Partition für die vergangenen Jahre zusammenzuführen. Dadurch werden die Aggregationsdaten beibehalten, ohne dass eine möglicherweise zeitaufwendige vollständige Verarbeitung des Cubes erforderlich ist.  
  
## <a name="specifying-partitions-to-merge"></a>Angeben von Partitionen für die Zusammenführung  
 Wenn die `MergePartitions` Befehl ausgeführt wurde, der Aggregationsdaten in der Quellpartitionen, die im angegebenen der [Quelle](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) Eigenschaft im angegebenen Zielpartition hinzugefügt wird die [Ziel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) Eigenschaft.  
  
> [!NOTE]  
>  Die `Source`-Eigenschaft kann mehrere Partitionsobjektverweise enthalten. Für die `Target`-Eigenschaft gilt dies jedoch nicht.  
  
 Damit die Zusammenführung erfolgreich ist, müssen sowohl die in der `Source`- als auch die in der `Target`-Eigenschaft angegebenen Partitionen in der gleichen Measuregruppe enthalten sein und den gleichen Aggregationsentwurf verwenden. Andernfalls tritt ein Fehler auf.  
  
 Die in der `Source`-Eigenschaft angegebenen Partitionen werden gelöscht, nachdem der Befehl `MergePartitions` erfolgreich abgeschlossen wurde.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>Description  
 Im folgenden Beispiel werden alle Partitionen in der **Customer Counts** -Measuregruppe des der **Adventure Works** Cubes in der **Adventure Works DW** Beispiel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für die Datenbank in der **Customers_2004** Partition.  
  
### <a name="code"></a>Code  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
