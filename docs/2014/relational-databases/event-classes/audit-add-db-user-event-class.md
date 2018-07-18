---
title: Audit Add DB User-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Add DB User event class
ms.assetid: ac9ed573-c84d-444c-81fb-923a6240c1ef
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4d145d63acba86422222ff9fca401933230fece
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260826"
---
# <a name="audit-add-db-user-event-class"></a>Audit Add DB User-Ereignisklasse
  Die **Audit Add DB User** -Ereignisklasse tritt auf, wenn ein Anmeldename als Datenbankbenutzer in einer Datenbank hinzugefügt oder entfernt wird. Diese Ereignisklasse wird für die gespeicherten Prozeduren **sp_grantdbaccess**, **sp_revokedbaccess**, **sp_adduser**und **sp_dropuser** verwendet.  
  
 Es kann sein, dass diese Ereignisklasse in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt wird. Es wird empfohlen, stattdessen die **Audit Database Principal Management** -Ereignisklasse zu verwenden.  
  
## <a name="audit-add-db-user-event-class-data-columns"></a>Datenspalten der Audit Add DB User-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|ja|  
|**ColumnPermissions**|**int**|Zeigt an, ob eine Spaltenberechtigung festgelegt wurde. Analysieren Sie den Text der Anweisung, um zu ermitteln, welche Berechtigungen auf welche Spalten angewendet wurden.|44|ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|**DatabaseName**|**nvarchar**|Der Name der Datenbank, der der Benutzername hinzugefügt oder aus der er entfernt wird.|35|ja|  
|**DBUserName**|**nvarchar**|Der Benutzername des Ausstellers in der Datenbank.|40|ja|  
|**EventClass**|**int**|Ereignistyp = 109.|27|nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1 = Hinzufügen<br /><br /> 2 = Löschen<br /><br /> 3 = Datenbankzugriff erteilen<br /><br /> 4 = Datenbankzugriff aufheben|21|ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|ja|  
|**LoginName**|**nvarchar**|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|ja|  
|**LoginSid**|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|ja|  
|**OwnerName**|**nvarchar**|Datenbank-Benutzername des Objektbesitzers.|37|ja|  
|**RequestID**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|ja|  
|**RoleName**|**nvarchar**|Der Name der Datenbankrolle, deren Mitgliedschaft geändert wird (falls **sp_adduser**verwendet wird).|38|ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26||  
|**SessionLoginName**|**Nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|ja|  
|**Success**|**int**|1 = Erfolg 0 = Fehler. Der Wert 1 deutet beispielsweise auf eine erfolgreiche Überprüfung der Berechtigungen hin, während die Überprüfung bei dem Wert 0 fehlgeschlagen ist.|23|ja|  
|**TargetLoginName**|**nvarchar**|Der Anmeldename, dessen Datenbankzugriff geändert wird.|42|ja|  
|**TargetLoginSid**|**image**|Für Aktionen, die auf einen Anmeldenamen abzielen (z. B. das Hinzufügen eines neuen Anmeldenamens), die Sicherheits-ID (SID), auf die abgezielt wird.|43|ja|  
|**TargetUserName**|**nvarchar**|Der Name des Datenbankbenutzers, der hinzugefügt wird.|39|ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|ja|  
|**XactSequence**|**bigint**|Token zur Beschreibung der aktuellen Transaktion.|50|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql)   
 [sp_adduser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adduser-transact-sql)   
 [sp_dropuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropuser-transact-sql)   
 [Audit Database Principal Management-Ereignisklasse](audit-database-principal-management-event-class.md)  
  
  
