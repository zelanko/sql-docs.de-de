---
title: SQL Server-Agent, Alerts-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3776ba97213564b36630c82845b0620b6d2cacd8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852984"
---
# <a name="sql-server-agent-alerts-object"></a>SQL Server-Agent, Warnungen-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das Leistungsobjekt **Warnungen** des SQL Server-Agents enthält Leistungsindikatoren mit Informationen über SQL Server-Agent-Warnungen. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
 Die folgende Tabelle enthält die Leistungsindikatoren **SQLAgent:Warnungen** .  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|**Aktivierte Warnungen**|Dieser Leistungsindikator berichtet die Gesamtanzahl der Warnungen, die der SQL Server-Agent seit dem letzten Neustart aktiviert hat.|  
|**Aktivierte Warnungen/Minute**|Dieser Leistungsindikator berichtet die Anzahl der Warnungen, die der SQL Server-Agent innerhalb der letzten Minute aktiviert hat.|  
  
> [!NOTE]  
>  Um dieses SQL Server-Agent-Objekt verwenden zu können, muss der Benutzer ein Mitglied der festen Serverrolle **sysadmin** sein.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Warnungen](../../ssms/agent/alerts.md)   
 [Verwenden von Leistungsobjekten](../../ssms/agent/use-performance-objects.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
