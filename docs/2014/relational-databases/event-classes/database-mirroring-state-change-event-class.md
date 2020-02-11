---
title: Database Mirroring State Change-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- database mirroring [SQL Server], event notifications
- Database Mirroring State Change event class
ms.assetid: f936a99e-2a81-4768-8177-5c969bbe2e04
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f81b196ee1b686fbe2dd3563f694411a0e00d962
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62663044"
---
# <a name="database-mirroring-state-change-event-class"></a>Database Mirroring State Change-Ereignisklasse
  Die **Daten Bank Spiegelungs Status Änderungs** -Ereignisklasse zeigt an, wenn sich der Status einer gespiegelten Datenbank ändert. Schließen Sie diese Ereignisklasse in Ablaufverfolgungen ein, von denen die Zustände gespiegelter Datenbanken überwacht werden.  
  
 Wenn die **Database Mirroring State Change** -Ereignisklasse in einer Ablaufverfolgung eingeschlossen ist, ist der damit verbundene Verwaltungsaufwand gering. Der Verwaltungsaufwand wächst möglicherweise mit der Größe der gespiegelten Datenbanken.  
  
## <a name="data-database-mirroring-state-change-event-class-data-columns"></a>Data Database Mirroring State Change (Ereignisklasse-Datenspalten)  
  
|Name der Datenspalte|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die use *Database* -Anweisung angegeben wurde, oder die Standarddatenbank, wenn für eine bestimmte Instanz keine use *Database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]zeigt den Namen der Datenbank an, wenn die **ServerName-Datenspalte** in der Ablauf Verfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|**nvarchar**|Der Name der gespiegelten Datenbank.|35|Ja|  
|**EventClass**|**int**|Ereignistyp = 167.|27|Nein|  
|**EventSequence**|**int**|Die Sequenz der Ereignisklasse im Batch.|51|Nein|  
|**IntegerData**|**int**|Die ID des vorherigen Status.|25|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginSID**|**Klang**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**RequestId**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|**Servername**|**nvarchar**|Name der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**Ausführen**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. b. mithilfe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Login1 eine Verbindung mit herstellen und eine Anweisung als Login2 ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|**State**|**int**|Die neue Spiegelungsstatus-ID:<br /><br /> 0 = Nullbenachrichtigung<br /><br /> 1 = Synchronisierter Prinzipal mit Zeugen<br /><br /> 2 = Synchronisierter Prinzipal ohne Zeugen<br /><br /> 3 = Synchronisierter Spiegel mit Zeugen<br /><br /> 4 = Synchronisierter Spiegel ohne Zeugen<br /><br /> 5 = Verbindung zum Prinzipal verloren<br /><br /> 6 = Verbindung zum Spiegel verloren<br /><br /> 7 = Manuelles Failover<br /><br /> 8 = Automatisches Failover<br /><br /> 9 = Spiegelung angehalten<br /><br /> 10 = Kein Quorum<br /><br /> 11 = Spiegel wird synchronisiert<br /><br /> 12 = Ausgeführter Prinzipal offen gelegt|30|Ja|  
|**TextData**|**ntext**|Die Beschreibung der Statusänderung.|1|Ja|  
|**TransactionId**|**BIGINT**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
