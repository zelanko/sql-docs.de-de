---
title: Zusammenführen von Partitionen (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 419ebd0d67b65213fde7393430aedec14249b2ae
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261639"
---
# <a name="merging-partitions-xmla"></a>Zusammenführen von Partitionen (XMLA)
  Wenn Partitionen, die dasselbe Aggregationsdesign und die Struktur verfügen, können Sie die Partition zusammenführen, mit der [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) -Befehl in XML for Analysis (XMLA) verwenden. Das Zusammenführen von Partitionen ist ein wichtiger Vorgang, wenn Sie Partitionen verwalten, insbesondere wenn es sich hierbei um Partitionen mit Vergangenheitsdaten handelt, die nach Datum partitioniert sind.  
  
 Beispielsweise verwendet ein finanzieller Cube möglicherweise zwei Partitionen:  
  
-   Eine Partition stellt die finanziellen Daten für das aktuelle Jahr dar und verwendet relationale OLAP-(ROLAP-)Speichereinstellungen in Echtzeit für die Leistung.  
  
-   Eine andere Partition enthält finanzielle Daten für vergangene Jahre und verwendet mehrdimensionale OLAP-(MOLAP-)Speichereinstellungen für die Speicherung.  
  
 Beide Partitionen verwenden andere Speichereinstellungen, jedoch den gleichen Aggregationsentwurf. Sie können stattdessen verwenden, anstatt die Verarbeitung des Cubes zahlreicher Jahre historische Daten am Ende des Jahres an, die **MergePartitions** Befehl aus, um die Partition für das aktuelle Jahr in die Partition für vergangene Jahre zusammenzuführen. Dadurch werden die Aggregationsdaten beibehalten, ohne dass eine möglicherweise zeitaufwendige vollständige Verarbeitung des Cubes erforderlich ist.  
  
## <a name="specifying-partitions-to-merge"></a>Angeben von Partitionen für die Zusammenführung  
 Wenn die **MergePartitions** Befehl ausgeführt wurde, der Aggregationsdaten in der Quellpartitionen, die im angegebenen der [Quelle](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) Eigenschaft im angegebenen Zielpartition hinzugefügt wird die [Ziel ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) Eigenschaft.  
  
> [!NOTE]  
>  Die **Quelle** -Eigenschaft kann mehrere partitionsobjektverweise enthalten. Allerdings die **Ziel** können Sie die Eigenschaft nicht.  
  
 Damit die Zusammenführung erfolgreich, die in beiden angegebenen Partitionen der **Quelle** und **Ziel** muss der gleichen Measuregruppe enthalten sein und den gleichen Aggregationsentwurf verwenden. Andernfalls tritt ein Fehler auf.  
  
 Im angegebenen Partitionen der **Quelle** werden gelöscht, nachdem die **MergePartitions** Befehl erfolgreich abgeschlossen wurde.  
  
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
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
