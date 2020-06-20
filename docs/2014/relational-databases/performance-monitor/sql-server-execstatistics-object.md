---
title: SQL Server, Ausführungsstatistik-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3697dcc854919699cea8d48087ca3a1f69f66c13
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066971"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, Ausführungsstatistik-Objekt
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
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
