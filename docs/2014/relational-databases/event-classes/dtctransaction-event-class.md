---
title: DTCTransaction-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- DTCTransaction event class
ms.assetid: 9a2d358e-5b8f-4d0b-8b93-6705c009ad57
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 26da2a16462b9853489c6430a6c80e1ab2a6f3b8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62662967"
---
# <a name="dtctransaction-event-class"></a>DTCTransaction-Ereignisklasse
  Verwenden Sie die **DTCTransaction-Ereignisklasse** zum Überwachen des Status von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Transaktionen, die über [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (DTC) koordiniert werden. Dies umfasst Transaktionen, die mindestens zwei Datenbanken in derselben Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]betreffen, oder verteilte Transaktionen, die mindestens Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]betreffen.  
  
## <a name="dtctransaction-event-class-data-columns"></a>Datenspalten der DTCTransaction-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**BinaryData**|`image`|Binäre Darstellung der Arbeitseinheits-ID (Unit of Work, UOW), die diese Transaktion eindeutig in DTC kennzeichnet.|2|Ja|  
|**ClientProcessID**|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|**DatabaseID**|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|**EventClass**|`int`|Ereignistyp = 19.|27|Nein|  
|**EventSequence**|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**EventSubClass**|`int`|Der Typ der Ereignisunterklasse.<br /><br /> 0 = Adresse abrufen<br /><br /> 1 = Transaktion weitergeben<br /><br /> 3 = Verbindung schließen<br /><br /> 6 = Erstellen einer neuen DTC-Transaktion<br /><br /> 7 = Eintragen in eine DTC-Transaktion<br /><br /> 9 = Interner Commit<br /><br /> 10 = Interner Abbruch<br /><br /> 14 = Vorbereiten der Transaktion<br /><br /> 15 = Transaktion ist vorbereitet<br /><br /> 16 = Transaktion wird abgebrochen<br /><br /> 17 = Für Transaktion wird ein Commit ausgeführt<br /><br /> 22 = TM im Status Vorbereitet fehlgeschlagen<br /><br /> 23 = Unbekannt|21|Ja|  
|**GroupID**|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|**HostName**|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IntegerData**|`int`|Isolationsstufe der Transaktion.|25|Ja|  
|**IsSystem**|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginName**|`nvarchar`|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|**LoginSid**|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|**NTUserName**|`nvarchar`|Windows-Benutzername.|6|Ja|  
|**RequestID**|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|**ServerName**|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|`datetime`|Der Zeitpunkt, zu dem das Ereignis begonnen hat (falls verfügbar).|14|Ja|  
|**TextData**|`ntext`|Textdarstellung der UOW, die diese Transaktion eindeutig in DTC kennzeichnet.|1|Ja|  
|**TransactionID**|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|**XactSequence**|`bigint`|Token zur Beschreibung der aktuellen Transaktion.|50|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
