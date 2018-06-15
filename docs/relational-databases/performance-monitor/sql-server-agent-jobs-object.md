---
title: SQL Server-Agent, Jobs-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ccbf65c2b1d297b8fd36ef75f84a6a8c09b21175
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950495"
---
# <a name="sql-server-agent-jobs-object"></a>SQL Server-Agent, Aufträge-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das **Jobs** -Leistungsobjekt des SQL Server-Agents enthält Leistungsindikatoren, die Informationen zu SQL Server-Agent-Aufträgen ausgeben. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
 Die nachfolgende Tabelle enthält die **SQLAgent:Jobs** -Leistungsindikatoren.  
  
|Name|Description|  
|----------|-----------------|  
|**Aktive Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der gerade ausgeführten Aufträge.|  
|**Fehlerhafte Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der Aufträge, die mit einem Fehler beendet wurden.|  
|**Erfolgsquote der Aufträge**|Dieser Leistungsindikator gibt den Prozentsatz der erfolgreich abgeschlossenen Aufträge aus.|  
|**Aktivierte Aufträge/Minute**|Dieser Leistungsindikator gibt die Anzahl der Aufträge aus, die innerhalb der letzten Minute gestartet wurden.|  
|**Aufträge in Warteschlange**|Dieser Leistungsindikator gibt die Anzahl der Aufträge aus, die zur Ausführung durch den SQL Server-Agent bereitstehen, jedoch noch nicht gestartet wurden.|  
|**Erfolgreiche Aufträge**|Dieser Leistungsindikator erfasst die Anzahl der Aufträge, die erfolgreich beendet wurden.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Instanz|Description|  
|--------------|-----------------|  
|**_Total**|Informationen zu allen Aufträgen.|  
|**Warnungen**|Informationen zu durch Warnungen gestarteten Aufträgen.|  
|**Sonstige**|Informationen zu Aufträgen, die nicht durch Warnungen oder Zeitpläne gestartet wurden. Meist werden diese Aufträge manuell mithilfe von **sp_start_job**gestartet.|  
|**Zeitpläne**|Informationen zu durch Zeitpläne gestarteten Aufträgen.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Implementieren von Aufträgen](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [Verwenden von Leistungsobjekten](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
