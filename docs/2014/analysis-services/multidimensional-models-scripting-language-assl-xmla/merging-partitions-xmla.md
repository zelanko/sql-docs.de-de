---
title: Zusammenführen von Partitionen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 65840066d3e95571db511a2015a1bee64aa8d922
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544952"
---
# <a name="merging-partitions-xmla"></a>Zusammenführen von Partitionen (XMLA)
  Wenn Partitionen denselben Aggregations Entwurf und dieselbe Struktur aufweisen, können Sie die Partition zusammenführen, indem Sie den [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) -Befehl in XML for Analysis (XMLA) verwenden. Das Zusammenführen von Partitionen ist ein wichtiger Vorgang, wenn Sie Partitionen verwalten, insbesondere wenn es sich hierbei um Partitionen mit Vergangenheitsdaten handelt, die nach Datum partitioniert sind.  
  
 Beispielsweise verwendet ein finanzieller Cube möglicherweise zwei Partitionen:  
  
-   Eine Partition stellt die finanziellen Daten für das aktuelle Jahr dar und verwendet relationale OLAP-(ROLAP-)Speichereinstellungen in Echtzeit für die Leistung.  
  
-   Eine andere Partition enthält finanzielle Daten für vergangene Jahre und verwendet mehrdimensionale OLAP-(MOLAP-)Speichereinstellungen für die Speicherung.  
  
 Beide Partitionen verwenden andere Speichereinstellungen, jedoch den gleichen Aggregationsentwurf. Anstatt den Cube am Ende des Jahres mit Vergangenheitsdaten zahlreicher Jahre zu verarbeiten, können Sie auch den `MergePartitions`-Befehl verwenden, um die Partition für das aktuelle Jahr mit der Partition für die vergangenen Jahre zusammenzuführen. Dadurch werden die Aggregationsdaten beibehalten, ohne dass eine möglicherweise zeitaufwendige vollständige Verarbeitung des Cubes erforderlich ist.  
  
## <a name="specifying-partitions-to-merge"></a>Angeben von Partitionen für die Zusammenführung  
 Wenn der `MergePartitions` Befehl ausgeführt wird, werden die Aggregations Daten, die in den in der [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) -Eigenschaft angegebenen Quell Partitionen gespeichert sind, der in der [target](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) -Eigenschaft angegebenen Ziel Partition hinzugefügt.  
  
> [!NOTE]  
>  Die `Source`-Eigenschaft kann mehrere Partitionsobjektverweise enthalten. Für die `Target`-Eigenschaft gilt dies jedoch nicht.  
  
 Damit die Zusammenführung erfolgreich ist, müssen sowohl die in der `Source`- als auch die in der `Target`-Eigenschaft angegebenen Partitionen in der gleichen Measuregruppe enthalten sein und den gleichen Aggregationsentwurf verwenden. Andernfalls tritt ein Fehler auf.  
  
 Die in der `Source`-Eigenschaft angegebenen Partitionen werden gelöscht, nachdem der Befehl `MergePartitions` erfolgreich abgeschlossen wurde.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="description"></a>BESCHREIBUNG  
 Im folgenden Beispiel werden alle Partitionen in der Measure-Gruppe **Customer Counts** des **Adventure Works** -Cubes in der **Adventure Works DW** -Beispiel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank in die **Customers_2004** Partition zusammengeführt.  
  
### <a name="code"></a>Code  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
