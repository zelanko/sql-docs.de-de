---
title: Sp_addsrvrolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addsrvrolemember
- sp_addsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addsrvrolemember
ms.assetid: 777f0e09-8ee5-4cb2-a3ac-939d02c3cd22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4c8636eaa9b2d83fcde0596a14cbc6658beaf158
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022450"
---
# <a name="spaddsrvrolemember-transact-sql"></a>sp_addsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt einen Benutzernamen als Mitglied einer festen Serverrolle hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addsrvrolemember [ @loginame= ] 'login'   
    , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @loginame **=** ] **"***Anmeldung***"**  
 Der Name der Anmeldung, die der festen Serverrolle hinzugefügt wird. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. *Anmeldung* kann eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename oder ein Windows-Anmeldename. Sollte der Windows-Anmeldename noch nicht die Zugriffsrechte für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besitzen, so werden diese automatisch erteilt.  
  
 [ @rolename **=** ] **"***Rolle***"**  
 Der Name der festen Serverrolle, der der Anmeldename hinzugefügt wird. *Rolle* ist **Sysname**, hat den Standardwert NULL und muss eine der folgenden Werte sein:  
  
-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin  

## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Anmeldename einer festen Serverrolle hinzugefügt wird, erhält der Anmeldename die Berechtigungen dieser Rolle.  
  
 Die Rollenmitgliedschaft des Anmeldenamens "sa" und öffentliche kann nicht geändert werden.  
  
 Verwenden Sie Sp_addrolemember, um ein Mitglied einer festen Datenbankrolle oder einer benutzerdefinierten Rolle hinzufügen.  
  
 Sp_addsrvrolemember kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Rolle, der das neue Mitglied hinzugefügt wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Windows-Anmeldename `Corporate\HelenS` der festen Serverrolle `sysadmin` hinzugefügt.  
  
```  
EXEC sp_addsrvrolemember 'Corporate\HelenS', 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [Sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [CREATE SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-role-transact-sql.md)  
  
  
