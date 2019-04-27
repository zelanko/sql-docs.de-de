---
title: Blocked Process Report-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Blocked Process Report event class
ms.assetid: e8acb408-938d-4b36-81dd-04f087410cc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c3061794a565c4397bbf949211774306c9acebf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62664266"
---
# <a name="blocked-process-report-event-class"></a>Blocked Process Report-Ereignisklasse
  Die **Blocked Process Report** -Ereignisklasse zeigt an, dass ein Task länger als die angegebene Zeitspanne blockiert wurde. Diese Ereignisklasse schließt keine Systemtasks oder Tasks ein, die auf Ressourcen warten, für die keine Deadlocks erkannt werden können.  
  
 Sie können den Schwellenwert und die Häufigkeit der Berichtgenerierung mit dem Befehl **sp_configure** konfigurieren, indem Sie die Option **Schwellenwert für blockierte Prozesse** (in Sekunden) festlegen. Standardmäßig werden für blockierte Prozesse keine Berichte erstellt. Weitere Informationen zum Einrichten des **Schwellenwerte für blockierte Prozesse** finden Sie unter [Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption)](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md).  
  
 Weitere Informationen zum Filtern von Daten, die von der Ereignisklasse **Blocked Process Report** zurückgegeben werden, finden Sie unter [Filtern von Ereignissen in einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md), [Festlegen eines Ablaufverfolgungsfilters &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) oder [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql).  
  
## <a name="blocked-process-report-event-class-data-columns"></a>Blocked Process Report (Ereignisklassen-Datenspalten)  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Die ID der Datenbank, in der die Sperre eingerichtet wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**Dauer**|**bigint**|Die Zeitdauer (in Millisekunden), für die der Prozess blockiert wurde.|13|Ja|  
|**EndTime**|**datetime**|Der Zeitpunkt, zu dem das Ereignis beendet wurde. Diese Spalte wird für Startereignisklassen, wie z. B. **SQL:BatchStarting** oder **SP:Starting**, nicht aufgefüllt.|15|Ja|  
|**EventClass**|**int**|Ereignistyp = 137.|27|Nein|  
|**EventSequence**|**int**|Die Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**IndexID**|**int**|ID für den Index des Objekts, das von dem Ereignis betroffen ist. Sie können die Index-ID für ein Objekt mithilfe der **indid** -Spalte der **sysindexes** -Systemtabelle ermitteln.|24|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginSid**|**image**|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Dieses Ereignis wird immer vom Systemthread gemeldet. IsSystem = 1; SID = sa.|41|Ja|  
|**Mode**|**int**|Der Status, der von einem Ereignis empfangen oder angefordert wird.<br /><br /> 0=NULL<br /><br /> 1=Sch-S<br /><br /> 2=Sch-M<br /><br /> 3 = S<br /><br /> 4 = U<br /><br /> 5 = X<br /><br /> 6 = IS<br /><br /> 7 = IU<br /><br /> 8 = IX<br /><br /> 9 = SIU<br /><br /> 10 = SIX<br /><br /> 11 = UIX<br /><br /> 12 = BU<br /><br /> 13 = RangeS-S<br /><br /> 14 = RangeS-U<br /><br /> 15 = RangeI-N<br /><br /> 16 = RangeI-S<br /><br /> 17=RangeI-U<br /><br /> 18=RangeI-X<br /><br /> 19=RangeX-S<br /><br /> 20=RangeX-U<br /><br /> 21=RangeX-X|32|Ja|  
|**ObjectID**|**int**|Die vom System zugewiesene ID des Objekts, für das die Sperre abgerufen wurde (sofern verfügbar und anwendbar).|22|Ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26||  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung ursprünglich begonnen hat. Wenn Sie z. B. mit Login1 eine Verbindung zu SQL Server herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**TextData**|**ntext**|Textwert, der von der Ereignisklasse abhängt, die in der Ablaufverfolgung aufgezeichnet wurde.|1|Ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
