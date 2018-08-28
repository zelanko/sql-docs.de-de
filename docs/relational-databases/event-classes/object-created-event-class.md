---
title: Object:Created-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Object:Created event class
ms.assetid: 57536924-5e66-4b09-a76d-8fcea2131771
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5678c7ad20f1f4d9417e7d07d7bde23aedbbdc5f
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43096304"
---
# <a name="objectcreated-event-class"></a>Object:Created-Ereignisklasse
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die Object:Created-Ereignisklasse gibt an, dass ein Objekt erstellt wurde, z. B. mit der CREATE INDEX-, CREATE TABLE- oder CREATE DATABASE-Anweisung.  
  
 Mit dieser Ereignisklasse kann ermittelt werden, ob Objekte angelegt werden, z. B. durch ODBC-Anwendungen, die oft temporäre gespeicherte Prozeduren erstellen. Durch Überwachen der Datenspalten LoginName und NTUserName können Sie den Namen des Benutzers bestimmen, der Objekte erstellt, löscht oder darauf zugreift.  
  
## <a name="objectcreated-event-class-data-columns"></a>Datenspalten der Object:Created-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|ClientProcessID|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Benutzerkontensteuerung|  
|DatabaseID|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|EventClass|**int**|Ereignistyp = 46.|27|nein|  
|EventSequence|**int**|Die Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|EventSubClass|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 0 = Begin<br /><br /> 1 = Commit<br /><br /> 2 = Rollback|21|Benutzerkontensteuerung|  
|GroupID|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|HostName|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IndexID|**int**|ID für den Index des Objekts, das von dem Ereignis betroffen ist. Um die Index-ID für ein Objekt zu ermitteln, verwenden Sie die index_id-Spalte der Katalogsicht sys.indexes.|24|Benutzerkontensteuerung|  
|IntegerData|**int**|Wert für eine ganze Zahl, der von der in der Ablaufverfolgung erfassten Ereignisklasse abhängt.|25|Benutzerkontensteuerung|  
|IsSystem|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Benutzerkontensteuerung|  
|LoginName|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Benutzerkontensteuerung|  
|LoginSid|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|NTDomainName|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|NTUserName|**nvarchar**|Windows-Benutzername.|6|Benutzerkontensteuerung|  
|ObjectID|**int**|Vom System zugewiesene ID des Objekts.|22|Benutzerkontensteuerung|  
|ObjectID2|**bigint**|Die ID des verbundenen Objekts oder der verbundenen Entität.|56|Benutzerkontensteuerung|  
|ObjectName|**nvarchar**|Name des Objekts, auf das verwiesen wird|34|Benutzerkontensteuerung|  
|ObjectType|**int**|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in sys.objects. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Benutzerkontensteuerung|  
|RequestID|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|ServerName|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise Login1 dazu verwenden, eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen, und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an, wogegen LoginName den Wert Login2 anzeigt. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|StartTime|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|TransactionID|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
|XactSequence|**bigint**|Token zur Beschreibung der aktuellen Transaktion.|50|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
