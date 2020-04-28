---
title: sp_msx_get_account (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_get_account_TSQL
- sp_msx_get_account
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_get_account
ms.assetid: 7b478049-e2d0-4bac-865a-b97fd1d8dfbc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3dab15a076200e464e82d0b01ef6a156447a537f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108043"
---
# <a name="sp_msx_get_account-transact-sql"></a>sp_msx_get_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet Informationen zu den Anmeldeinformationen auf, die der Zielserver für die Anmeldung am Masterserver verwendet.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_msx_get_account  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt das folgende Resultset zurück:  
  
|Spaltenname|type|BESCHREIBUNG|  
|-----------------|----------|-----------------|  
|msx_connection|**int**|Nummer der Masterserververbindung|  
|msx_credential_id|**int**|ID der Anmeldeinformationen, die für diese Masterserververbindung verwendet werden.|  
|msx_credential_name|**sysname**|Name der Anmeldeinformationen, die für diese Masterserververbindung verwendet werden.|  
|msx_login_name|**nvarchar(4000)**|Domänenname und Benutzername des Windows-Benutzers für die Anmeldeinformationen.|  
  
## <a name="remarks"></a>Bemerkungen  
 Gibt ein leeres Resultset zurück, wenn für diesen Zielserver keine Anmeldeinformationen angegeben wurden. Verwenden Sie sp_msx_set_account zum Festlegen der Anmeldeinformationen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den Anmeldeinformationen aufgelistet, die der Zielserver für die Anmeldung am Masterserver verwendet.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_get_account ;  
GO  
```  
  
 Im Folgenden finden Sie ein Beispiel für ein Resultset:  
  
 `msx_connection msx_credential_id msx_credential_name  msx_login_name`  
  
 `-------------- ----------------- -------------------- ------------------------------`  
  
 `1              65538             MsxAccount           AdventureWorks2012\MsxAccount`  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Create Credential &#40;Transact-SQL-&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_set_account &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-msx-set-account-transact-sql.md)  
  
  
