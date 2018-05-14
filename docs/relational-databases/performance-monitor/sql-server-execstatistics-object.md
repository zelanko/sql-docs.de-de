---
title: SQL Server, Ausführungsstatistik-Objekt | Microsoft-Dokumentation
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
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a6c8f32055fab862e4f74781ecb6220a5859f14f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, Ausführungsstatistik-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das **SQLServer:ExecStatistics** -Objekt in Microsoft SQL Server stellt Leistungsindikatoren zum Überwachen verschiedener Vorgänge zur Verfügung.  
  
 In dieser Tabelle werden die **Exec Statistics** -Leistungsindikatoren von SQL Server beschrieben.  
  
|Exec Statistics-Leistungsindikatoren von SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Verteilte Abfrage**|Für die Ausführung von verteilten Abfragen wichtige Statistiken.|  
|**DTC-Aufrufe**|Für die Ausführung von DTC-Aufrufen wichtige Statistiken.|  
|**Erweiterte Prozeduren**|Für die Ausführung von erweiterten Prozeduren wichtige Statistiken.|  
|**OLE DB-Aufrufe**|Für die Ausführung von OLE DB-Aufrufen wichtige Statistiken.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Element|Description|  
|----------|-----------------|  
|**Durchschnittliche Ausführungszeit (ms)**|Durchschnittliche Ausführungszeit des ausgewählten Ausführungstyps.|  
|**Kumulierte Ausführungszeit (ms) pro Sekunde**|Aggregierte Ausführungszeit des ausgewählten Ausführungstyps pro Sekunde.|  
|**Aktuelle Ausführungen**|Anzahl der aktuellen Ausführungen des ausgewählten Ausführungstyps.|  
|**Gestartete Ausführungen pro Sekunde**|Anzahl der pro Sekunde gestarteten Ausführungen des ausgewählten Ausführungstyps.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
