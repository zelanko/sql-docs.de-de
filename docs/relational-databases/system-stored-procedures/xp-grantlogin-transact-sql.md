---
title: Xp_grantlogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_grantlogin
- xp_grantlogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_grantlogin
ms.assetid: c851c1ab-3b29-4b99-9902-78c2665a844b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 957bbdc43c0f0adf3a545fee76e9f69df130d8f9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116671"
---
# <a name="xpgrantlogin-transact-sql"></a>xp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erteilt einer Windows-Gruppe oder einem Windows-Benutzer Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_grantlogin {[@loginame = ] 'login'} [,[@logintype = ] 'logintype']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'` Ist der Name des Windows-Benutzer oder der Gruppe hinzugefügt werden. Windows-Benutzers oder der Gruppe muss mit einem Windows-Domänennamen im Format qualifiziert werden *Domäne*\\*Benutzer*. *login* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @logintype = ] 'logintype'` Wird die Sicherheitsstufe der Anmeldung den Zugriff gewährt. *LoginType* ist **varchar(5)** , hat den Standardwert NULL. Nur **Admin** kann angegeben werden. Wenn **Admin** angegeben wird, *Anmeldung* erhält Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und als Mitglied hinzugefügt der **Sysadmin** -Serverrolle sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Xp_grantlogin** ist jetzt eine Systemprozedur statt einer erweiterten gespeicherten Prozedur gespeicherte. **Xp_grantlogin** Aufrufe **Sp_grantlogin** und **Sp_addsrvrolemember**.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **securityadmin** . Beim Ändern der *Logintype*, erfordert die Mitgliedschaft in der **Sysadmin** -Serverrolle sein.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte allgemeine erweiterte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [Xp_enumgroups &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)  
  
  
