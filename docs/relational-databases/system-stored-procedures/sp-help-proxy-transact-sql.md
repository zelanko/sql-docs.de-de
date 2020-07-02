---
title: sp_help_proxy (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e9c59c6347317d193eafe43c511c0ece3831e29c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750532"
---
# <a name="sp_help_proxy-transact-sql"></a>sp_help_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Listet Informationen zu mindestens einem Proxy auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @subsystem_name = ] 'subsystem_name' ,  
    [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_id = ] id`Die Proxy-ID des Proxys, für den Informationen aufgelistet werden sollen. Der *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es kann entweder die *ID* oder die *proxy_name* angegeben werden.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys, für den Informationen aufgelistet werden sollen. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es kann entweder die *ID* oder die *proxy_name* angegeben werden.  
  
`[ @subsystem_name = ] 'subsystem_name'`Der Name des Subsystems, für das Proxys aufgelistet werden sollen. Der *subsystem_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *subsystem_name* angegeben wird, muss auch *Name* angegeben werden.  
  
 In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|ActiveScripting|ActiveX-Skript|  
|CmdExec|Betriebssystem (CmdExec)|  
|Snapshot|Replikationsmomentaufnahme-Agent|  
|LogReader|Replikationsprotokolllese-Agent|  
|Verteilung|Replikations Verteilungs-Agent|  
|Merge|Replikationsmerge-Agent|  
|QueueReader|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|ANALYSISQUERY|Analysis Services-Befehl|  
|ANALYSISCOMMAND|Analysis Services-Abfrage|  
|Dts|SSIS-Paketausführung|  
|PowerShell|PowerShell-Skript|  
  
`[ @name = ] 'name'`Der Name einer Anmeldung, für die Proxys [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgelistet werden sollen. Der Name ist vom Datentyp **nvarchar (256)** und hat den Standardwert NULL. Wenn *Name* angegeben ist, muss auch *subsystem_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID des Proxys.|  
|**name**|**sysname**|Der Name des Proxys.|  
|**credential_identity**|**sysname**|Der Microsoft Windows-Domänenname und -Benutzername für die dem Proxy zugeordneten Anmeldeinformationen.|  
|**wodurch**|**tinyint**|Gibt an, ob dieser Proxy aktiviert ist. { **0** = nicht aktiviert, **1** = aktiviert}|  
|**description**|**nvarchar(1024)**|Die Beschreibung des Proxys.|  
|**user_sid**|**varbinary(85)**|Die Windows-SID des Windows-Benutzers für diesen Proxy.|  
|**credential_id**|**int**|Die ID für die dem Proxy zugeordneten Anmeldeinformationen.|  
|**credential_identity_exists**|**int**|Gibt an, ob credential_identity vorhanden ist. { 0 = ist nicht vorhanden, 1 = ist vorhanden }|  
  
## <a name="remarks"></a>Hinweise  
 Wenn keine Parameter bereitgestellt werden, listet **sp_help_proxy** Informationen für alle Proxys in der Instanz auf.  
  
 Um zu ermitteln, welche Proxys ein Anmelde Name für ein bestimmtes Subsystem verwenden kann, geben Sie *Name* und *subsystem_name*an. Wenn diese Argumente bereitgestellt werden, listet **sp_help_proxy** Proxys auf, auf die der angegebene Anmelde Name zugreifen kann und die für das angegebene Subsystem verwendet werden kann.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
 Ausführliche Informationen zu **SQLAgentOperatorRole**finden Sie unter [SQL Server-Agent fester Daten bankrollen](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
> [!NOTE]  
>  Die Spalten **credential_identity** und **user_sid** werden nur im Resultset zurückgegeben, wenn Mitglieder von **sysadmin** diese gespeicherte Prozedur ausführen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)  
  
  
