---
title: SQL Server, Speicherknoten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32a2296fdb68e640ce8ebfc8dd9cdb351666b337
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250582"
---
# <a name="sql-server-memory-node"></a>SQL Server, Speicherknoten
  Das **Speicher Knoten** Objekt in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet Leistungsindikatoren zum Überwachen der Server Speicherauslastung auf NUMA-Knoten.  
  
## <a name="memory-node-counters"></a>Leistungsindikatoren für Speicherknoten  
 In dieser Tabelle sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Speicherknoten** beschrieben.  
  
|Speicher-Manager-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|----------------------------------------|-----------------|  
|**Datenbankknoten Speicher (KB)**|Gibt den Arbeitsspeicher an, die der Server derzeit in diesem Knoten für Datenbankseiten verwendet.|  
|**Freier Knoten Speicher (KB)**|Gibt den Arbeitsspeicher an, den der Server nicht in diesem Knoten verwendet.|  
|**Fremd Knoten Speicher (KB)**|Gibt die Menge des Arbeitsspeichers in diesem Knoten an, der kein Teil des lokalen NUMA-Arbeitsspeichers ist.|  
|**Gestohlener Speicher Knoten (KB)**|Gibt den Arbeitsspeicher an, die der Server derzeit in diesem Knoten für andere Zwecke als Datenbankseiten verwendet.|  
|**Zielknoten Speicher**|Gibt den idealen Arbeitsspeicher für diesen Knoten an.|  
|**Knoten Speicher gesamt**|Gibt die Gesamtmenge des Arbeitsspeichers an, für die der Server einen Commit in diesem Knoten ausgeführt hat.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, Puffer-Manager-Objekt](sql-server-buffer-manager-object.md)   
 [sys. dm_os_performance_counters &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
