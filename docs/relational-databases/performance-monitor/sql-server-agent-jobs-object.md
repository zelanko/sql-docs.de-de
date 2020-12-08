---
title: SQL Server-Agent, Jobs-Objekt | Microsoft-Dokumentation
description: Hier lernen Sie das Leistungsobjekt „SQL Server-Agent-Aufträge“ kennen, das Leistungsindikatoren enthält, die Informationen über den SQL Server-Aufträgen melden.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 34b4a1e9fc276da5e629d7521609bca5570a5798
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505927"
---
# <a name="sql-server-agent-jobs-object"></a>SQL Server-Agent, Aufträge-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Das **Jobs** -Leistungsobjekt des SQL Server-Agents enthält Leistungsindikatoren, die Informationen zu SQL Server-Agent-Aufträgen ausgeben. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
 Die nachfolgende Tabelle enthält die **SQLAgent:Jobs** -Leistungsindikatoren.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|**Aktive Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der gerade ausgeführten Aufträge.|  
|**Fehlerhafte Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der Aufträge, die mit einem Fehler beendet wurden.|  
|**Erfolgsquote der Aufträge**|Dieser Leistungsindikator gibt den Prozentsatz der erfolgreich abgeschlossenen Aufträge aus.|  
|**Aktivierte Aufträge/Minute**|Dieser Leistungsindikator gibt die Anzahl der Aufträge aus, die innerhalb der letzten Minute gestartet wurden.|  
|**Aufträge in Warteschlange**|Dieser Leistungsindikator gibt die Anzahl der Aufträge aus, die zur Ausführung durch den SQL Server-Agent bereitstehen, jedoch noch nicht gestartet wurden.|  
|**Erfolgreiche Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der Aufträge, die erfolgreich beendet wurden.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Instanz|BESCHREIBUNG|  
|--------------|-----------------|  
|**_Total**|Informationen zu allen Aufträgen.|  
|**Warnungen**|Informationen zu durch Warnungen gestarteten Aufträgen.|  
|**Andere**|Informationen zu Aufträgen, die nicht durch Warnungen oder Zeitpläne gestartet wurden. Meist werden diese Aufträge manuell mithilfe von **sp_start_job** gestartet.|  
|**Zeitpläne**|Informationen zu durch Zeitpläne gestarteten Aufträgen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)   
 [Verwenden von Leistungsobjekten](../../ssms/agent/use-performance-objects.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
