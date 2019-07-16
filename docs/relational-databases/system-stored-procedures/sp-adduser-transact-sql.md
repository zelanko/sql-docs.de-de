---
title: Sp_adduser (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_adduser
- sp_adduser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adduser
ms.assetid: 61a40eb4-573f-460c-9164-bd1bbfaf8b25
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a2984479c8a1be35f8ccfa63d14b3250939f56c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68117901"
---
# <a name="spadduser-transact-sql"></a>sp_adduser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt der aktuellen Datenbank einen neuen Benutzer hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) .  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adduser [ @loginame = ] 'login'   
    [ , [ @name_in_db = ] 'user' ]   
    [ , [ @grpname = ] 'role' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'` Der Name des der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung oder Windows-Anmeldung. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. *Anmeldung* muss einer vorhandenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung oder Windows-Anmeldung.  
  
`[ @name_in_db = ] 'user'` Ist der Name für den neuen Datenbankbenutzer. *Benutzer* ist eine **Sysname**, hat den Standardwert NULL. Wenn *Benutzer* nicht angegeben ist, der Namen des neuen Datenbankbenutzers standardmäßig die *Anmeldung* Name. Angeben von *Benutzer* benennt dem neuen Benutzer mit einem Namen in der Datenbank, die den Anmeldenamen auf Serverebene unterscheidet.  
  
`[ @grpname = ] 'role'` Ist die Datenbankrolle, die Mitglied der neue Benutzer wird. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. *Rolle* muss eine gültige Datenbankrolle in der aktuellen Datenbank sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_adduser** erstellt auch ein Schema mit dem Namen des Benutzers ab.  
  
 Definieren Sie nach dem Hinzufügen eines Benutzers mit den Anweisungen GRANT, DENY und REVOKE die Berechtigungen für die Aktivitäten, die der Benutzer ausführen darf.  
  
 Verwendung **Sys. server_principals** um eine Liste gültiger Anmeldenamen anzuzeigen.  
  
 Verwendung **Sp_helprole** um eine Liste der gültigen Rollennamen anzuzeigen. Bei Angabe einer Rolle erhält der Benutzer automatisch die für diese Rolle definierten Berechtigungen. Wenn eine Rolle nicht angegeben wird, erhält der Benutzer die Berechtigungen, die auf den Standardwert **öffentliche** Rolle. Zum Hinzufügen eines Benutzers zu einer Rolle, die einen Wert für die *Benutzernamen* muss angegeben werden. (*Benutzername* können identisch sein *Login_id*.)  
  
 Benutzer **Gast** bereits in jeder Datenbank vorhanden ist. Hinzufügen eines Benutzers **Gast** wird dieser aktiviert, wenn sie zuvor deaktiviert war. In der Standardeinstellung Benutzer **Gast** ist in neuen Datenbanken deaktiviert.  
  
 **Sp_adduser** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
 Sie können nicht hinzugefügt werden eine **Gast** Benutzer da eine **Gast** Benutzer, die bereits in jeder Datenbank vorhanden ist. So aktivieren Sie die **Gast** Benutzer, Grant **Gast** CONNECT-Berechtigung wie folgt:  
  
```  
GRANT CONNECT TO guest;  
GO  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert den Besitz der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-adding-a-database-user"></a>A. Hinzufügen eines Datenbankbenutzers  
 Im folgenden Beispiel wird der Datenbankbenutzer `Vidur` der vorhandenen Rolle `Recruiting` in der aktuellen Datenbank hinzugefügt, wobei der vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename `Vidur` verwendet wird.  
  
```  
EXEC sp_adduser 'Vidur', 'Vidur', 'Recruiting';  
```  
  
### <a name="b-adding-a-database-user-with-the-same-login-id"></a>B. Hinzufügen eines Datenbankbenutzers mit der gleichen Anmelde-ID  
 Im folgenden Beispiel wird der Benutzer `Arvind` der aktuellen Datenbank für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen `Arvind` hinzugefügt. Dieser Benutzer gehört, auf den Standardwert **öffentliche** Rolle.  
  
```  
EXEC sp_adduser 'Arvind';  
```  
  
### <a name="c-adding-a-database-user-with-a-different-name-than-its-server-level-login"></a>C. Hinzufügen eines Datenbankbenutzers mit einem anderen Namen als der Anmeldename auf Serverebene  
 Im folgenden Beispiel wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename `BjornR` der aktuellen Datenbank hinzugefügt, die den Benutzernamen `Bjorn` besitzt. Der Datenbankbenutzer `Bjorn` wird der `Production`-Datenbankrolle hinzugefügt.  
  
```  
EXEC sp_adduser 'BjornR', 'Bjorn', 'Production';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
