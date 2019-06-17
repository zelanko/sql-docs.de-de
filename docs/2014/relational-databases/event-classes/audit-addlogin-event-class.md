---
title: Audit Addlogin-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Addlogin event class
ms.assetid: 6e0633dc-889e-49ef-bace-3c50958db2dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b40ec59f8d0f845528bb644631142ee89af03dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62912164"
---
# <a name="audit-addlogin-event-class"></a>Audit Addlogin-Ereignisklasse
  Die **Audit Addlogin** -Ereignisklasse tritt auf, wenn ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename hinzugefügt oder entfernt wird.  
  
 Wenn Sie beim Hinzufügen des Anmeldenamens zusätzliche Eigenschaften festlegen, z. B. eine Standarddatenbank, sind die Informationen zu diesen Eigenschaften in der **TextData** -Spalte dieses Ereignisses zu finden. Wenn Sie diese Eigenschaften beim Hinzufügen eines Anmeldenamens festlegen, tritt kein Ereignis der **Audit Login Change Property** -Ereignisklasse auf.  
  
 Dieses Überwachungsereignis ist für die gespeicherten Prozeduren **sp_addlogin** und **sp_droplogin** .  
  
 Es kann sein, dass diese Ereignisklasse in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt wird. Es wird empfohlen, dass Sie stattdessen die **Audit Server Principal Management** -Ereignisklasse verwenden.  
  
## <a name="audit-addlogin-event-class-data-columns"></a>Datenspalten der Audit Addlogin-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|**EventClass**|**int**|Ereignistyp = 104.|27|Nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1 = Hinzufügen<br /><br /> 2 = Löschen|21|Ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginName**|**nvarchar**|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|**LoginSid**|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|Ja|  
|**RequestID**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|**Nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|**Success**|**int**|1 = Erfolg 0 = Fehler. Der Wert 1 zeigt z. B. den Erfolg einer Berechtigungsüberprüfung an und der Wert 0 das Fehlschlagen dieser Überprüfung.|23|Ja|  
|**TargetLoginName**|**nvarchar**|Hinzuzufügender oder zu löschender Anmeldename|42|Ja|  
|**TargetLoginSid**|**image**|Sicherheits-ID (SID) des Zielanmeldenamens (falls als Parameter übergeben)|43|Ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|**XactSequence**|**bigint**|Token zur Beschreibung der aktuellen Transaktion.|50|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Audit Login Change Property (Ereignisklasse)](audit-login-change-property-event-class.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)   
 [sp_droplogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droplogin-transact-sql)   
 [Audit Server Principal Management (Ereignisklasse)](audit-server-principal-management-event-class.md)  
  
  
