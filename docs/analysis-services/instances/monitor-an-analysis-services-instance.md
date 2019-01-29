---
title: Eine Übersicht über die Analysis Services-Instanz überwachen | Microsoft-Dokumentation
ms.date: 11/16/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 39cc5a22165d07aafce29e4216548c4e8d226892
ms.sourcegitcommit: b51edbe07a0a2fdb5f74b5874771042400baf919
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087629"
---
# <a name="monitoring-overview"></a>Übersicht über die Überwachung
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services verfügt über verschiedene Tools zum Überwachen und Optimieren der Leistung von Ihren Servern. Das richtige Tool ergibt sich aus der Art der gewünschten Überwachung oder Optimierung sowie aus den jeweils zu überwachenden Ereignissen.

Weitere Informationen zur Überwachung von SQL Server Analysis Services finden Sie unter den [SQL Server 2008 R2-Vorgangshandbuch](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
## <a name="monitoring-tools"></a>Überwachungstools  

|Tool  |Description  |
|---------|---------|
|[SQL Server Profiler](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)      |   Verfolgt Engine-Prozessereignisse an. Es erfasst auch Daten zu diesen Ereignissen, können Sie Server- und Datenbankaktivität überwachen.      |
| [Erweiterte Ereignisse](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)     |   Ein kompaktes Ablaufverfolgungs- und die Leistung, System, das nur sehr wenige Systemressourcen verwendet, dadurch stellen sie ein ideales Tool zum Diagnostizieren von Problemen auf den Test und Produktion.       |
| [Dynamische Verwaltungssichten &#40;DMVs&#41;](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)      |   Abfragen, die Informationen zu modellobjekten, Server-Vorgänge und Integrität der Server zurückzugeben. Die Abfrage, die basierend auf SQL ist eine Schnittstelle zu Schemarowsets.      |
| [Ablaufverfolgungsereignisse](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)     |  Führen Sie die Aktivität von einer Instanz von erfassen und Analysieren anschließend die von der Instanz generierten Ablaufverfolgungsereignisse. Ablaufverfolgungsereignisse werden so gruppiert, dass verwandte Ablaufverfolgungsereignisse einfacher gefunden werden können.        |
|   [Leistungsindikatoren](../../analysis-services/instances/performance-counters-ssas.md)\*    |    Mit dem Systemmonitor können Sie die Leistung einer Microsoft SQL Server Analysis Services (SSAS)-Instanz mithilfe von Leistungsindikatoren überwachen.     |
|[Protokollvorgänge](../../analysis-services/instances/performance-counters-ssas.md)\*|Eine SQL Server Analysis Services-Instanz wird serverbenachrichtigungen, Fehler und Warnungen in der Datei "Msmdsrv.log" – einer für jede Instanz protokolliert, die Sie installieren. |

\* Gilt nur für SQL Server Analysis Services ein.

## <a name="see-also"></a>Siehe auch

[Überwachen von Azure Analysis Services-servermetriken](https://docs.microsoft.com/azure/analysis-services/analysis-services-monitor)   
[Einrichten der diagnoseprotokollierung für Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-logging)
