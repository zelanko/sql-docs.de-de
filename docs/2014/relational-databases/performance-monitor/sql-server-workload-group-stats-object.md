---
title: SQL Server, 'Statistiken für Arbeitsauslastungsgruppen'-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 06651ffcfee30d538c8ede09914133a2ed818b3b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151100"
---
# <a name="sql-server-workload-group-stats-object"></a>SQL Server, 'Statistiken für Arbeitsauslastungsgruppen'-Objekt
  Das SQLServer:Statistiken für Arbeitsauslastungsgruppen-Objekt enthält Leistungsindikatoren, die Informationen zur Ressourcenkontrollen-Arbeitsauslastungsgruppenstatistik zurückgeben.  
  
 Jede aktive Arbeitsauslastungsgruppe erstellt eine Instanz des Leistungsobjekts SQLServer:Statistiken für Arbeitsauslastungsgruppen, wobei der Name der Instanz dem Namen der Arbeitsauslastungsgruppe in der Ressourcenkontrolle entspricht. In der folgenden Tabelle sind die für diese Instanz unterstützten Leistungsindikatoren beschrieben.  
  
|Indikatorname|Description|  
|------------------|-----------------|  
|Anforderungen in der Warteschlange|Die aktuelle Anzahl der Anforderungen in der Warteschlange, die darauf warten, abgerufen zu werden. Diese Anzahl kann ungleich 0 (null) sein, wenn eine Einschränkung angewandt wird, nachdem der Grenzwert GROUP_MAX_REQUESTS erreicht wurde.|  
|Aktive Anforderungen|Die Anzahl von Anforderungen, die aktuell in dieser Arbeitsauslastungsgruppe ausgeführt werden. Diese Anzahl sollte der Anzahl von Zeilen entsprechen, die anhand der Gruppen-ID aus sys.dm_exec_requests herausgefiltert wird.|  
|Abgeschlossene Anforderungen/Sekunde|Die Anzahl der in dieser Arbeitsauslastungsgruppe abgeschlossenen Anforderungen. Diese Anzahl ist kumulativ.|  
|CPU-Verwendung in %|Die von allen Anforderungen in dieser Arbeitsauslastungsgruppe belegte CPU-Bandbreite, gemessen relativ zum Computer und normalisiert auf alle CPUs im System. Dieser Wert ändert sich, wenn sich die für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess verfügbare CPU-Leistung ändert. Der Wert wird auf die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess empfangenen Elemente normalisiert.|  
|Maximale CPU-Zeit für Anforderungen (ms)|Die maximal von einer aktuell in der Arbeitsauslastungsgruppe ausgeführten Anforderung belegte CPU-Zeit in Millisekunden.|  
|Blockierte Anforderungen|Die aktuelle Anzahl blockierter Anforderungen in der Arbeitsauslastungsgruppe. Mit diesem Wert können Arbeitsauslastungseigenschaften ermittelt werden.|  
|Reduzierte Arbeitsspeicherzuweisungen/Sekunde|Die Anzahl von Abfragen, die nicht die optimale Menge an Arbeitsspeicherzuweisungen pro Sekunde erhalten.|  
|Maximale Arbeitsspeicherzuweisung für Anforderungen (KB)|Der maximale Wert der Arbeitsspeicherzuweisung für eine Abfrage in Kilobyte (KB).|  
|Abfrageoptimierungen/Sekunde|Die Anzahl von Abfrageoptimierungen, die pro Sekunde in dieser Arbeitsauslastungsgruppe stattgefunden haben. Mit diesem Wert können Arbeitsauslastungseigenschaften ermittelt werden.|  
|Suboptimale Pläne/Sekunde|Die Anzahl von suboptimalen Plänen, die pro Sekunde in dieser Arbeitsauslastungsgruppe erzeugt werden.|  
|Aktive parallele Threads|Die aktuelle Anzahl belegter paralleler Threads.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, 'Statistiken für Ressourcenpools'-Objekt](sql-server-resource-pool-stats-object.md)   
 [Ressourcenkontrolle](../resource-governor/resource-governor.md)  
  
  
