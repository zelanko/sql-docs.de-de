---
title: Sp_browsereplcmds (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsereplcmds_TSQL
- sp_browsereplcmds
helpviewer_keywords:
- sp_browsereplcmds
ms.assetid: 30abcb41-1d18-4f43-a692-4c80914c0450
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7918e257428fd85ddb54867ee5144f45a3bf89f1
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493842"
---
# <a name="spbrowsereplcmds-transact-sql"></a>sp_browsereplcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird als Diagnosetool verwendet und gibt ein Resultset mit einer lesbaren Version der replizierten Befehle zurück, die in der Verteilungsdatenbank gespeichert sind. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_browsereplcmds [ [ @xact_seqno_start = ] 'xact_seqno_start' ]  
    [ , [ @xact_seqno_end = ] 'xact_seqno_end' ]   
    [ , [ @originator_id = ] 'originator_id' ]  
    [ , [ @publisher_database_id = ] 'publisher_database_id' ]  
    [ , [ @article_id = ] 'article_id' ]  
    [ , [ @command_id= ] command_id ]  
    [ , [ @agent_id = ] agent_id ]  
    [ , [ @compatibility_level = ] compatibility_level ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @xact_seqno_start = ] 'xact_seqno_start'` Gibt die niedrigste genaue Sequenznummer zurückgegeben. *Xact_seqno_start* ist **nchar(22)**, hat den Standardwert 0 x 00000000000000000000.  
  
`[ @xact_seqno_end = ] 'xact_seqno_end'` Gibt die höchste genaue Sequenznummer zurückgegeben. *Xact_seqno_end* ist **nchar(22)**, hat den Standardwert 0xffffffffffffffffffff.  
  
`[ @originator_id = ] 'originator_id'` Gibt an, ob Befehle mit dem angegebenen *Originator_id* zurückgegeben werden. *Originator_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @publisher_database_id = ] 'publisher_database_id'` Gibt an, ob Befehle mit dem angegebenen *Publisher_database_id* zurückgegeben werden. *Publisher_database_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @article_id = ] 'article_id'` Gibt an, ob Befehle mit dem angegebenen *Article_id* zurückgegeben werden. *Article_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @command_id = ] command_id` Ist der Speicherort des Befehls in [MSrepl_commands &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msrepl-commands-transact-sql.md) decodiert werden muss. *Command_id* ist **Int**, hat den Standardwert NULL. Wenn angegeben, alle anderen Parameter müssen angegeben werden darüber hinaus und *Xact_seqno_start*muss identisch mit *Xact_seqno_end*.  
  
`[ @agent_id = ] agent_id` Gibt an, dass nur Befehle für einen bestimmten Replikations-Agent zurückgegeben werden. *Agent_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @compatibility_level = ] compatibility_level` Ist die Version des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem die *Compatibility_level* ist **Int**, hat den Standardwert 9000000.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**varbinary(16)**|Sequenznummer des Befehls.|  
|**originator_srvname**|**sysname**|Server, von dem die Transaktion stammt|  
|**originator_db**|**sysname**|Datenbank, von der die Transaktion stammt|  
|**article_id**|**int**|ID des Artikels.|  
|**type**|**int**|Der Typ des Befehls.|  
|**partial_command**|**bit**|Zeigt an, ob dies ein Teilbefehl ist.|  
|**hashkey**|**int**|Nur interne Verwendung.|  
|**originator_publication_id**|**int**|ID der Veröffentlichung, von der die Transaktion stammt|  
|**originator_db_version**|**int**|Version der Datenbank, von der die Transaktion stammt|  
|**originator_lsn**|**varbinary(16)**|Identifiziert die Protokollfolgenummer (LSN, Log Sequence Number) für den Befehl in der ursprünglichen Veröffentlichung Peer-zu-Peer-Transaktionsreplikation verwendet.|  
|**Befehl**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] -Befehl.|  
|**command_id**|**int**|ID des Befehls in [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
  
 Lange Befehle können auf mehrere Zeilen des Resultsets aufgeteilt werden.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_browsereplcmds** wird in Transaktionsreplikationen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle oder Mitglieder der **Db_owner** oder **Replmonitor** festen Datenbankrollen für die Verteilungsdatenbank können Ausführen**Sp_browsereplcmds**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
