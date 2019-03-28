---
title: Sp_MSchange_logreader_agent_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_logreader_agent_properties_TSQL
- sp_MSchange_logreader_agent_properties
helpviewer_keywords:
- sp_MSchange_logreader_agent_properties
ms.assetid: 925df9d3-a041-4046-8e17-c47f40edb86d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e4393f1cc0baab6fd10899b18cac763363d9af89
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535836"
---
# <a name="spmschangelogreaderagentproperties-transact-sql"></a>sp_MSchange_logreader_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Eigenschaften eines Protokolllese-Agent-Auftrags, der ausgeführt wird ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder einer höheren Version Verteiler. Diese gespeicherte Prozedur wird zum Ändern von Eigenschaften verwendet, wenn der Verleger in einer Instanz von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ausgeführt wird. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_MSchange_logreader_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Der Sicherheitsmodus wird vom Agent verwendet werden, Herstellen der Verbindung mit dem Verleger. *Publisher_security_mode* ist **Smallint**, hat keinen Standardwert.  
  
 **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.  
  
 **1** gibt die Windows-Authentifizierung.  
  
`[ @publisher_login = ] 'publisher_login'` Der Benutzername, der verwendet wird, Herstellen der Verbindung mit dem Verleger. *Publisher_login* ist **Sysname**, hat keinen Standardwert. *Publisher_login* muss angegeben werden, wenn *Publisher_security_mode* ist **0**. Wenn *Publisher_login* ist NULL und *Publisher_security_mode* ist **1**, und klicken Sie dann das angegebene Windows-Konto *Job_login* verwendet werden Herstellen der Verbindung mit dem Verleger.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort wird verwendet werden, wenn eine Verbindung mit dem Verleger herstellen. *Publisher_password* ist **Sysname**, hat keinen Standardwert.  
  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_login* ist **nvarchar(257)**, hat keinen Standardwert. *Dies kann nicht geändert werden, für einen nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_type = ] 'publisher_type'` Gibt den verlegertyp an, wenn der Verleger nicht, in einer Instanz von ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Publisher_type* ist **Sysname**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Gibt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger an.|  
|**ORACLE**|Gibt einen standardmäßigen Oracle-Verleger an.|  
|**ORACLE-GATEWAY**|Gibt einen Oracle Gateway-Verleger an.|  
  
 Weitere Informationen zu den Unterschieden zwischen einem Oracle-Verleger und einem Oracle Gateway-Verleger finden Sie unter [Oracle-Veröffentlichung (Übersicht)](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="remarks"></a>Hinweise  
 **Sp_MSchange_logreader_agent_properties** wird in Transaktionsreplikationen verwendet.  
  
 Sie müssen alle Parameter angeben, für die Ausführung **Sp_MSchange_logreader_agent_properties**. Führen Sie [Sp_helplogreader_agent &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) auf die aktuellen Eigenschaften des Protokolllese-Agent-Auftrags zurückzugeben.  
  
 Nach dem Ändern des Anmeldenamens oder Kennworts eines Agents müssen Sie den Agent beenden und neu starten, damit die Änderungen in Kraft treten.  
  
 Wenn der Verleger ausgeführt wird, auf einer Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher, verwenden Sie [Sp_changelogreader_agent](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md) so ändern Sie die Eigenschaften des Protokolllese-Agent.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle auf dem Verteiler **Sp_MSchange_logreader_agent_properties**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
