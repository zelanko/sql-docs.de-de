---
title: ExistingConnection (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- ExistingConnection event class
ms.assetid: 3eae548f-61af-4f91-ae6f-af5c8a152543
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f57bf8b1a40783eccbb75cd27edf5eb390b1cdc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078160"
---
# <a name="existingconnection-event-class"></a>ExistingConnection (Ereignisklasse)
  Die Ereignisklasse ExistingConnection zeigt die Eigenschaften der Benutzerverbindungen, die beim Starten der Ablaufverfolgung vorhanden waren. Der Server löst je ein ExistingConnection-Ereignis für die einzelnen vorhandenen Benutzerverbindungen aus.  
  
## <a name="existing-connection-event-class-data-columns"></a>Datenspalten in der Existing Connection-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|BinaryData|`image`|Binäre Sicherung von Optionsflags wie z. B. Einstellungen auf Sitzungsebene, einschließlich ANSI-Nullen, ANSI-Zeichenauffüllung, Schließen des Cursors nach dem Commit, NULL-Verkettung und Bezeichner in Anführungszeichen.|2|Benutzerkontensteuerung|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Benutzerkontensteuerung|  
|DatabaseID|`int`|Aktuelle Datenbank-ID für die Benutzerverbindung. Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|EventClass|`int`|Ereignistyp = 17.|27|nein|  
|EventSequence|`int`|Die Position dieses Ereignisses in der Reihenfolge dieser Ablaufverfolgung.|51|nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IntegerData|`int`|Die Netzwerkpaketgröße, die für die Verbindung verwendet wird.|25|Benutzerkontensteuerung|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, NULL = Benutzer. Bei diesem Ereignis immer gleich NULL.|60|Benutzerkontensteuerung|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Benutzerkontensteuerung|  
|LoginSid|`image`|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Benutzerkontensteuerung|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|StartTime|`datetime`|Der Zeitpunkt, zu dem der Benutzer diese Verbindung geöffnet hatte (Anmeldezeitpunkt).|14|Benutzerkontensteuerung|  
|TextData|`ntext`|Für verbindungsspezifische Optionen.|1|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Audit Login (Ereignisklasse)](audit-login-event-class.md)  
  
  
