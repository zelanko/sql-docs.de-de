---
title: SQL Server, Speicherknoten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e9cc8a72709afd522c2bf54be9f324143b9f87d0
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51029816"
---
# <a name="sql-server-memory-node"></a>SQL Server, Speicherknoten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das **Speicherknoten** -Objekt in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Leistungsindikatoren bereit, mit denen Sie die Speicherauslastung des Servers für NUMA-Knoten überwachen können.  
  
## <a name="memory-node-counters"></a>Leistungsindikatoren für Speicherknoten  
 In dieser Tabelle sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Speicherknoten** beschrieben.  
  
|Speicher-Manager-Leistungsindikatoren von SQL Server|und Beschreibung|  
|----------------------------------------|-----------------|  
|**Datenbankknotenspeicher (KB)**|Gibt den Arbeitsspeicher an, die der Server derzeit in diesem Knoten für Datenbankseiten verwendet.|  
|**Freier Knotenspeicher (KB)**|Gibt den Arbeitsspeicher an, den der Server nicht in diesem Knoten verwendet.|  
|**Fremder Knotenspeicher (KB)**|Gibt die Menge des Arbeitsspeichers in diesem Knoten an, der kein Teil des lokalen NUMA-Arbeitsspeichers ist.|  
|**Gestohlener Knotenspeicher (KB)**|Gibt den Arbeitsspeicher an, die der Server derzeit in diesem Knoten für andere Zwecke als Datenbankseiten verwendet.|  
|**Zielknotenspeicher**|Gibt den idealen Arbeitsspeicher für diesen Knoten an.|  
|**Gesamtknotenspeicher**|Gibt die Gesamtmenge des Arbeitsspeichers an, für die der Server einen Commit in diesem Knoten ausgeführt hat.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, Puffer-Manager-Objekt](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  
