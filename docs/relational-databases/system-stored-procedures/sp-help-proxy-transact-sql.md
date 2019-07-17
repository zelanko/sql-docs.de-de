---
title: Sp_help_proxy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_proxy
- sp_help_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_proxy
ms.assetid: a2fce164-2b64-40c2-8f35-6eeb7844abf1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 904a694d73613bb1c40c671b18ca33e5d9b5d0e6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085278"
---
# <a name="sphelpproxy-transact-sql"></a>sp_help_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet Informationen zu mindestens einem Proxy auf.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @subsystem_name = ] 'subsystem_name' ,  
    [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_id = ] id` Die Proxy-ID des Proxys für den Informationen aufgelistet werden soll. Die *Proxy_id* ist **Int**, hat den Standardwert NULL. Entweder die *Id* oder *Proxy_name* kann angegeben werden.  
  
`[ @proxy_name = ] 'proxy_name'` Der Name des Proxys für den Informationen aufgelistet. Die *Proxy_name* ist **Sysname**, hat den Standardwert NULL. Entweder die *Id* oder *Proxy_name* kann angegeben werden.  
  
`[ @subsystem_name = ] 'subsystem_name'` Der Name des Subsystems, für die Proxys aufgelistet werden sollen. Die *Subsystem_name* ist **Sysname**, hat den Standardwert NULL. Wenn *Subsystem_name* angegeben wird, *Namen* muss auch angegeben werden.  
  
 In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|ActiveScripting|ActiveX-Skript|  
|CmdExec|Betriebssystem (CmdExec)|  
|Momentaufnahme|Replikationsmomentaufnahme-Agent|  
|LogReader|Replikationsprotokolllese-Agent|  
|Distribution|Replikationsverteilungs-Agent|  
|Merge|Replikationsmerge-Agent|  
|QueueReader|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|ANALYSISQUERY|Analysis Services-Befehl|  
|ANALYSISCOMMAND|Analysis Services-Abfrage|  
|Dts|SSIS-Paketausführung|  
|PowerShell|PowerShell-Skript|  
  
`[ @name = ] 'name'` Der Name des eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] melden Sie sich die Proxys aufgelistet werden sollen. Der Name ist **nvarchar(256)** , hat den Standardwert NULL. Wenn *Namen* angegeben wird, *Subsystem_name* muss auch angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID des Proxys.|  
|**name**|**sysname**|Der Name des Proxys.|  
|**credential_identity**|**sysname**|Der Microsoft Windows-Domänenname und -Benutzername für die dem Proxy zugeordneten Anmeldeinformationen.|  
|**aktiviert**|**tinyint**|Gibt an, ob dieser Proxy aktiviert ist. { **0** = nicht aktiviert, **1** = aktiviert}|  
|**description**|**nvarchar(1024)**|Die Beschreibung des Proxys.|  
|**user_sid**|**varbinary(85)**|Die Windows-SID des Windows-Benutzers für diesen Proxy.|  
|**credential_id**|**int**|Die ID für die dem Proxy zugeordneten Anmeldeinformationen.|  
|**credential_identity_exists**|**int**|Gibt an, ob credential_identity vorhanden ist. { 0 = ist nicht vorhanden, 1 = ist vorhanden }|  
  
## <a name="remarks"></a>Hinweise  
 Wenn keine Parameter angegeben werden, **Sp_help_proxy** listet Informationen zu allen Proxys in der Instanz.  
  
 Um zu bestimmen, welche Proxys eine Anmeldung für ein bestimmtes Subsystem verwenden können, geben Sie *Namen* und *Subsystem_name*. Wenn diese Argumente angegeben werden, **Sp_help_proxy** Proxys, die die Anmeldung angegeben, kann den Zugriff und können verwendet werden für das angegebene Subsystem aufgelistet.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
 Weitere Informationen zu **SQLAgentOperatorRole**, finden Sie unter [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
> [!NOTE]  
>  Die **Credential_identity** und **User_sid** Spalten werden nur zurückgegeben, das Ergebnis festgelegt, wenn Mitglieder der **Sysadmin** diese gespeicherte Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-information-for-all-proxies"></a>A. Auflistungsinformationen für alle Proxys  
 Im folgenden Beispiel werden die Informationen zu allen Proxys in der Instanz aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-proxy"></a>B. Auflistungsinformationen für einen bestimmten Proxy  
 Im folgenden Beispiel werden die Informationen zum Proxy `Catalog application proxy` aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)  
  
  
