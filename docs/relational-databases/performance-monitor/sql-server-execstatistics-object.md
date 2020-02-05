---
title: SQL Server, Ausführungsstatistik-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: c1dad11470d76b0759c7c0b1d4f26c84bfb67a45
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68093584"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, Ausführungsstatistik-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das **SQLServer:ExecStatistics** -Objekt in Microsoft SQL Server stellt Leistungsindikatoren zum Überwachen verschiedener Vorgänge zur Verfügung.  
  
 In dieser Tabelle werden die **Exec Statistics** -Leistungsindikatoren von SQL Server beschrieben.  
  
|Exec Statistics-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|-----------------------------------------|-----------------|  
|**Verteilte Abfrage**|Für die Ausführung von verteilten Abfragen wichtige Statistiken.|  
|**DTC-Aufrufe**|Für die Ausführung von DTC-Aufrufen wichtige Statistiken.|  
|**Erweiterte Prozeduren**|Für die Ausführung von erweiterten Prozeduren wichtige Statistiken.|  
|**OLE DB-Aufrufe**|Für die Ausführung von OLE DB-Aufrufen wichtige Statistiken.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Element|BESCHREIBUNG|  
|----------|-----------------|  
|**Durchschnittliche Ausführungszeit (ms)**|Durchschnittliche Ausführungszeit des ausgewählten Ausführungstyps.|  
|**Kumulierte Ausführungszeit (ms) pro Sekunde**|Aggregierte Ausführungszeit des ausgewählten Ausführungstyps pro Sekunde.|  
|**Aktuelle Ausführungen**|Anzahl der aktuellen Ausführungen des ausgewählten Ausführungstyps.|  
|**Gestartete Ausführungen pro Sekunde**|Anzahl der pro Sekunde gestarteten Ausführungen des ausgewählten Ausführungstyps.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
