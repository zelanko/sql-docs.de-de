---
title: sp_adduser (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 9e7ba3827b9a659c0100805d0a9895fad503b2a7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716290"
---
# <a name="sp_adduser-transact-sql"></a>sp_adduser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Fügt der aktuellen Datenbank einen neuen Benutzer hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Create User](../../t-sql/statements/create-user-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adduser [ @loginame = ] 'login'   
    [ , [ @name_in_db = ] 'user' ]   
    [ , [ @grpname = ] 'role' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'`Der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung oder der Windows-Anmeldung. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. *Login* muss ein vorhandener- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Name oder Windows-Anmelde Name sein.  
  
`[ @name_in_db = ] 'user'`Der Name des neuen Daten Bank Benutzers. *User* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der *Benutzer* nicht angegeben ist, wird der Name des neuen Daten Bank Benutzers standardmäßig auf den *Anmelde* Namen festgelegt. Durch Angeben eines *Benutzers* erhält der neue Benutzer einen anderen Namen als den Anmelde Namen auf Serverebene.  
  
`[ @grpname = ] 'role'`Die Daten Bank Rolle, deren Mitglied der neue Benutzer wird. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. die *Rolle* muss eine gültige Daten Bank Rolle in der aktuellen Datenbank sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_adduser** wird auch ein Schema mit dem Namen des Benutzers erstellt.  
  
 Definieren Sie nach dem Hinzufügen eines Benutzers mit den Anweisungen GRANT, DENY und REVOKE die Berechtigungen für die Aktivitäten, die der Benutzer ausführen darf.  
  
 Verwenden Sie **sys. server_principals** , um eine Liste gültiger Anmelde Namen anzuzeigen.  
  
 Verwenden Sie **sp_helprole** , um eine Liste der gültigen Rollennamen anzuzeigen. Bei Angabe einer Rolle erhält der Benutzer automatisch die für diese Rolle definierten Berechtigungen. Wenn keine Rolle angegeben wird, erhält der Benutzer die Berechtigungen, die der standardmäßigen **Public** -Rolle erteilt wurden. Zum Hinzufügen eines Benutzers zu einer Rolle muss ein Wert für den *Benutzernamen* angegeben werden. (der*Benutzername* kann mit *login_id*identisch sein.)  
  
 Der Benutzer **Gast** ist bereits in jeder Datenbank vorhanden. Durch das Hinzufügen des Benutzers **Guest** wird dieser Benutzer aktiviert, wenn er zuvor deaktiviert war. Standardmäßig ist der Benutzer **Gast** in neuen Datenbanken deaktiviert.  
  
 **sp_adduser** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
 Ein **Gast** Benutzer kann nicht hinzugefügt werden, da ein **Gast** Benutzer bereits in jeder Datenbank vorhanden ist. Um den **Gast** Benutzer zu aktivieren, erteilen Sie die Berechtigung **Guest** Connect wie hier gezeigt:  
  
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
 Im folgenden Beispiel wird der Benutzer `Arvind` der aktuellen Datenbank für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen `Arvind` hinzugefügt. Dieser Benutzer gehört zur standardmäßigen **Public** -Rolle.  
  
```  
EXEC sp_adduser 'Arvind';  
```  
  
### <a name="c-adding-a-database-user-with-a-different-name-than-its-server-level-login"></a>C. Hinzufügen eines Datenbankbenutzers mit einem anderen Namen als der Anmeldename auf Serverebene  
 Im folgenden Beispiel wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename `BjornR` der aktuellen Datenbank hinzugefügt, die den Benutzernamen `Bjorn` besitzt. Der Datenbankbenutzer `Bjorn` wird der `Production`-Datenbankrolle hinzugefügt.  
  
```  
EXEC sp_adduser 'BjornR', 'Bjorn', 'Production';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys. server_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [Erstellen eines Benutzer &#40;Transact-SQL-&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
