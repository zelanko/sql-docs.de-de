---
title: Lock:Timeout (timeout &gt; 0)-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Timeout event class
ms.assetid: d755833a-d7eb-4973-9352-67a2fba2442a
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 22ed4cad3f0c80dadc0b4558f1e6beb94a7d82d9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43089278"
---
# <a name="locktimeout-timeout-gt-0-event-class"></a>Lock:Timeout (timeout &gt; 0)-Ereignisklasse
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die **Lock:Timeout (timeout > 0)**-Ereignisklasse gibt an, dass für die Anforderung einer Sperre für eine Ressource, z.B. eine Seite, ein Timeout aufgetreten ist, da eine andere Transaktion eine blockierende Sperre für die angeforderte Ressource aufrechterhält. Diese Ereignisklasse unterscheidet sich von der **Lock:Timeout** -Ereignisklasse nur dadurch, dass sie keine Ereignisse einschließt, in denen der Timeoutwert gleich 0 (null) ist.  
  
 Schließen Sie die **Lock:Timeout (timeout > 0)**-Ereignisklasse in Ablaufverfolgungen ein, bei denen Sie Sperren oder sonstige Prozesse mit einem Timeoutwert von 0 verwenden. Dies ermöglicht Ihnen, festzustellen, wo tatsächlich Timeouts auftreten, ohne dass Timeouts mit dem Wert 0 angezeigt werden.  
  
## <a name="locktimeout-timeout--0-event-class-data-columns"></a>Datenspalten für die Lock:Timeout (timeout > 0)-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|BinaryData|**image**|ID der LOCK-Ressource.|2|Benutzerkontensteuerung|  
|ClientProcessID|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Benutzerkontensteuerung|  
|DatabaseID|**int**|ID der Datenbank, in der das Timeout auftrat. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|**nvarchar**|Der Name der Datenbank, in der das Timeout auftrat.|35|Benutzerkontensteuerung|  
|Duration|**bigint**|Die Zeit (in Mikrosekunden), die für das Ereignis benötigt wurde.|13|Benutzerkontensteuerung|  
|EndTime|**datetime**|Der Zeitpunkt, zu dem das Ereignis beendet wurde. Diese Spalte wird für Startereignisklassen, wie z. B. **SQL:BatchStarting** oder **SP:Starting**, nicht aufgefüllt.|15|Benutzerkontensteuerung|  
|EventClass|**int**|Ereignistyp = 189.|27|nein|  
|EventSequence|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|GroupID|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|HostName|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IntegerData2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|55|Benutzerkontensteuerung|  
|IsSystem|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Benutzerkontensteuerung|  
|LoginName|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Benutzerkontensteuerung|  
|LoginSid|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|Mode|**int**|Der Status, den das Ereignis erhalten hat oder anfordert.<br /><br /> 0=NULL<br /><br /> 1=Sch-S<br /><br /> 2=Sch-M<br /><br /> 3 = S<br /><br /> 4 = U<br /><br /> 5 = X<br /><br /> 6 = IS<br /><br /> 7 = IU<br /><br /> 8 = IX<br /><br /> 9 = SIU<br /><br /> 10 = SIX<br /><br /> 11 = UIX<br /><br /> 12 = BU<br /><br /> 13 = RangeS-S<br /><br /> 14 = RangeS-U<br /><br /> 15 = RangeI-N<br /><br /> 16 = RangeI-S<br /><br /> 17=RangeI-U<br /><br /> 18=RangeI-X<br /><br /> 19=RangeX-S<br /><br /> 20=RangeX-U<br /><br /> 21=RangeX-X|32|Benutzerkontensteuerung|  
|NTDomainName|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|NTUserName|**nvarchar**|Windows-Benutzername.|6|Benutzerkontensteuerung|  
|ObjectID|**int**|Die ID des Objekts, soweit verfügbar und anwendbar.|22|Benutzerkontensteuerung|  
|ObjectID2|**bigint**|Die ID des verbundenen Objekts oder der verbundenen Entität (sofern verfügbar und anwendbar).|56|Benutzerkontensteuerung|  
|OwnerID|**int**|1 = TRANSACTION<br /><br /> 2 = CURSOR<br /><br /> 3 = SESSION<br /><br /> 4 = SHARED_TRANSACTION_WORKSPACE<br /><br /> 5 = EXCLUSIVE_TRANSACTION_WORKSPACE|58|Benutzerkontensteuerung|  
|RequestID|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|ServerName|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|StartTime|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|TextData|**ntext**|Textwert, der von der Ereignisklasse abhängt, die in der Ablaufverfolgung aufgezeichnet wurde.|1|Benutzerkontensteuerung|  
|TransactionID|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
|Typ|**int**|1 = NULL_RESOURCE<br /><br /> 2 = DATABASE<br /><br /> 3 = FILE<br /><br /> 5 = OBJECT<br /><br /> 6 = PAGE<br /><br /> 7 = KEY<br /><br /> 8 = EXTENT<br /><br /> 9 = RID<br /><br /> 10 = APPLICATION<br /><br /> 11 = METADATA<br /><br /> 12 = AUTONAMEDB<br /><br /> 13 = HOBT<br /><br /> 14 = ALLOCATION_UNIT|57|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Lock:Timeout (Ereignisklasse)](../../relational-databases/event-classes/lock-timeout-event-class.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
  
