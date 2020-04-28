---
title: xp_grantlogin (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68116671"
---
# <a name="xp_grantlogin-transact-sql"></a>xp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erteilt einer Windows-Gruppe oder einem Windows-Benutzer Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Create Login](../../t-sql/statements/create-login-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_grantlogin {[@loginame = ] 'login'} [,[@logintype = ] 'logintype']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'`Der Name des hinzu zufügenden Windows-Benutzers oder der Windows-Gruppe. Der Windows-Benutzer oder die Windows-Gruppe muss mit einem Windows-Domänen Namen in der Form " *Domäne*\\*Benutzer*" qualifiziert werden. *login* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @logintype = ] 'logintype'`Die Sicherheitsstufe der Anmeldung, für die der Zugriff gewährt wird. *LoginType ist vom Datentyp* **varchar (5)** und hat den Standardwert NULL. Es kann nur **Admin** angegeben werden. Wenn **Admin** angegeben ist, erhält der *Anmelde* Name Zugriff [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf und wird als Mitglied der festen Server Rolle **sysadmin** hinzugefügt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **xp_grantlogin** ist nun eine gespeicherte System Prozedur anstelle einer erweiterten gespeicherten Prozedur. **xp_grantlogin** ruft **sp_grantlogin** und **sp_addsrvrolemember**auf.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **securityadmin** . Wenn *LoginType*geändert wird, ist die Mitgliedschaft in der festen Server Rolle **sysadmin** erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_denylogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_enumgroups &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)  
  
  
