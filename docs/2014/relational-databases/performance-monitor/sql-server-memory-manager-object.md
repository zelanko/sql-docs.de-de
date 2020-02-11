---
title: SQL Server, Speicher-Manager-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Manager
- Memory Manager object
ms.assetid: dbf49000-eeb0-4e9c-a361-5092363920dc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 822cb494b7dce35ea965a2a53cab36785a38bc75
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250631"
---
# <a name="sql-server-memory-manager-object"></a>SQL Server, Speicher-Manager-Objekt
  Das **Speicher-Manager** -Objekt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Microsoft stellt Leistungsindikatoren zum Überwachen der gesamten Server Speicherauslastung bereit. Das Überwachen der gesamten Speicherauslastung des Servers zur Messung der Benutzeraktivität und der Ressourcennutzung kann Ihnen dabei helfen, Leistungsengpässe zu erkennen. Durch Überwachen des Arbeitsspeichers, der von einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird, können Sie Folgendes ermitteln:  
  
-   Ob es zu Engpässen kommt, da nicht genügend Arbeitsspeicher vorhanden ist, um Daten, auf die häufig zugegriffen wird, im Cache zu speichern. In diesem Fall muss [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten vom Datenträger abrufen.  
  
-   Ob die Abfrageleistung durch Hinzufügen von Arbeitsspeicher oder durch Zuordnen von zusätzlichem Arbeitsspeicher für den Datencache bzw. für interne Strukturen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbessert werden kann.  
  
## <a name="memory-manager-counters"></a>Speicher-Manager-Leistungsindikatoren  
 In dieser Tabelle werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Speicher-Manager** beschrieben.  
  
|Speicher-Manager-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|----------------------------------------|-----------------|  
|**Verbindungs Speicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für die Aufrechterhaltung von Verbindungen verwendet.|  
|**Datenbank-Cache Speicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server derzeit für den Datenbankseitencache verwendet.|  
|**Freier Speicher (KB)**|Gibt den Umfang des zugesicherten Arbeitsspeichers an, der derzeit nicht vom Server verwendet wird.|  
|**Zugewiesener Arbeitsbereichs Speicher (KB)**|Gibt den Gesamtumfang des Arbeitsspeichers an, der derzeit dem Ausführen von Prozessen, z. B. Hash-, Sortier-, Massenkopier- und Indexerstellungsvorgängen, zugewiesen ist.|  
|**Sperr Blöcke**|Gibt die aktuelle Anzahl der Sperrblöcke an, die auf dem Server verwendet werden. Wird regelmäßig aktualisiert. Ein Sperrblock stellt eine einzelne gesperrte Ressource, wie z. B. eine Tabelle, Seite oder Zeile, dar.|  
|**Zugeordnete Sperr Blöcke**|Gibt die aktuelle Anzahl der zugeordneten Sperrblöcke an. Beim Starten des Servers hängt die Anzahl der zugeordneten Sperrblöcke plus die Anzahl der zugeordneten Sperrenbesitzerblöcke von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-Konfigurationsoption von** ab. Wenn mehr Sperrblöcke benötigt werden, steigt der Wert.|  
|**Sperr Speicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für Sperren verwendet.|  
|**Sperrenbesitzerblöcke**|Gibt die Anzahl der Sperrenbesitzerblöcke an, die zurzeit auf dem Server verwendet werden. Wird regelmäßig aktualisiert. Ein Sperrenbesitzerblock stellt den Besitz einer Sperre für ein Objekt durch einen einzelnen Thread dar. Wenn also drei Threads jeweils über eine freigegebene Sperre (S) für eine Seite verfügen, liegen drei Sperrenbesitzerblöcke vor.|  
|**Zugeordnete Sperrenbesitzerblöcke**|Gibt die aktuelle Anzahl der zugeordneten Sperrenbesitzerblöcke an. Beim Starten des Servers hängt die Anzahl der zugeordneten Sperrenbesitzerblöcke und die Anzahl der zugeordneten Sperrblöcke von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-Konfigurationsoption von** ab. Wenn mehr Sperrenbesitzerblöcke benötigt werden, steigt der Wert dynamisch an.|  
|**Maximaler Arbeitsbereichs Speicher (KB)**|Gibt den maximalen Umfang des Arbeitsspeichers an, der für das Ausführen von Prozessen, z. B. Hash-, Sortier,- Massenkopier- und Indexerstellungsvorgängen, zur Verfügung steht.|  
|**Ausstehende Arbeitsspeicher Zuweisungen**|Gibt die Gesamtanzahl der Prozesse an, die erfolgreich eine Zuweisung für Arbeitsbereichsspeicher erhalten haben.|  
|**Ausstehende Arbeitsspeicher Zuweisungen**|Gibt die Gesamtanzahl der Prozesse an, die auf eine Zuweisung von Arbeitsbereichsspeicher warten.|  
|**Optimiererspeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für die Abfrageoptimierung verwendet.|  
|**Reservierter Server Arbeitsspeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server für die zukünftige Verwendung reserviert hat. Dieser Leistungsindikator gibt den derzeit nicht verwendeten Umfang des ursprünglich zugewiesenen Arbeitsspeichers an, der in **Erteilter Arbeitsbereichsspeicher (KB)** angezeigt wird.|  
|**SQL-Cache Speicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für den dynamischen SQL-Cache verwendet.|  
|**Gestohlener Server Arbeitsspeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server derzeit für andere Zwecke als Datenbankseiten verwendet.|  
|**Ziel Server Arbeitsspeicher (KB)**|Gibt den idealen Umfang des Arbeitsspeichers an, den der Server belegen kann.|  
|**Server Arbeitsspeicher Gesamt (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server mit dem Speicher-Manager zugesichert hat.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, Puffer-Manager-Objekt](sql-server-buffer-manager-object.md)   
 [sys. dm_os_performance_counters &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
