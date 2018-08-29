---
title: Sp_revoke_proxy_from_subsystem (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_revoke_login_from_subsystem
- sp_revoke_login_from_subsystem_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revoke_proxy_from_subsystem
ms.assetid: b87bc8ba-3ea8-4aed-b54b-32c3d82d9d2a
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 883ae75134c2559c2f9c4742ed73e4c760d140d7
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028149"
---
# <a name="sprevokeproxyfromsubsystem-transact-sql"></a>sp_revoke_proxy_from_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Hebt den Zugriff auf ein Subsystem für einen Proxy auf.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_revoke_proxy_from_subsystem   
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@proxy_id** = ] *id*  
 Die Proxy-ID des Proxys, für den der Zugriff aufgehoben werden soll. Die *Proxy_id* ist **Int**, hat den Standardwert NULL. Entweder *Proxy_id* oder *Proxy_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
 [ **@proxy_name** =] **"***Proxy_name***"**  
 Der Name des Proxys, für den der Zugriff aufgehoben werden soll. Die *Proxy_name* ist **Sysname**, hat den Standardwert NULL. Entweder *Proxy_id* oder *Proxy_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
 [ **@subsystem_id** = ] *id*  
 Die ID des Subsystems, für das der Zugriff aufgehoben werden soll. Die *Subsystem_id* ist **Int**, hat den Standardwert NULL. Entweder *Subsystem_id* oder *Subsystem_name* muss angegeben werden, aber beide Angaben sind nicht möglich. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|value|Description|  
|-----------|-----------------|  
|**2**|ActiveX-Skript<br /><br /> **\*\* Wichtige \* \***  das ActiveX-skriptsubsystem wird aufgehoben, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent in einer zukünftigen Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.|  
|**3**|Betriebssystem (CmdExec)|  
|**4**|Replikationsmomentaufnahme-Agent|  
|**5**|Replikationsprotokolllese-Agent|  
|**6**|Replikationsverteilungs-Agent|  
|**7**|Replikationsmerge-Agent|  
|**8**|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|**9**|Analysis Services-Befehl|  
|**10**|Analysis Services-Abfrage|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)]-Paketausführung|  
|**12**|PowerShell-Skript|  
  
 [ **@subsystem_name**=] **"***Subsystem_name***"**  
 Der Name des Subsystems, für das der Zugriff aufgehoben werden soll. Die *Subsystem_name* ist **Sysname**, hat den Standardwert NULL. Entweder *Subsystem_id* oder *Subsystem_name* muss angegeben werden, aber beide Angaben sind nicht möglich. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|value|Description|  
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
|Dts|[!INCLUDE[ssIS](../../includes/ssis-md.md)]-Paketausführung|  
|PowerShell|PowerShell-Skript|  
  
## <a name="remarks"></a>Hinweise  
 Mit dem Aufheben des Zugriffs auf ein Subsystem werden nicht die Berechtigungen für den im Proxy angegebenen Prinzipal geändert.  
  
> [!NOTE]  
>  Um zu bestimmen, welche Auftragsschritte auf einen Proxy verweisen, Informationen zu diesem mit der rechten Maustaste die **Proxys** Knoten unter **SQL Server-Agent** in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], und klicken Sie dann auf **Eigenschaften**. In der **Proxyeigenschaften** wählen Sie im Dialogfeld die **Verweise** Seite, um alle Auftragsschritte anzuzeigen, die auf diesen Proxy verweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_revoke_proxy_from_subsystem**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Zugriff auf das [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Subsystem für den Proxy `Catalog application proxy` aufgehoben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_proxy_from_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_name = N'Dts';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Implementieren von SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
