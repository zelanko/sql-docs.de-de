---
title: Sp_grant_login_to_proxy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_proxy
- sp_grant_login_to_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_login_to_proxy
ms.assetid: 90e1a6d5-a692-4462-a163-4b0709d83150
ms.author: vanto
manager: craigg
ms.openlocfilehash: c2a34ff49213cbc308f2d315735819e706bd54d6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704768"
---
# <a name="spgrantlogintoproxy-transact-sql"></a>sp_grant_login_to_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gewährt über einen Sicherheitsprinzipal den Zugriff auf einen Proxy.  

  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_grant_login_to_proxy   
     { [ @login_name = ] 'login_name'   
     | [ @fixed_server_role = ] 'fixed_server_role'   
     | [ @msdb_role = ] 'msdb_role' } ,   
     { [ @proxy_id = ] id | [ @proxy_name = ] 'proxy_name' }  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@login_name** =] **"***Login_name***"**  
 Der Anmeldename, für den der Zugriff gewährt werden soll. *login_name* ist vom Datentyp **nvarchar(256)** und hat den Standardwert NULL. Einer der **@login_name**, **@fixed_server_role**, oder **@msdb_role** muss angegeben werden, oder die gespeicherte Prozedur ein Fehler auftritt.  
  
 [ **@fixed_server_role**=] **"***Fixed_server_role***"**  
 Die feste Serverrolle, für die der Zugriff gewährt werden soll. *fixed_server_role* ist vom Datentyp **nvarchar(256)** und hat den Standardwert NULL. Einer der **@login_name**, **@fixed_server_role**, oder **@msdb_role** muss angegeben werden, oder die gespeicherte Prozedur ein Fehler auftritt.  
  
 [ **@msdb_role**=] '*Msdb_role*"  
 Die Datenbankrolle in der **msdb** -Datenbank, für die der Zugriff gewährt werden soll. *msdb_role* ist vom Datentyp **nvarchar(256)** und hat den Standardwert NULL. Einer der **@login_name**, **@fixed_server_role**, oder **@msdb_role** muss angegeben werden, oder die gespeicherte Prozedur ein Fehler auftritt.  
  
 [ **@proxy_id**= ] *id*  
 Der Bezeichner des Proxys, für den der Zugriff erteilt werden soll. *id* ist vom Datentyp **int**und hat den Standardwert NULL. Einer der **@proxy_id** oder **@proxy_name** muss angegeben werden, oder die gespeicherte Prozedur ein Fehler auftritt.  
  
 [ **@proxy_name**=] **"***Proxy_name***"**  
 Der Name des Proxys, für den der Zugriff erteilt werden soll. *proxy_name* ist vom Datentyp **nvarchar(256)** und hat den Standardwert NULL. Einer der **@proxy_id** oder **@proxy_name** muss angegeben werden, oder die gespeicherte Prozedur ein Fehler auftritt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_grant_login_to_proxy** muss von der **msdb** -Datenbank aus ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können **sp_grant_login_to_proxy**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird dem Anmeldenamen `adventure-works\terrid` die Verwendung des Proxys `Catalog application proxy`ermöglicht.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_login_to_proxy  
    @login_name = N'adventure-works\terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
