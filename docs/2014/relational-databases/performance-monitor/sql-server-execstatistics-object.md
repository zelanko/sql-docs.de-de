---
title: SQL Server, Ausführungsstatistik-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 762e0b77545e21cc07a6aec026e19f4b59557e43
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067136"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, Ausführungsstatistik-Objekt
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
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
