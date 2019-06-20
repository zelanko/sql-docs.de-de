---
title: Deprecation Final Support (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Deprecation Final Support event class
- deprecation [SQL Server], events final support
ms.assetid: 2b4d88d0-62be-45c0-bea8-c5900d553d31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2833f1f342aa212b73611d257b8e29606a14cce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62662981"
---
# <a name="deprecation-final-support-event-class"></a>Deprecation Final Support (Ereignisklasse)
  Die **Deprecation Final Support** -Ereignisklasse tritt auf, wenn Sie eine Funktion verwenden, die aus der nächsten Hauptversion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt wird. Damit Ihre Anwendungen möglichst langlebig sind, sollten Sie keine Funktionen verwenden, die die **Deprecation Announcement** -Ereignisklasse oder die **Deprecation Final Support** -Ereignisklasse auslösen. Ändern Sie Anwendungen mit veralteten Funktionen so bald wie möglich.  
  
## <a name="deprecation-final-support-event-class-data-columns"></a>Deprecation Final Support-Ereignisklasse (Datenspalten)  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die `ServerName`-Datenspalte in der Ablaufverfolgung erfasst wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|EventClass|`int`|Ereignistyp = 126.|27|Nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IntegerData2|`int`|Endoffset (in Bytes) der Anweisung, die gerade ausgeführt wird.|55|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Ja|  
|Offset|`int`|Der Startoffset der Anweisung in der gespeicherten Prozedur oder im Batch.|61|Ja|  
|ObjectID|`int`|Die ID der veralteten Funktion.|22|Ja|  
|ObjectName|`nvarchar`|Der Name der veralteten Funktion.|34|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von Login1 herstellen und eine Anweisung mithilfe von Login2 ausführen, zeigt `SessionLoginName` Login1 an, und `LoginName` zeigt Login2 an. In dieser Spalte werden sowohl der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch der Windows-Anmeldename angezeigt.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|SqlHandle|`image`|Binäres Handle, mit dem SQL-Batches oder gespeicherte Prozeduren identifiziert werden können.|63|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TextData|`ntext`|Textwert, der von der Ereignisklasse abhängt, die in der Ablaufverfolgung aufgezeichnet wurde.|1|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|XactSequence|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Deprecation Announcement-Ereignisklasse](deprecation-announcement-event-class.md)   
 [Als veraltet markierte Features der Datenbank-Engine in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
