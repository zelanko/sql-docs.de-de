---
title: SQL Server-Agent, Jobs-Objekt | Microsoft-Dokumentation
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
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: e3bb24d2a8f18077f69358ad26d2363c2ad743d4
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380961"
---
# <a name="sql-server-agent-jobs-object"></a>SQL Server-Agent, Aufträge-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das **Jobs** -Leistungsobjekt des SQL Server-Agents enthält Leistungsindikatoren, die Informationen zu SQL Server-Agent-Aufträgen ausgeben. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
 Die nachfolgende Tabelle enthält die **SQLAgent:Jobs** -Leistungsindikatoren.  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|**Aktive Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der gerade ausgeführten Aufträge.|  
|**Fehlerhafte Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der Aufträge, die mit einem Fehler beendet wurden.|  
|**Erfolgsquote der Aufträge**|Dieser Leistungsindikator gibt den Prozentsatz der erfolgreich abgeschlossenen Aufträge aus.|  
|**Aktivierte Aufträge/Minute**|Dieser Leistungsindikator gibt die Anzahl der Aufträge aus, die innerhalb der letzten Minute gestartet wurden.|  
|**Aufträge in Warteschlange**|Dieser Leistungsindikator gibt die Anzahl der Aufträge aus, die zur Ausführung durch den SQL Server-Agent bereitstehen, jedoch noch nicht gestartet wurden.|  
|**Erfolgreiche Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der Aufträge, die erfolgreich beendet wurden.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Instanz|und Beschreibung|  
|--------------|-----------------|  
|**_Total**|Informationen zu allen Aufträgen.|  
|**Warnungen**|Informationen zu durch Warnungen gestarteten Aufträgen.|  
|**Sonstige**|Informationen zu Aufträgen, die nicht durch Warnungen oder Zeitpläne gestartet wurden. Meist werden diese Aufträge manuell mithilfe von **sp_start_job**gestartet.|  
|**Zeitpläne**|Informationen zu durch Zeitpläne gestarteten Aufträgen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)   
 [Verwenden von Leistungsobjekten](../../ssms/agent/use-performance-objects.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
