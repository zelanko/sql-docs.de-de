---
title: sp_revoke_proxy_from_subsystem (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
ms.openlocfilehash: 5c8dc5e9a20c9a00b840ec51d3339299cc3756a3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901383"
---
# <a name="sp_revoke_proxy_from_subsystem-transact-sql"></a>sp_revoke_proxy_from_subsystem (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Hebt den Zugriff auf ein Subsystem für einen Proxy auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_revoke_proxy_from_subsystem   
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_id = ] id`Die Proxy-ID des Proxys, von dem der Zugriff widerrufen werden soll. Der *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *proxy_id* oder *proxy_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys, dessen Zugriff aufgehoben werden soll. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es muss entweder *proxy_id* oder *proxy_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @subsystem_id = ] id`Die ID des Subsystems, auf das der Zugriff widerrufen werden soll. Der *subsystem_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *subsystem_id* oder *subsystem_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**2**|ActiveX-Skript<br /><br /> Wichtig das ActiveX Scripting-Subsystem wird in einer zukünftigen Version von aus dem-Agent entfernt ** \* . \* \* \* ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.|  
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
  
`[ @subsystem_name = ] 'subsystem_name'`Der Name des Subsystems, für das der Zugriff aufgehoben werden soll. Der *subsystem_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es muss entweder *subsystem_id* oder *subsystem_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|ActiveScripting|ActiveX-Skript|  
|CmdExec|Betriebssystem (CmdExec)|  
|Snapshot|Replikationsmomentaufnahme-Agent|  
|LogReader|Replikationsprotokolllese-Agent|  
|Verteilung|Replikationsverteilungs-Agent|  
|Merge|Replikationsmerge-Agent|  
|QueueReader|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|ANALYSISQUERY|Analysis Services-Befehl|  
|ANALYSISCOMMAND|Analysis Services-Abfrage|  
|Dts|[!INCLUDE[ssIS](../../includes/ssis-md.md)]-Paketausführung|  
|PowerShell|PowerShell-Skript|  
  
## <a name="remarks"></a>Hinweise  
 Mit dem Aufheben des Zugriffs auf ein Subsystem werden nicht die Berechtigungen für den im Proxy angegebenen Prinzipal geändert.  
  
> [!NOTE]  
>  Um zu ermitteln, welche Auftrags Schritte auf einen Proxy verweisen, klicken Sie mit der rechten Maustaste auf den Knoten **Proxies** unter **SQL Server-Agent** in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und klicken Sie dann auf **Eigenschaften**. Wählen Sie im Dialogfeld **Eigenschaften von Proxy Konto** die Seite **Verweise** aus, um alle Auftrags Schritte anzuzeigen, die auf diesen Proxy verweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_revoke_proxy_from_subsystem**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Zugriff auf das [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Subsystem für den Proxy `Catalog application proxy` aufgehoben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_proxy_from_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_name = N'Dts';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Implementieren SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
