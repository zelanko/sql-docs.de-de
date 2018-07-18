---
title: SQL Server, 'Statistiken für Ressourcenpools'-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Reosurce Pool Stats object
- 'SQLServer: Resource Pool Stats object'
ms.assetid: bb46e029-fcf9-4aeb-a066-be41e7668fb9
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a996ff8faa6fa1bf4f907282462b4e6df6598afd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252122"
---
# <a name="sql-server-resource-pool-stats-object"></a>SQL Server, 'Statistiken für Ressourcenpools'-Objekt
  Das SQLServer:Statistiken für Ressourcenpools-Objekt enthält Leistungsindikatoren, die Informationen zur Ressourcenkontrollen-Poolstatistik zurückgeben.  
  
 Jeder aktive Ressourcenpool erstellt eine Instanz des Leistungsobjekts SQLServer:Statistiken für Ressourcenpools, wobei der Name der Instanz dem Namen des Ressourcenpools in der Ressourcenkontrolle entspricht. In der folgenden Tabelle sind die für diese Instanz unterstützten Leistungsindikatoren beschrieben.  
  
|Indikatorname|Description|  
|------------------|-----------------|  
|CPU-Verwendung in %|Die von allen Anforderungen in allen Arbeitsauslastungsgruppen dieses Pools belegte CPU-Bandbreite. Dieser Wert wird relativ zum Computer gemessen und auf alle CPUs im System normalisiert. Dieser Wert ändert sich, wenn sich die für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess verfügbare CPU-Leistung ändert. Der Wert wird auf die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess empfangenen Elemente normalisiert.|  
|Ziel-CPU-Verwendung in %|Der Zielwert für die CPU-Auslastung in Prozent für den Ressourcenpool. Dieser Wert basiert auf den Konfigurationseinstellungen für den Ressourcenpool und der Systemauslastung.|  
|Auswirkungen der CPU-Kontrolle in %|Die Auswirkungen der Ressourcenkontrolle auf den Ressourcenpool. Wird wie folgt berechnet: (CPU-Verwendung in %) / (CPU-Verwendung in % ohne Ressourcenkontrolle).|  
|Speicherziel für Kompilierung (KB)|Das aktuelle Speicherbrokerziel für Abfragekompilierungen in Kilobyte (KB).|  
|Cachespeicherziel (KB)|Das aktuelle Speicherbrokerziel für den Cache in Kilobyte (KB).|  
|Speicherziel für Abfrageausführung (KB)|Das aktuelle Speicherbrokerziel für die Arbeitsspeicherzuweisung der Abfrageausführung in Kilobyte (KB). Diese Information ist auch in [sys.dm_exec_query_memory_grants](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql)verfügbar.|  
|Arbeitsspeicherzuweisungen/Sekunde|Die Anzahl von Arbeitsspeicherzuweisungen, die pro Sekunde in diesem Ressourcenpool ausgeführt werden.|  
|Anzahl aktiver Arbeitsspeicherzuweisungen|Die aktuelle Gesamtanzahl von Arbeitsspeicherzuweisungen. Diese Information ist auch in [sys.dm_exec_query_memory_grants](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql)verfügbar.|  
|Timeouts für Arbeitsspeicherzuweisungen/Sekunde|Die Anzahl von Timeouts für Arbeitsspeicherzuweisungen pro Sekunde.|  
|Menge aktiver Arbeitsspeicherzuweisungen (KB)|Der aktuell zugewiesene Gesamtspeichers in Kilobyte (KB). Diese Information ist auch in [sys.dm_exec_query_resource_semaphores](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql) verfügbar.|  
|Anzahl ausstehender Arbeitsspeicherzuweisungen|Die Anzahl von Anforderungen in der Warteschlange, die auf Arbeitsspeicherzuweisungen warten. Diese Information ist auch in [sys.dm_exec_query_resource_semaphores](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql)verfügbar.|  
|Maximaler Arbeitsspeicher (KB)|Die maximale Menge an Arbeitsspeicher in Kilobyte (KB), die der Ressourcenpool basierend auf den Einstellungen für den Ressourcenpool und dem Serverstatus aufweisen kann.|  
|Verwendeter Arbeitsspeicher (KB)|Die im Ressourcenpool verwendete Arbeitsspeichermenge in Kilobyte (KB).|  
|Zielspeicher (KB)|Der Zielarbeitsspeicher in Kilobyte (KB), die der Ressourcenpool, auf Grundlage der Einstellungen für den Ressourcenpool und des Serverstatus, abzurufen versucht.|  
|E/A-Lesevorgänge von Datenträger/s|Die Anzahl der Lesevorgänge vom Datenträger in der letzten Sekunde.|  
|Gedrosselte E/A-Lesevorgänge auf Datenträger/s|Die Anzahl der in der letzten Sekunde gedrosselten Lesevorgänge.|  
|Vom Datenträger gelesene Bytes/s|Die Anzahl der in der letzten Sekunde vom Datenträger gelesenen Bytes.|  
|Durchschnittl. Datenträgerzeit (ms)|Die durchschnittliche Zeit (in Millisekunden) eines Lesevorgangs vom Datenträger.|  
|E/A-Schreibvorgänge auf Datenträger/s|Die Anzahl der Schreibvorgänge auf den Datenträger in der letzten Sekunde.|  
|Gedrosselte E/A-Schreibvorgänge auf Datenträger/s|Die Anzahl der in der letzten Sekunde gedrosselten Schreibvorgänge.|  
|Auf den Datenträger geschriebene Bytes/s|Die Anzahl der in der letzten Sekunde auf den Datenträger geschriebenen Bytes.|  
|Durchschnittl. Datenträgerzeit (ms)/Schreiben E/A|Die durchschnittliche Zeit (in Millisekunden) eines Schreibvorgangs auf den Datenträger.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, 'Statistiken für Arbeitsauslastungsgruppen'-Objekt](sql-server-workload-group-stats-object.md)   
 [Ressourcenkontrolle](../resource-governor/resource-governor.md)  
  
  
