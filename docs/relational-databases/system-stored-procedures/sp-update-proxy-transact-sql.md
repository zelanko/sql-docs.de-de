---
title: sp_update_proxy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_proxy
- sp_update_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROXY statement
- sp_update_proxy
ms.assetid: 864fd0e6-9d61-4f07-92ef-145318d2f881
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ec6c40abd080c86722565762fab3b4f9d30bd0c0
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305306"
---
# <a name="sp_update_proxy-transact-sql"></a>sp_update_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Eigenschaften eines vorhandenen Proxys.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @new_name = ] 'new_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_id = ] id` die Proxy-ID des zu ändernden Proxys. Der *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @proxy_name = ] 'proxy_name'` den Namen des zu ändernden Proxys an. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @credential_name = ] 'credential_name'` den Namen der neuen Anmelde Informationen für den Proxy. Der *credential_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es können entweder *credential_name* oder *credential_id* angegeben werden.  
  
`[ @credential_id = ] credential_id` die Identifikationsnummer der neuen Anmelde Informationen für den Proxy. Der *credential_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es können entweder *credential_name* oder *credential_id* angegeben werden.  
  
`[ @new_name = ] 'new_name'` den neuen Namen des Proxys an. Der *new_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn bereitgestellt, ändert die Prozedur den Namen des Proxys in *new_name*. Wenn für das Argument NULL festgelegt wird, bleibt der Name des Proxys unverändert.  
  
`[ @enabled = ] is_enabled` gibt an, ob der Proxy aktiviert ist. Das *is_enabled* -Flag ist vom Datentyp **tinyint**. der Standardwert ist NULL. Wenn *is_enabled* **0**ist, ist der Proxy nicht aktiviert und kann nicht von einem Auftrags Schritt verwendet werden. Wird für das Argument NULL festgelegt, bleibt der Status des Proxys unverändert.  
  
`[ @description = ] 'description'` die neue Beschreibung des Proxys. Die *Beschreibung* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL. Wenn für das Argument NULL festgelegt wird, bleibt die Beschreibung des Proxys unverändert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Remarks  
 Es muss entweder **\@proxy_name** oder **\@proxy_id** angegeben werden. Wenn beide Argumente angegeben werden, müssen sie sich beide auf denselben Proxy beziehen. Andernfalls erzeugt die gespeicherte Prozedur einen Fehler.  
  
 Es muss entweder **\@credential_name** oder **\@credential_id** angegeben werden, um die Anmelde Informationen für den Proxy zu ändern. Wenn beide Argumente angegeben werden, müssen sich beide auf dieselben Anmeldeinformationen beziehen, andernfalls erzeugt die gespeicherte Prozedur einen Fehler.  
  
 Mit dieser Prozedur wird der Proxy geändert, jedoch nicht der Zugriff auf den Proxy. Verwenden Sie **sp_grant_login_to_proxy** und **sp_revoke_login_from_proxy**, um den Zugriff auf einen Proxy zu ändern.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Sicherheitsrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der aktivierte Wert für den Proxy `Catalog application proxy` auf `0` festgelegt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 0;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent gespeicherte Prozeduren &#40;Transact&#41; -SQL](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md) -   
 [Implementieren SQL Server-Agent Sicherheits](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
