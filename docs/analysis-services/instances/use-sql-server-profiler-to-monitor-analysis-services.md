---
title: Verwenden von SQL Server Profiler zum Überwachen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 190ae82b43f7a4f311d358ea9597a10cd5cc39dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181210"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>Verwenden von SQL Server Profiler zum Überwachen von Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verfolgt Engine-Prozessereignisse wie das Starten eines Batches oder einer Transaktion und erfasst Daten zu diesen Ereignissen. So können Sie die Server- und Datenbankaktivität überwachen (z.B. Benutzerabfragen oder Anmeldeaktivität). Sie können [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle oder -Datei aufzeichnen und später analysieren oder die aufgezeichneten Ereignisse in der gleichen oder einer anderen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz wiedergeben, um den genauen Ablauf anzuzeigen. Ereignisse können in Echtzeit oder schrittweise wiedergegeben werden. Sehr hilfreich ist es auch, die Ablaufverfolgungsereignisse zusammen mit den Leistungsindikatoren auf dem gleichen Computer auszuführen. Der Profiler kann diese auf der Grundlage von Zeit korrelieren und gemeinsam in einer einzelnen Zeitskala anzeigen. Ablaufverfolgungsereignisse bieten Ihnen mehr Details, während Leistungsindikatoren eine Aggregatsicht liefern. Informationen zum Erstellen und Ausführen von Ablaufverfolgungen finden Sie unter [Erstellen von Profilerablaufverfolgungen für Replay &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md).  
  
 In der folgenden Tabelle werden die Themen in diesem Abschnitt beschrieben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Einführung in die Überwachung von Analysis Services mit SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|Beschreibt das Verwenden von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zum Überwachen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz.|  
|[Erstellen von Profilerablaufverfolgungen für Replay &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)|Beschreibt die Anforderungen für das Erstellen einer Ablaufverfolgung zur Wiedergabe mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Analysis Services-Ablaufverfolgungsereignisse](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|Beschreibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Ereignisklassen. Diese Ereignisklassen sind Aktionen zugeordnet, die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generiert werden, und werden zum Wiedergeben von Ablaufverfolgungen verwendet.|  
  

  
  
