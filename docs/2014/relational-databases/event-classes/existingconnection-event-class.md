---
title: ExistingConnection (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- ExistingConnection event class
ms.assetid: 3eae548f-61af-4f91-ae6f-af5c8a152543
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d30a857647b9796afb919b078553ecce58344c21
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "63023402"
---
# <a name="existingconnection-event-class"></a>ExistingConnection (Ereignisklasse)
  Die Ereignisklasse ExistingConnection zeigt die Eigenschaften der Benutzerverbindungen, die beim Starten der Ablaufverfolgung vorhanden waren. Der Server löst je ein ExistingConnection-Ereignis für die einzelnen vorhandenen Benutzerverbindungen aus.  
  
## <a name="existing-connection-event-class-data-columns"></a>Datenspalten in der Existing Connection-Ereignisklasse  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|BinaryData|`image`|Binäre Sicherung von Optionsflags wie z. B. Einstellungen auf Sitzungsebene, einschließlich ANSI-Nullen, ANSI-Zeichenauffüllung, Schließen des Cursors nach dem Commit, NULL-Verkettung und Bezeichner in Anführungszeichen.|2|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|DatabaseID|`int`|Aktuelle Datenbank-ID für die Benutzerverbindung. Die ID der Datenbank, die durch die use *Database* -Anweisung angegeben wurde, oder die Standarddatenbank, wenn für eine bestimmte Instanz keine use *Database* -Anweisung ausgegeben wurde. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|EventClass|`int`|Ereignistyp = 17.|27|Nein|  
|EventSequence|`int`|Die Position dieses Ereignisses in der Reihenfolge dieser Ablaufverfolgung.|51|Nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IntegerData|`int`|Die Netzwerkpaketgröße, die für die Verbindung verwendet wird.|25|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, NULL = Benutzer. Bei diesem Ereignis immer gleich NULL.|60|Ja|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSid|`image`|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Der Zeitpunkt, zu dem der Benutzer diese Verbindung geöffnet hatte (Anmeldezeitpunkt).|14|Ja|  
|TextData|`ntext`|Für verbindungsspezifische Optionen.|1|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Audit Login-Ereignisklasse](audit-login-event-class.md)  
  
  
