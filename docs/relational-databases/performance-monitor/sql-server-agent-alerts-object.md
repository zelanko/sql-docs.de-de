---
title: SQL Server-Agent, Alerts-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: ca1234a9b70c3da26ed9146e4c5eda51ca431f80
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53379871"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Warnungen](../../ssms/agent/alerts.md)   
 [Verwenden von Leistungsobjekten](../../ssms/agent/use-performance-objects.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
