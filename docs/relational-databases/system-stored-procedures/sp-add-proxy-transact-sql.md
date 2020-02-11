---
title: sp_add_proxy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_proxy
- sp_add_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE PROXY statement
- sp_add_proxy
ms.assetid: cb59df37-f103-439b-bec1-2871fb669a8b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4aa4120db7b45cb0b3a7d7a10bb53931b8300d9d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088465"
---
# <a name="sp_add_proxy-transact-sql"></a>sp_add_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt den angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Proxy hinzu.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_proxy  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description' ,  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @proxy_id = ] id OUTPUT   
```  
  
## <a name="arguments"></a>Argumente  
`[ @proxy_name = ] 'proxy_name'`Der Name des zu erstellenden Proxys. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn die *proxy_name* NULL oder eine leere Zeichenfolge ist, wird der Name des Proxys standardmäßig auf den angegebenen *user_name* eingestellt.  
  
`[ @enabled = ] is_enabled`Gibt an, ob der Proxy aktiviert ist. Das *is_enabled* -Flag ist vom Datentyp **tinyint**. der Standardwert ist 1. Wenn *is_enabled* **0**ist, ist der Proxy nicht aktiviert und kann nicht von einem Auftrags Schritt verwendet werden.  
  
`[ @description = ] 'description'`Eine Beschreibung des Proxys. Die Beschreibung ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL. Mit der Beschreibung können Sie den Proxy dokumentieren. Sie erfüllt keine weiteren Aufgaben für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent. Daher ist dieses Argument optional.  
  
`[ @credential_name = ] 'credential_name'`Der Name der Anmelde Informationen für den Proxy. Der *credential_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es muss entweder *credential_name* oder *credential_id* angegeben werden.  
  
`[ @credential_id = ] credential_id`Die Identifikationsnummer der Anmelde Informationen für den Proxy. Der *credential_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *credential_name* oder *credential_id* angegeben werden.  
  
`[ @proxy_id = ] id OUTPUT`Die Proxy-ID, die dem Proxy zugewiesen wird, wenn er erfolgreich erstellt wurde.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Diese gespeicherte Prozedur muss in der **msdb** -Datenbank ausgeführt werden.  
  
 Von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Proxy wird die Sicherheit für Auftragsschritte verwaltet, die andere Subsysteme als das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Subsystem verwenden. Jeder Proxy entspricht einem Satz Sicherheitsanmeldeinformationen. Ein Proxy kann über Zugriff auf eine beliebige Anzahl von Subsystemen verfügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Sicherheitsrolle **sysadmin** können diese Prozedur ausführen.  
  
 Mitglieder der festen Sicherheitsrolle **sysadmin** können Auftrags Schritte erstellen, die einen beliebigen Proxy verwenden. Verwenden Sie die gespeicherte Prozedur [sp_grant_login_to_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md) , um anderen Anmeldungen Zugriff auf den Proxy zu gewähren.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird ein Proxy für die Anmeldeinformationen `CatalogApplicationCredential` erstellt. Es wird im Code vorausgesetzt, dass die Anmeldeinformationen bereits vorhanden sind. Weitere Informationen zu Anmelde Informationen finden Sie unter [Create Credential &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 1,  
    @description = 'Maintenance tasks on catalog application.',  
    @credential_name = 'CatalogApplicationCredential' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
