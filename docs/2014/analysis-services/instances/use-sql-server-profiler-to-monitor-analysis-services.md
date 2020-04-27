---
title: Verwenden Sie SQL Server Profiler, um Analysis Services zu überwachen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2a042d49dc8222c0357c6fde6077153c40b11b53
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079530"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>Verwenden von SQL Server Profiler zum Überwachen von Analysis Services
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verfolgt Engine-Prozessereignisse wie das Starten eines Batches oder einer Transaktion und erfasst Daten zu diesen Ereignissen. So können Sie die Server- und Datenbankaktivität überwachen (z.B. Benutzerabfragen oder Anmeldeaktivität). Sie können [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle oder -Datei aufzeichnen und später analysieren oder die aufgezeichneten Ereignisse in der gleichen oder einer anderen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz wiedergeben, um den genauen Ablauf anzuzeigen. Ereignisse können in Echtzeit oder schrittweise wiedergegeben werden. Sehr hilfreich ist es auch, die Ablaufverfolgungsereignisse zusammen mit den Leistungsindikatoren auf dem gleichen Computer auszuführen. Der Profiler kann diese auf der Grundlage von Zeit korrelieren und gemeinsam in einer einzelnen Zeitskala anzeigen. Ablaufverfolgungsereignisse bieten Ihnen mehr Details, während Leistungsindikatoren eine Aggregatsicht liefern. Informationen zum Erstellen und Ausführen von Ablaufverfolgungen finden Sie unter [Erstellen von Profilerablaufverfolgungen für Replay &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md).  
  
 In der folgenden Tabelle werden die Themen in diesem Abschnitt beschrieben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Einführung in die Überwachung von Analysis Services mit SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|Beschreibt das Verwenden von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zum Überwachen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz.|  
|[Erstellen von Profilerablaufverfolgungen für Replay &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)|Beschreibt die Anforderungen für das Erstellen einer Ablaufverfolgung zur Wiedergabe mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Analysis Services-Ablaufverfolgungsereignisse](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|Beschreibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Ereignisklassen. Diese Ereignisklassen sind Aktionen zugeordnet, die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generiert werden, und werden zum Wiedergeben von Ablaufverfolgungen verwendet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen einer Instanz von Analysis Services](monitor-an-analysis-services-instance.md)  
  
  
