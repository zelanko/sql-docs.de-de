---
title: sp_revokelogin (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: f7b0c3e906fdd9576970ed1e8dfd69893b0759a0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750473"
---
# <a name="sp_revokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Entfernt die Anmelde Einträge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für einen Windows-Benutzer oder eine Windows-Gruppe, die mit Create Login, **sp_grantlogin**oder **sp_denylogin**erstellt wurde.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Drop Login](../../t-sql/statements/drop-login-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'`Der Name des Windows-Benutzers oder der Windows-Gruppe. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. " *Login* " kann ein beliebiger Windows-Benutzername oder eine Gruppe im Format " *Computer Name* \\ *Benutzer" oder "Domäne* \\ *Benutzer*" sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_revokelogin** deaktiviert Verbindungen unter Verwendung des durch den *Login* -Parameter angegebenen Kontos. Windows-Benutzer, denen der Zugriff auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über die Mitgliedschaft in einer Windows-Gruppe erteilt wurde, können jedoch weiterhin als Gruppe eine Verbindung herstellen, nachdem ihr individueller Zugriff aufgehoben wurde. Wenn der *Login* -Parameter den Namen einer Windows-Gruppe angibt, können auch Mitglieder dieser Gruppe, denen der Zugriff auf die Instanz von separat gewährt wurde, weiterhin eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung herstellen.  
  
 Wenn beispielsweise der Windows-Benutzer " **ADVWORKS\john** " Mitglied der Windows-Gruppe " **ADVWORKS\Admins**" ist, und **sp_revokelogin** widerruft den Zugriff auf `ADVWORKS\john` :  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 Der Benutzer " **ADVWORKS\john** " kann immer noch eine Verbindung herstellen, wenn " **ADVWORKS\Admins** " Zugriff auf eine Instanz von gewährt wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ebenso kann, wenn die Windows-Gruppe **ADVWORKS\Admins** den Zugriff widerrufen hat, aber **ADVWORKS\john** Zugriff gewährt wird, **ADVWORKS\john** immer noch eine Verbindung herstellen.  
  
 Verwenden Sie **sp_denylogin** , um explizit zu verhindern, dass Benutzer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unabhängig von Ihren Windows-Gruppenmitgliedschaften eine Verbindung mit einer Instanz von herstellen.  
  
 **sp_revokelogin** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Drop Login &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
