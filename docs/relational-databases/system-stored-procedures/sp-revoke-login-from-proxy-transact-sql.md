---
title: sp_revoke_login_from_proxy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revoke_login_from_proxy_TSQL
- sp_revoke_login_from_proxy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revoke_login_from_proxy
ms.assetid: e4546c13-9fba-4bab-8b42-d6f18b33ec25
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0819dbe8c2b4f76e638c09861d83ddb37e76da31
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899232"
---
# <a name="sp_revoke_login_from_proxy-transact-sql"></a>sp_revoke_login_from_proxy (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt den Zugriff auf einen Proxy für ein Sicherheitsprinzipal.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_revoke_login_from_proxy   
    [ @name = ] 'name' ,  
    [ @proxy_id = ] id ,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'`Der Name der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung, Server Rolle oder **msdb** -Daten Bank Rolle, für die der Zugriff entfernt werden soll. *Name ist vom Datentyp* **nvarchar (256)** und hat keinen Standardwert.  
  
`[ @proxy_id = ] id`Die ID des Proxys, für den der Zugriff entfernt werden soll. Es muss entweder eine *ID* oder eine *proxy_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. *id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys, für den der Zugriff entfernt werden soll. Es muss entweder eine *ID* oder eine *proxy_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Aufträge im Besitz des Anmeldenamens, der auf diesen Proxy verweist, schlagen fehl.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss ein Benutzer Mitglied der festen Serverrolle **sysadmin** sein.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Zugriff auf den Proxy `terrid` für den Anmeldenamen `Catalog application proxy` aufgehoben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_login_from_proxy  
    @name = N'terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_help_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)  
  
  
