---
title: Tools für die Leistungsüberwachung und -optimierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tools [SQL Server], monitoring performance
- monitoring server performance [SQL Server], tools
- monitoring performance [SQL Server], tools
- database performance [SQL Server], tools
- tuning databases [SQL Server], tools
- database monitoring [SQL Server], tools
- performance [SQL Server], monitoring tools
- server performance [SQL Server], tools
ms.assetid: 31529dfe-68e7-49f7-b3c2-39fcecf33a95
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 179944412ed72bc0055bf5c47b788a3a929e9844
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150838"
---
# <a name="performance-monitoring-and-tuning-tools"></a>Tools für die Leistungsüberwachung und -optimierung
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt einen umfassenden Satz von Tools für die Überwachung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ereignissen in und für die Optimierung des physischen Daten bankentwurfs bereit. Das richtige Tool ergibt sich aus der Art der gewünschten Überwachung oder Optimierung sowie aus den jeweils zu überwachenden Ereignissen.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stehen die folgenden Tools zur Überwachung und Optimierung zur Verfügung:  
  
|Tool|BESCHREIBUNG|  
|----------|-----------------|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|
  [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] verfolgt Engine-Prozessereignisse wie das Starten eines Batches oder einer Transaktion. So können Sie die Server- und Datenbankaktivität überwachen (z.B. Deadlocks, schwerwiegende Fehler oder Anmeldeaktivität). Sie können [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] -Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle oder -Datei aufzeichnen und später analysieren oder die aufgezeichneten Ereignisse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schrittweise wiedergeben, um den genauen Ablauf anzuzeigen.|  
|[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay können Ablauf Verfolgungs Daten mithilfe mehrerer Computer wiedergeben und eine Unternehmens wichtige Arbeitsauslastung simulieren.|  
|[Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)|Der Systemmonitor verfolgt hauptsächlich die Ressourcennutzung, wie die Anzahl der verwendeten Seitenanforderungen des Puffer-Managers. So können Sie die Serverleistung und Aktivität mit vordefinierten Objekten und Leistungsindikatoren überwachen oder benutzerdefinierte Leistungsindikatoren zum Überwachen von Ereignissen verwenden. Der Systemmonitor erfasst Leistungsindikatoren und Raten für die Ereignisse anstelle von Daten über die Ereignisse (z. B. Speicherauslastung, Anzahl der aktiven Transaktionen, Anzahl der blockierten Sperren oder CPU-Aktivität). Für bestimmte Leistungsindikatoren können Schwellwerte festgelegt werden, um Warnungen zu generieren, durch die Operatoren benachrichtigt werden.<br /><br /> Der Systemmonitor kann unter den Betriebssystemen Microsoft Windows Server und Windows ausgeführt werden. Hiermit können Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (remotely oder lokal) unter Windows NT 4.0 (oder höher) überwachen.<br /><br /> Der wichtigste Unterschied zwischen [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] und dem Systemmonitor liegt darin, dass bei [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] die Datenbank-Engine-Ereignisse verfolgt werden, im Systemmonitor dagegen die Ressourcennutzung im Zusammenhang mit Serverprozessen.|  
|[Öffnen des Aktivitätsmonitors &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|Der Aktivitätsmonitor von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eignet sich für eine Ad-hoc-Ansicht der aktuellen Aktivität. Außerdem werden darin die folgenden Informationen grafisch angezeigt:<br /><br /> Prozesse, die unter einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden<br /><br /> Gesperrte Prozesse<br /><br /> Sperren<br /><br /> Benutzeraktivität|  
|[SQL-Ablaufverfolgung](../sql-trace/sql-trace.md)|
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] gespeicherte Prozeduren, mit denen die Ablaufverfolgung erstellt, gefiltert und definiert wird:<br /><br /> [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)<br /><br /> [sp_trace_generateevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)<br /><br /> [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)<br /><br /> [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)<br /><br /> [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|  
|Fehlerprotokolle|Das Windows-Anwendungsereignisprotokoll liefert ein Gesamtbild der Ereignisse in den Betriebssystemen Windows Server und Windows insgesamt sowie der Ereignisse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent und der Volltextsuche. Hier sind Informationen zu Ereignissen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthalten, die anderweitig nicht zur Verfügung stehen. Sie können die Informationen im Fehlerprotokoll für die Problembehandlung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nutzen.|  
|[Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)|Die folgenden im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System gespeicherten Prozeduren bilden eine leistungsfähige Alternative für zahlreiche Überwachungsaufgaben:<br /><br /> [sp_who &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql): <br />                    Meldet Momentaufnahme-Informationen zu aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Benutzern und -Prozessen, einschließlich der derzeit ausgeführten Anweisung und der Information, ob die Anweisung blockiert wurde.<br /><br /> [sp_lock &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-lock-transact-sql): meldet Momentaufnahme Informationen zu sperren, einschließlich der Objekt-ID, der Index-ID, des Sperrentyps und des Typs oder der Ressource, auf die die Sperre angewendet wird.<br /><br /> [sp_spaceused &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql): zeigt eine Schätzung der aktuellen Menge an Speicherplatz an, die von einer Tabelle (oder einer gesamten Datenbank) belegt wird.<br /><br /> [sp_monitor &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-monitor-transact-sql): zeigt Statistiken an, einschließlich der CPU-Auslastung, der e/a-Nutzung und der Zeitspanne, die seit der letzten Ausführung **sp_monitor** in den Leerlauf versetzt wurde.|  
|[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)|DBCC-Anweisungen (Database Consistency Checker, Datenbankkonsistenzprüfer) ermöglichen die Überprüfung der Leistungsstatistik und der logischen und physischen Konsistenz einer Datenbank.|  
|[Integrierte Funktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions)|Integrierte Funktionen zeigen Momentaufnahmestatistiken über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Aktivität seit dem Starten des Servers an, die in vordefinierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Leistungsindikatoren gespeichert werden. Beispielsweise enthält **@@CPU_BUSY ** den Zeitraum, in dem die CPU Code ausgeführt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat. **@@CONNECTIONS ** enthält die Anzahl der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungen oder Verbindungsversuche. und **@@PACKET_ERRORS ** enthält die Anzahl der Netzwerkpakete, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bei Verbindungen auftreten.|  
|[Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)|Ablaufverfolgungsflags zeigen Informationen zu einer bestimmten Aktivität im Server an und werden für die Diagnose von Problemen oder Leistungskriterien (z. B. mehrere Deadlocks in Folge) verwendet.|  
|[Datenbankoptimierungsratgeber](database-engine-tuning-advisor.md)|Der Datenbankoptimierungsratgeber analysiert die Leistungsauswirkungen von [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen, die auf die Datenbanken für die Optimierung ausgeführt werden. Der Datenbankoptimierungsratgeber bietet Empfehlungen zum Hinzufügen, Entfernen oder Ändern von Indizes, indizierten Sichten und Partitionierungen.|  
  
## <a name="choosing-a-monitoring-tool"></a>Auswählen von Überwachungstools  
 Die Wahl eines geeigneten Überwachungstools hängt von der Art des Ereignisses und der Aktivität, die überwacht werden sollen, ab.  
  
|Ereignis oder Aktivität|SQL Server Profiler|Distributed Replay|Systemmonitor|Aktivitätsmonitor|Transact-SQL|Fehlerprotokolle|  
|-----------------------|-------------------------|------------------------|--------------------|----------------------|-------------------|----------------|  
|Trendanalyse|Ja||Ja||||  
|Wiedergeben aufgezeichneter Ereignisse|Ja (von einem einzelnen Computer)|Ja (von mehreren Computern)|||||  
|Ad-hoc-Überwachung|Ja|||Ja|Ja|Ja|  
|Generieren von Warnungen|||Ja||||  
|Grafische Benutzeroberfläche|Ja||Ja|Ja||Ja|  
|Verwendung im Rahmen von benutzerdefinierten Anwendungen|Ja<sup>1</sup>||||Ja||  
  
 <sup>1</sup> mithilfe [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] gespeicherter System Prozeduren.  
  
## <a name="windows-monitoring-tools"></a>Windows-Überwachungstools  
 Die Windows-Betriebssysteme sowie Windows Server 2003 enthalten außerdem die folgenden Überwachungstools:  
  
|Tool|BESCHREIBUNG|  
|----------|-----------------|  
|Task-Manager|Zeigt eine vergleichende Übersicht über die Prozesse und Anwendungen an, die im System ausgeführt werden.|  
|Netzwerkmonitor-Agent|Überwacht die Netzwerkbelastung.|  
  
 Weitere Informationen zu den Windows-Betriebssystemen oder zu den Windows-Server-Tools finden Sie in der Windows-Dokumentation.  
  
  
