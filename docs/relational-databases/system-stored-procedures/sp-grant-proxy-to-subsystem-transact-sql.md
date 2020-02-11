---
title: sp_grant_proxy_to_subsystem (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 96e044b94244492202058d6dc2b2f048a9c1db6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68123821"
---
# <a name="sp_grant_proxy_to_subsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gewährt einem Subsystem einen Proxyzugriff.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_id = ] id`Die Proxy-ID des Proxys, für den der Zugriff gewährt werden soll. Der *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *proxy_id* oder *proxy_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys, für den der Zugriff gewährt werden soll. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es muss entweder *proxy_id* oder *proxy_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @subsystem_id = ] id`Die ID-Nummer des Subsystems, auf das der Zugriff gewährt werden soll. Der *subsystem_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *subsystem_id* oder *subsystem_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**2**|
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX-Skript<br /><br /> ** \* Wichtig \* \* ** Das ActiveX Scripting-Subsystem wird in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zukünftigen Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aus dem-Agent entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.|  
|**€**|Betriebs System (**CmdExec**)|  
|**4**|Replikationsmomentaufnahme-Agent|  
|**5@@**|Replikationsprotokolllese-Agent|  
|**6**|Replikationsverteilungs-Agent|  
|**19.00**|Replikationsmerge-Agent|  
|**88**|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|**21.00**|Analysis Services-Abfrage|  
|**€**|Analysis Services-Befehl|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)]Paket Ausführung|  
|**12**|PowerShell-Skript|  
| &nbsp; | &nbsp; |
  
`[ @subsystem_name = ] 'subsystem_name'`Der Name des Subsystems, auf das der Zugriff gewährt werden soll. Der **subsystem_name** ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es muss entweder *subsystem_id* oder *subsystem_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**ActiveScripting**|ActiveX-Skript|  
|**CmdExec**|Betriebs System (**CmdExec**)|  
|**Überblick**|Replikationsmomentaufnahme-Agent|  
|**Protokoll Leser**|Replikationsprotokolllese-Agent|  
|**Distribution**|Replikations Verteilungs-Agent|  
|**Merge** (Zusammenführen)|Replikationsmerge-Agent|  
|**Queue Reader**|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|**ANALYSISQUERY**|Analysis Services-Abfrage|  
|**ANALYSISCOMMAND**|Analysis Services-Befehl|  
|**Dt**|SSIS-Paketausführung|  
|**PowerShell**|PowerShell-Skript|  
| &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Bemerkungen  
 Beim Gewähren eines Proxyzugriffs auf ein Subsystem werden nicht die Berechtigungen für den im Proxy angegebenen Prinzipal geändert.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_grant_proxy_to_subsystem**ausführen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-granting-access-to-a-subsystem-by-id"></a>A. Gewähren von Zugriff auf ein Subsystem nach ID  
 Im folgenden Beispiel wird dem Proxy `Catalog application proxy` der Zugriff auf das ActiveX Scripting-Subsystem gewährt.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_id = 2;  
GO  
```  
  
### <a name="b-granting-access-to-a-subsystem-by-name"></a>B. Gewähren von Zugriff auf ein Subsystem nach Name  
 Im folgenden Beispiel wird dem Proxy `Catalog application proxy` der Zugriff auf das Subsystem SSIS-Paketausführung gewährt.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = N'Catalog application proxy',  
    @subsystem_name = N'Dts' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_revoke_proxy_from_subsystem &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revoke-proxy-from-subsystem-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_update_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-proxy-transact-sql.md)  
  
  
