---
title: Degree of Parallelism (7.0 Insert)-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Degree of Parallelism event class
ms.assetid: 6753ef30-890f-47a3-b0b6-8abb184e1d83
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03f723987ebce872068a128bec80be6bb8cfe10b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162935"
---
# <a name="degree-of-parallelism-70-insert-event-class"></a>Degree of Parallelism (7.0 Insert)-Ereignisklasse
  Die Ereignisklasse **Degree of Parallelism (7.0 Insert)** tritt jedes Mal auf, wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine SELECT-, INSERT-, UPDATE- oder DELETE-Anweisung ausgeführt wird.  
  
 Wenn diese Ereignisklasse in eine Ablaufverfolgung aufgenommen wird, wird die Leistung möglicherweise deutlich durch den Umfang des resultierendem Aufwands beeinträchtigt, wenn diese Ereignisse häufig auftreten. Wenn Sie den angefallenen Mehraufwand minimieren möchten, begrenzen Sie die Verwendung dieser Ereignisklasse auf Ablaufverfolgungen, die bestimmte Probleme nur kurzzeitig überwachen.  
  
## <a name="degree-of-parallelism-70-insert-event-class-data-columns"></a>Datenspalten der Degree of Parallelism (7.0 Insert)-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|**BinaryData**|**image**|Anzahl der CPUs, die zum Abschließen des Prozesses auf der Grundlage der folgenden Werte verwendet werden:<br /><br /> 0 x 00000000: Gibt einen seriellen Plan, der in Serie ausgeführt wird.<br /><br /> 0 x 01000000 einen parallelen Plan, der in Serie ausgeführt wird.<br /><br /> > = 0 x 02000000: Gibt einen parallelen Plan parallel ausgeführt wird.|2|nein|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE-Datenbankanweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE-Datenbankanweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|ja|  
|**Ereignisklasse**|**int**|Ereignistyp = 28.|27|nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**EventSubClass**|**int**|Gibt die ausgeführte Anweisung an, basierend auf den folgenden Werten:<br /><br /> 1 = Auswählen<br /><br /> 2 = Einfügen<br /><br /> 3 = Aktualisieren<br /><br /> 4 = Löschen|21|nein|  
|**GroupID**|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|**Ganzzahlige Daten**|**int**|Der "Arbeitsbereichsspeicher" in KB, der der Abfrage zugeteilt wurde, um Hashing, Sortier- oder Indexerstellungsvorgänge auszuführen. Der Arbeitsspeicher wird während der Ausführung nach Bedarf zugeordnet.|25|ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|ja|  
|**LoginName**|**nvarchar**|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder Windows-Anmeldeinformationen im Format „DOMAIN\\*username*).|11|ja|  
|**LoginSid**|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|ja|  
|**RequestID**|**int**|Die Anforderungs-ID, mit der die Volltextabfrage initiiert wurde.|49|ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)  
  
  
