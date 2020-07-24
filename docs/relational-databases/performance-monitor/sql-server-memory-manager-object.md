---
title: SQL Server, Speicher-Manager-Objekt | Microsoft-Dokumentation
description: Hier lernen Sie das „Speicher-Manager“-Objekt kennen, das Leistungsindikatoren bereitstellt, mit denen Sie die gesamte Speicherauslastung des Servers in SQL Server überwachen können.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Manager
- Memory Manager object
ms.assetid: dbf49000-eeb0-4e9c-a361-5092363920dc
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: ad1317d52ca3075a5726e528216f569bd91c2a15
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458796"
---
# <a name="sql-server-memory-manager-object"></a>SQL Server, Speicher-Manager-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Das **Speicher-Manager** -Objekt in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Leistungsindikatoren bereit, mit denen Sie die gesamte Speicherauslastung des Servers überwachen können. Das Überwachen der gesamten Speicherauslastung des Servers zur Messung der Benutzeraktivität und der Ressourcennutzung kann Ihnen dabei helfen, Leistungsengpässe zu erkennen. Durch Überwachen des Arbeitsspeichers, der von einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird, können Sie Folgendes ermitteln:  
  
-   Ob es zu Engpässen kommt, da nicht genügend Arbeitsspeicher vorhanden ist, um Daten, auf die häufig zugegriffen wird, im Cache zu speichern. In diesem Fall muss [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten vom Datenträger abrufen.  
  
-   Ob die Abfrageleistung durch Hinzufügen von Arbeitsspeicher oder durch Zuordnen von zusätzlichem Arbeitsspeicher für den Datencache bzw. für interne Strukturen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbessert werden kann.  
  
## <a name="memory-manager-counters"></a>Speicher-Manager-Leistungsindikatoren  
 In dieser Tabelle werden die Leistungsindikatoren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-**Speicher-Managers** beschrieben.  
  
|Speicher-Manager-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|----------------------------------------|-----------------|  
|**Verbindungsspeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für die Aufrechterhaltung von Verbindungen verwendet.|  
|**Datenbankcachespeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server derzeit für den Datenbankseitencache verwendet.|  
|**Externer Speichernutzen**| Eine interne Schätzung des Leistungsnutzens durch das Hinzufügen von Speicher zu einem bestimmten Cache. Der Nutzen wird von der Engine hinzugefügt, um den Speicherverbrauch zwischen Caches auszugleichen und ist nützlich für den Support, wenn Problembehandlung in Fällen mit unerwarteter Vergrößerung des Caches erforderlich ist. Der Wert wird als Integer basierend auf einer internen Berechnung dargestellt. | 
|**Freier Arbeitsspeicher (KB)**|Gibt den Umfang des zugesicherten Arbeitsspeichers an, der derzeit nicht vom Server verwendet wird.|  
|**Zugewiesener Arbeitsbereichsspeicher (KB)**|Gibt den Gesamtumfang des Arbeitsspeichers an, der derzeit dem Ausführen von Prozessen, z. B. Hash-, Sortier-, Massenkopier- und Indexerstellungsvorgängen, zugewiesen ist.|  
|**Sperrblöcke**|Gibt die aktuelle Anzahl der Sperrblöcke an, die auf dem Server verwendet werden. Wird regelmäßig aktualisiert. Ein Sperrblock stellt eine einzelne gesperrte Ressource, wie z. B. eine Tabelle, Seite oder Zeile, dar.|  
|**Zugeordnete Sperrblöcke**|Gibt die aktuelle Anzahl der zugeordneten Sperrblöcke an. Beim Starten des Servers hängen die Anzahl der zugeordneten Sperrblöcke und die Anzahl der zugeordneten Sperrenbesitzerblöcke von der Konfigurationsoption **Sperren** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab. Wenn mehr Sperrblöcke benötigt werden, steigt der Wert.|  
|**Sperrspeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für Sperren verwendet.|  
|**Sperrenbesitzerblöcke**|Gibt die Anzahl der Sperrenbesitzerblöcke an, die zurzeit auf dem Server verwendet werden. Wird regelmäßig aktualisiert. Ein Sperrenbesitzerblock stellt den Besitz einer Sperre für ein Objekt durch einen einzelnen Thread dar. Wenn also drei Threads jeweils über eine freigegebene Sperre (S) für eine Seite verfügen, liegen drei Sperrenbesitzerblöcke vor.|  
|**Zugeordnete Sperrenbesitzerblöcke**|Gibt die aktuelle Anzahl der zugeordneten Sperrenbesitzerblöcke an. Beim Starten des Servers hängen die Anzahl der zugeordneten Sperrenbesitzerblöcke und die Anzahl der zugeordneten Sperrblöcke von der Konfigurationsoption **Sperren** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab. Wenn mehr Sperrenbesitzerblöcke benötigt werden, steigt der Wert dynamisch an.|  
|**Protokollpoolspeicher (KB)**|Die Gesamtkapazität des dynamischen Speichers, den der Server für den Protokollpool verwendet.| 
|**Maximaler Arbeitsbereichsspeicher (KB)**|Gibt den maximalen Umfang des Arbeitsspeichers an, der für das Ausführen von Prozessen, z. B. Hash-, Sortier,- Massenkopier- und Indexerstellungsvorgängen, zur Verfügung steht.|  
|**Ausstehende Speicherzuweisungen**|Gibt die Gesamtanzahl der Prozesse an, die erfolgreich eine Zuweisung für Arbeitsbereichsspeicher erhalten haben.|  
|**Ausstehende Speicherzuweisungen**|Gibt die Gesamtanzahl der Prozesse an, die auf eine Zuweisung von Arbeitsbereichsspeicher warten.|  
|**Optimiererspeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für die Abfrageoptimierung verwendet.|  
|**Reservierter Serverarbeitsspeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server für die zukünftige Verwendung reserviert hat. Dieser Leistungsindikator gibt den derzeit nicht verwendeten Umfang des ursprünglich zugewiesenen Arbeitsspeichers an, der in **Erteilter Arbeitsbereichsspeicher (KB)** angezeigt wird.|  
|**SQL-Cachespeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für den dynamischen SQL-Cache verwendet.|  
|**Gestohlener Serverarbeitsspeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server derzeit für andere Zwecke als Datenbankseiten verwendet.|  
|**Zielserverspeicher (KB)**|Gibt den idealen Umfang des Arbeitsspeichers an, den der Server belegen kann.|  
|**Serverspeicher gesamt (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server mit dem Speicher-Manager zugesichert hat.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, Puffer-Manager-Objekt](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
[sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
