---
title: Sp_revokelogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 2763b573eff741575c1d496efb0e861472714823
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533002"
---
# <a name="sprevokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt die anmeldenameneinträge in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für eine Windows-Benutzer oder Gruppe, die mit CREATE LOGIN auf, erstellt **Sp_grantlogin**, oder **Sp_denylogin**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) .  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'` Ist der Name des Windows-Benutzers oder der Gruppe. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. *Anmeldung* möglich, alle vorhandenen Windows-Benutzernamen oder die Gruppe im Format *Computername*\\*Benutzer- oder Domänenkonto*\\*Benutzer*.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_revokelogin** deaktiviert Verbindungen mithilfe des Kontos, das gemäß der *Anmeldung* Parameter. Windows-Benutzer, denen der Zugriff auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über die Mitgliedschaft in einer Windows-Gruppe erteilt wurde, können jedoch weiterhin als Gruppe eine Verbindung herstellen, nachdem ihr individueller Zugriff aufgehoben wurde. Auf ähnliche Weise, wenn die *Anmeldung* Parameter gibt den Namen einer Windows-Gruppe, Mitglieder dieser Gruppe, die getrennt wurden gewährt Zugriff auf die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden weiterhin eine Verbindung herstellen können.  
  
 Zum Beispiel wenn Windows-Benutzer **ADVWORKS\john** ist ein Mitglied der Gruppe "Windows" **ADVWORKS\Admins**, und **Sp_revokelogin** hebt den Zugriff von `ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 Benutzer **ADVWORKS\john** lässt dennoch verbinden, wenn **ADVWORKS\Admins** hat Zugriff gewährt wurde mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Auf ähnliche Weise, wenn Windows-Gruppe **ADVWORKS\Admins** der Zugriff aufgehoben, aber **ADVWORKS\john** wird Zugriff erteilt wurde, **ADVWORKS\john** können weiterhin eine Verbindung herstellen.  
  
 Verwendung **Sp_denylogin** explizit verhindern Benutzer Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], unabhängig von ihrer Windows-Gruppenmitgliedschaft.  
  
 **Sp_revokelogin** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Anmeldenameneinträge für die Windows-Benutzerin `Corporate\MollyA` entfernt.  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 oder  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
