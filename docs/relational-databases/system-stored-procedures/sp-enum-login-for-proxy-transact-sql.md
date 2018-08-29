---
title: Sp_enum_login_for_proxy (Transact-SQL) | Microsoft-Dokumentation
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
- sp_enum_login_for_proxy_TSQL
- sp_enum_login_for_proxy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_login_for_proxy
ms.assetid: 62a75019-248a-44c8-a5cc-c79f55ea3acf
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7faec16e49bb2776babb126a5f4d314889b70c2b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036272"
---
# <a name="spenumloginforproxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet Zuordnungen zwischen Sicherheitsprinzipalen und Proxys auf.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_enum_login_for_proxy  
    [ @name = ] 'name'  
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@name**=] '*Namen*"  
 Der Name des eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Prinzipal, Anmeldung, Serverrolle oder **Msdb** -Datenbankrolle, für die Proxys aufgelistet werden sollen. Der Name ist **nvarchar(256)**, hat den Standardwert NULL.  
  
 [ **@proxy_id**= ] *id*  
 Die Proxy-ID des Proxys, zu dem die Informationen aufgelistet werden sollen. Die *Proxy_id* ist **Int**, hat den Standardwert NULL. Entweder die *Id* oder *Proxy_name* kann angegeben werden.  
  
 [ **@proxy_name**=] **"***Proxy_name***"**  
 Der Name des Proxys, zu dem Informationen aufgelistet werden sollen. Die *Proxy_name* ist **Sysname**, hat den Standardwert NULL. Entweder die *Id* oder *Proxy_name* kann angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID des Proxys.|  
|**proxy_name**|**sysname**|Der Name des Proxys.|  
|**name**|**sysname**|Name des Sicherheitsprinzipals für die Zuordnung|  
|**flags**|**int**|Typ des Sicherheitsprinzipals.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung<br /><br /> **1** = feste Systemrolle<br /><br /> **2** = Datenbankrolle in **Msdb**|  
  
## <a name="remarks"></a>Hinweise  
 Wenn keine Parameter angegeben werden, **Sp_enum_login_for_proxy** listet Informationen zu allen Anmeldenamen in der Instanz für alle Proxys.  
  
 Wenn eine Proxy-Id oder ein Proxyname angegeben wird, **Sp_enum_login_for_proxy** enthält Anmeldungen, die über Zugriff auf den Proxy. Wenn ein Anmeldename angegeben wird, **Sp_enum_login_for_proxy** Listen die Proxys, die der Anmeldename hat Zugriff auf.  
  
 Wenn sowohl ein Proxy als auch ein Anmeldename angegeben wird, gibt das Resultset eine Zeile zurück, falls der angegebene Anmeldename auf den angegebenen Proxy zugreifen kann.  
  
 Diese gespeicherte Prozedur befindet sich im **Msdb**.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen für diese Prozedur erhalten standardmäßig Mitglieder der **Sysadmin** -Serverrolle sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-associations"></a>A. Auflisten aller Zuordnungen  
 Mit dem folgenden Beispiel werden alle Berechtigungen aufgelistet, die in der aktuellen Instanz zwischen Anmeldenamen und Proxys eingerichtet wurden.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy ;  
GO  
```  
  
### <a name="b-listing-proxies-for-a-specific-login"></a>B. Auflisten von Proxys für einen bestimmten Anmeldenamen  
 Mit dem folgenden Beispiel werden die Proxys aufgelistet, auf die der Anmeldename `terrid` zugreifen kann.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy  
    @name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_help_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
