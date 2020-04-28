---
title: sp_helplogreader_agent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords:
- sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
author: stevestein
ms.author: sstein
ms.openlocfilehash: b6ecac979077dd83d6549b408c8c9e4d2bd4402f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122437"
---
# <a name="sp_helplogreader_agent-transact-sql"></a>sp_helplogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Eigenschaften des Auftrags des Protokolllese-Agents für die Veröffentlichungsdatenbank zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helplogreader_agent [ [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID des Agents.|  
|**name**|**nvarchar (100)**|Der Name des Agents.|  
|**publisher_security_mode**|**smallint**|Sicherheitsmodus, der vom Agent für die Verbindung mit dem Verleger verwendet wird. Folgende Werte sind möglich:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung<br /><br /> **1** = Windows-Authentifizierung.|  
|**publisher_login**|**sysname**|Anmeldename, der für die Verbindung mit dem Verleger verwendet wird.|  
|**publisher_password**|**nvarchar (524)**|Aus Sicherheitsgründen wird ** \* \* \* \* \* \* immer \* der \* Wert zurück \* ** gegeben.|  
|**job_id**|**uniqueidentifier**|Eindeutige ID des Agentauftrags.|  
|**job_login**|**nvarchar(512)**|Das Windows-Konto, unter dem die Protokolllese-Agent ausgeführt wird, das im Format *Domäne*\\*Benutzername*zurückgegeben wird.|  
|**job_password**|**sysname**|Aus Sicherheitsgründen wird ** \* \* \* \* \* \* immer \* der \* Wert zurück \* ** gegeben.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helplogreader_agent** wird bei der Transaktions Replikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verleger oder Mitglieder der festen Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank können **sp_helplogreader_agent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Replikations Sicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addlogreader_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
