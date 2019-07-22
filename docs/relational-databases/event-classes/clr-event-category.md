---
title: CLR-Ereigniskategorie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], CLR event category
- SQL Server event classes, CLR event category
- CLR event category [SQL Server]
ms.assetid: a7c0cd60-3bec-42be-ad5e-473bd26a06d9
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e589b57de25a5240b32e254d9c8280810dc0b557
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67999626"
---
# <a name="clr-event-category"></a>CLR-Ereigniskategorie
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **CLR** -Ereigniskategorie enthält Ereignisklassen, die durch Ausführen von CLR-Objekten (Common Language Runtime) von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt werden.  
 
 ## <a name="assembly-load-event-class"></a>Assembly Load-Ereignisklasse 
  Die **Assembly Load** -Ereignisklasse tritt auf, wenn eine Anforderung zum Laden einer Assembly ausgeführt wird.  
  
 Schließen Sie die **Assembly Load** -Ereignisklasse in Ablaufverfolgungen ein, mit denen Sie Assemblyauslastungen überwachen möchten. Dies kann hilfreich sein für die Problembehandlung einer Abfrage, die CLR (Common Language Runtime) verwendet, bei der Problembehandlung eines langsamen Servers, der CLR-Abfragen ausführt, oder wenn ein Server überwacht wird, um Benutzer-, Datenbank- Erfolgs- oder sonstige Informationen zu Assemblyladevorgängen zu sammeln.  
  
## <a name="assembly-load-event-class-data-columns"></a>Datenspalten der Assembly Load-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Anwendung, die den Ladevorgang angefordert hat|10|Ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE-Datenbankanweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE-Datenbankanweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**GroupID**|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**LoginName**|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|**LoginSID**|**image**|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|Ja|  
|**ObjectID**|**int**|Assembly-ID|22|Ja|  
|**ObjectName**|**nvarchar**|Der vollqualifizierte Name der Assembly|34|Ja|  
|**RequestID**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|**Success**|**int**|Gibt an, ob der Assemblyladevorgang erfolgreich ausgeführt wurde (1) oder ob ein Fehler gemeldet wurde (0)|23|Ja|  
|**TextData**|**ntext**|"Assembly Load Succeeded" bei erfolgreichem Laden, andernfalls "Assembly Load Failed".|1|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)   
 [Assemblys &#40;Datenbank-Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)  
  
   
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
