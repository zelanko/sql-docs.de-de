---
title: Object:Altered-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Object:Altered event class
ms.assetid: f94e3b59-ff2f-4d8d-8479-e85ce5b3483e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bd38e8d1685b23cfeeb1793d02b0fff1d7de0640
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62662244"
---
# <a name="objectaltered-event-class"></a>Object:Altered-Ereignisklasse
  Durch die Object:Altered-Ereignisklasse wird angegeben, dass Objekt geändert wurde, beispielsweise durch eine ALTER INDEX-, ALTER TABLE- oder ALTER DATABASE-Anweisung. Dieses Ereignisklasse kann dazu verwendet werden, festzustellen, ob Objekte beispielsweise durch ODBC-Anwendungen geändert wurden, durch die häufig temporäre gespeicherte Prozeduren erstellt werden.  
  
 Die Object:Altered-Ereignisklasse tritt immer als zwei Ereignisse auf. Das erste Ereignis gibt die Phase des Begins an. Das zweite Ereignis gibt die Rollback- oder Commitphase an.  
  
 Durch das Überwachen der Datenspalten LoginName und NTUserName können Sie den Namen des Benutzers feststellen, der Objekte erstellt, löscht oder ändert.  
  
## <a name="objectaltered-event-class-data-columns"></a>Object:Altered (Ereignisklasse-Datenspalten)  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|EventClass|`int`|Ereignistyp = 164.|27|Nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|EventSubClass|`int`|Der Typ der Ereignisunterklasse.<br /><br /> 0 = Begin<br /><br /> 1 = Commit<br /><br /> 2 = Rollback|21|Ja|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IndexID|`int`|ID für den Index des Objekts, das von dem Ereignis betroffen ist. Um die Index-ID für ein Objekt zu ermitteln, verwenden Sie die index_id-Spalte der Katalogsicht sys.indexes.|24|Ja|  
|IntegerData|`int`|Die Ereignissequenznummer des korrespondierenden Begin-Ereignisses. Diese Spalte ist nur für den Commit- und Rollback-Typ der Ereignisunterklasse verfügbar.|25|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, NULL = Benutzer.|60|Ja|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Ja|  
|ObjectID|`int`|Vom System zugewiesene ID des Objekts.|22|Ja|  
|ObjectID2|`bigint`|Die Partitionsfunktions-ID beim Ändern des Partitionsschemas, die Warteschlangen-ID beim Ändern des Dienstes, oder die Sammlungsschema-ID beim Ändern des XML-Schemas.|56|Ja|  
|ObjectName|`nvarchar`|Name des Objekts, auf das verwiesen wird|34|Ja|  
|ObjectType|`int`|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in der sys.objects-Katalogsicht. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](objecttype-trace-event-column.md).|28|Ja|  
|RequestID|`int`|Die ID der Batchanforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|XactSequence|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
