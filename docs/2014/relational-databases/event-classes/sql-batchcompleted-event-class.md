---
title: SQL:BatchCompleted-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL:BatchCompleted event class
ms.assetid: 1be023e8-7a98-4400-b9e7-b24f6a3fc5ca
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94127112d214ba976e3b517bdf91a7d6b26b2d1e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63050689"
---
# <a name="sqlbatchcompleted-event-class"></a>SQL:BatchCompleted (Ereignisklasse)
  Die SQL:BatchCompleted-Ereignisklasse gibt an, dass der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Batch abgeschlossen ist.  
  
## <a name="sqlbatchcompleted-event-class-data-columns"></a>SQL:BatchCompleted-Ereignisklasse (Datenspalten)  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|CPU|`int`|CPU-Zeit (in Millisekunden), die vom Batch benötigt wird.|18|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die use *Database* -Anweisung angegeben wurde, oder die Standarddatenbank, wenn für eine bestimmte Instanz keine use *Database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|Duration|`bigint`|Die Zeit (in Mikrosekunden), die für das Ereignis benötigt wurde.|13|Ja|  
|EndTime|`datetime`|Der Zeitpunkt, zu dem das Ereignis beendet wurde. Diese Spalte wird für Startereignisklassen (z. B. SQL:BatchStarting oder SP:Starting) nicht aufgefüllt.|15|Ja|  
|Fehler|`int`|Die Fehlernummer des Ereignisses.<br /><br /> 0 = OK<br /><br /> 1 = Fehler<br /><br /> 2 = Abbruch|31|Ja|  
|EventClass|`int`|Ereignistyp = 12.|27|Nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Ja|  
|Lesevorgänge|`bigint`|Anzahl der Lesevorgänge, die durch den Batch verursacht wurden.|16|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|RowCounts|`bigint`|Die Anzahl der von einem Ereignis betroffenen Zeilen.|48|Ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TextData|`ntext`|Text des Batches.|1|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|Schreibvorgänge|`bigint`|Anzahl der Schreibvorgänge, die durch den Batch verursacht wurden.|17|Ja|  
|XactSequence|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
