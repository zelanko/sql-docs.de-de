---
title: sp_helpqreader_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2e969e33c42348aabcd46f1c51d56c1329669820
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729204"
---
# <a name="sp_helpqreader_agent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt Eigenschaften des Warteschlangenlese-Agents zurück. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank oder auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @frompublisher = ] frompublisher`Gibt an, ob die gespeicherte Prozedur auf dem Verleger oder auf dem Verteiler aufgerufen wird. *frompublisher* ist vom Typ Bit und hat den Standardwert 0. **1** bedeutet, dass die gespeicherte Prozedur vom Verleger aufgerufen wird, und **0** bedeutet, dass die gespeicherte Prozedur vom Verteiler aufgerufen wird.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID des Agents.|  
|**name**|**nvarchar (100)**|Der Name des Agents.|  
|**job_id**|**uniqueidentifier**|Eindeutige ID des Agentauftrags.|  
|**job_login**|**nvarchar(512)**|Das Windows-Konto, unter dem der Verteilungs-Agent ausgeführt wird, das im Format *Domäne* \\ *Benutzername*zurückgegeben wird.|  
|**job_password**|**sysname**|Aus Sicherheitsgründen wird immer der Wert **\*\*\*\*\*\*\*\*\*\*** zurückgegeben.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpqreader_agent** wird bei der Transaktions Replikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn der Wert von *frompublisher* **1**ist, können nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verleger oder Mitglieder der festen Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank **sp_helpqreader_agent**ausführen. Andernfalls können nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler oder Mitglieder der festen Daten Bank Rolle **db_owner** in der Verteilungs Datenbank **sp_helpqreader_agent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
