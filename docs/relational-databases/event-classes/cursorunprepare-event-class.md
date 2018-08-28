---
title: CursorUnprepare-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CursorUnprepare event class
ms.assetid: 34055a2f-7d0f-4e13-a62e-7ee5b6c23b86
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9b56fbf325399e35c271824df9bba6e42ed473ce
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085543"
---
# <a name="cursorunprepare-event-class"></a>CursorUnprepare (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **CursorUnprepare** -Ereignisklasse stellt Informationen zu Ereignissen bereit, mit denen die Vorbereitung eines Cursors aufgehoben wird und die in Cursorn von Anwendungsprogrammierschnittstellen (Application Programming Interface; API) auftreten. Ereignisse zur Aufhebung der Vorbereitung eines Cursors treten ein, wenn ein Ausführungsplan durch [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] verworfen wird.  
  
 Nehmen Sie die **CursorUnprepare** -Ereignisklasse in Ablaufverfolgungen auf, mit denen die Leistung von Cursorn verfolgt wird. Ist die **CursorUnprepare** -Ereignisklasse ein Bestandteil einer Ablaufverfolgung, ergibt sich der anfallende Aufwand daraus, wie häufig Cursor für die Datenbank während der Ablaufverfolgung verwendet werden. Falls Cursor intensiv verwendet werden, kann die Leistung durch die Ablaufverfolgung erheblich beeinträchtigt werden.  
  
## <a name="cursorunprepare-event-class-data-columns"></a>Datenspalten in der CursorUnprepare-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den von der Anwendung übergebenen Werten und nicht mit dem angezeigten Programmnamen aufgefüllt.|10|Benutzerkontensteuerung|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Benutzerkontensteuerung|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE-Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|**EventClass**|**int**|Typ des aufgezeichneten Ereignisses = 77.|27|nein|  
|**EventSequence**|**int**|Batchreihenfolge für die **CursorUnprepare** -Ereignisklasse.|51|nein|  
|**GroupID**|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|**Handle**|**Int**|Bezeichnet den vorbereiteten Handle, dessen Vorbereitung aufgehoben werden soll.|33|Benutzerkontensteuerung|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Benutzerkontensteuerung|  
|**LoginName**|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Benutzerkontensteuerung|  
|**LoginSid**|**image**|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|Benutzerkontensteuerung|  
|**RequestID**|**int**|ID der Anforderung, mit der die Vorbereitung des Cursors aufgehoben wurde.|49|Benutzerkontensteuerung|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
|**XactSequence**|**bigint**|Das Token, das die aktuelle Transaktion beschreibt.|50|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
