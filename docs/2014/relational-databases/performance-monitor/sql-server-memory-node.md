---
title: SQL Server, Speicherknoten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b2bffcd00bad148022e66e95dca9f03f70faee43
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175190"
---
# <a name="sql-server-memory-node"></a>SQL Server, Speicherknoten
  Das **Speicherknoten** -Objekt in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Leistungsindikatoren bereit, mit denen Sie die Speicherauslastung des Servers für NUMA-Knoten überwachen können.  
  
## <a name="memory-node-counters"></a>Leistungsindikatoren für Speicherknoten  
 In dieser Tabelle sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Speicherknoten** beschrieben.  
  
|Speicher-Manager-Leistungsindikatoren von SQL Server|Description|  
|----------------------------------------|-----------------|  
|**Datenbankknotenspeicher (KB)**|Gibt den Arbeitsspeicher an, die der Server derzeit in diesem Knoten für Datenbankseiten verwendet.|  
|**Freier Knotenspeicher (KB)**|Gibt den Arbeitsspeicher an, den der Server nicht in diesem Knoten verwendet.|  
|**Fremder Knotenspeicher (KB)**|Gibt die Menge des Arbeitsspeichers in diesem Knoten an, der kein Teil des lokalen NUMA-Arbeitsspeichers ist.|  
|**Gestohlener Knotenspeicher (KB)**|Gibt den Arbeitsspeicher an, die der Server derzeit in diesem Knoten für andere Zwecke als Datenbankseiten verwendet.|  
|**Zielknotenspeicher**|Gibt den idealen Arbeitsspeicher für diesen Knoten an.|  
|**Gesamtknotenspeicher**|Gibt die Gesamtmenge des Arbeitsspeichers an, für die der Server einen Commit in diesem Knoten ausgeführt hat.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, Puffer-Manager-Objekt](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
