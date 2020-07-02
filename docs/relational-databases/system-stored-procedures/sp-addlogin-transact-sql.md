---
title: sp_addlogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addlogin
- sp_addlogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlogin
ms.assetid: 030f19c3-a5e3-4b53-bfc4-de4bfca0fddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 06629b059afffe3baa0a34caec1337d7bc3f2517
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757996"
---
# <a name="sp_addlogin-transact-sql"></a>sp_addlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Erstellt einen neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen, der es einem Benutzer ermöglicht, eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung herzustellen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Create Login](../../t-sql/statements/create-login-transact-sql.md) .  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addlogin [ @loginame = ] 'login'   
    [ , [ @passwd = ] 'password' ]   
    [ , [ @defdb = ] 'database' ]   
    [ , [ @deflanguage = ] 'language' ]   
    [ , [ @sid = ] sid ]   
    [ , [ @encryptopt = ] 'encryption_option' ]   
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @loginame =] '*Login*'  
 Der Name der Anmeldung. *login* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [ @passwd =] '*Kennwort*'  
 Das Anmelde Kennwort. *Password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 [ @defdb =] '*Datenbank*'  
 Ist die Standarddatenbank des Anmeldenamens (die Datenbank, mit der der Anmeldename nach dem Anmelden zuerst verbunden wird). *Database* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **Master**.  
  
 [ @deflanguage =] '*Sprache*'  
 Die Standardsprache der Anmeldung. *language* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *Language* nicht angegeben wird, wird die Standard *Sprache* des neuen Anmelde namens auf die aktuelle Standardsprache des Servers festgelegt.  
  
 [ @sid =] '*sid*'  
 Die Sicherheits-ID (SID). *sid* ist vom Datentyp **varbinary (16)** und hat den Standardwert NULL. Wenn *sid* den Wert NULL hat, generiert das System eine sid für den neuen Anmelde Namen. Trotz der Verwendung eines **varbinary** -Datentyps müssen andere Werte als NULL genau 16 Byte lang sein und dürfen nicht bereits vorhanden sein. Die Angabe von *sid* ist beispielsweise nützlich, wenn Sie Skripts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einem Server auf einen anderen übertragen oder die Anmelde Namen von einem Server auf einen anderen verschieben, und Sie möchten, dass die Anmeldungen auf verschiedenen Servern dieselbe SID haben.  
  
 [ @encryptopt =] '*encryption_option*'  
 Gibt an, ob das Kennwort als Klartext oder als Hash des Klartextkennworts weitergegeben wird. Dabei ist zu beachten, dass keine Verschlüsselung stattfindet. Der Begriff "verschlüsseln" wird in diesem Zusammenhang aus Gründen der Abwärtskompatibilität verwendet. Wenn ein Klartextkennwort übergeben wird, geschieht dies in Form eines Hashs. Der Hash wird gespeichert. *encryption_option* ist vom Datentyp **varchar (20)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|NULL|Das Kennwort wird als Klartext übergeben. Dies ist die Standardeinstellung.|  
|**skip_encryption**|Es wurde bereits ein Hashwert aus dem Kennwort erstellt. [!INCLUDE[ssDE](../../includes/ssde-md.md)] sollte den Wert ohne erneutes Hashing speichern.|  
|**skip_encryption_old**|Es wurde ein Hashwert des bereitgestellten Kennworts von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt. [!INCLUDE[ssDE](../../includes/ssde-md.md)] sollte den Wert ohne erneutes Hashing speichern. Diese Option dient lediglich Upgradezwecken.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen können zwischen 1 und 128 Zeichen (einschließlich Buchstaben, Sonderzeichen und Ziffern) enthalten. Anmeldungen dürfen keinen umgekehrten Schrägstrich ( \\ ) enthalten. Sie müssen ein reservierter Anmelde Name sein, z. b. SA oder Public, oder Sie sind bereits vorhanden, oder NULL oder eine leere Zeichenfolge ( `''` ).  
  
 Wenn der Name einer Standarddatenbank angegeben wird, ist die Verbindung mit dieser Datenbank ohne das Ausführen der USE-Anweisung möglich. Es ist jedoch nicht möglich, die Standarddatenbank zu verwenden, bis Sie vom Datenbankbesitzer (mithilfe von [sp_adduser](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md) oder [sp_addrolemember](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)) oder [sp_addrole](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)Zugriff auf diese Datenbank erhalten.  
  
 Die SID ist ein GUID, die den Anmeldenamen auf dem Server eindeutig identifiziert.  
  
 Wird die Standardsprache des Servers geändert, ändert sich dadurch nicht die Standardsprache der bestehenden Anmeldenamen. Verwenden Sie [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md), um die Standardsprache des Servers zu ändern.  
  
 Das Verwenden von **skip_encryption** zum Unterdrücken von Kenn Wort Hash ist nützlich, wenn das Kennwort beim Hinzufügen des Anmelde namens zu bereits Hashwert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn für das Kennwort eine frühere Version von verwendet wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , verwenden Sie **skip_encryption_old**.  
  
 sp_addlogin kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
 In der folgenden Tabelle werden verschiedene gespeicherte Prozeduren angezeigt, die mit sp_addlogin verwendet werden.  
  
|Gespeicherte Prozedur|BESCHREIBUNG|  
|----------------------|-----------------|  
|[sp_grantlogin](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)|Fügt einen Windows-Benutzer oder eine Windows-Gruppe hinzu.|  
|[sp_password](../../relational-databases/system-stored-procedures/sp-password-transact-sql.md)|Ändert das Kennwort eines Benutzers.|  
|[sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)|Ändert die Standarddatenbank eines Benutzers.|  
|[sp_defaultlanguage](../../relational-databases/system-stored-procedures/sp-defaultlanguage-transact-sql.md)|Ändert die Standardsprache eines Benutzers.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-sql-server-login"></a>A. Erstellen einer SQL Server-Anmeldung  
 Im folgenden Beispiel wird ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename für den Benutzer `Victoria` mit dem Kennwort `B1r12-36` erstellt, ohne dass eine Standarddatenbank angegeben wird.  
  
```  
EXEC sp_addlogin 'Victoria', 'B1r12-36';  
GO  
```  
  
### <a name="b-creating-a-sql-server-login-that-has-a-default-database"></a>B. Erstellen einer SQL Server-Anmeldung mit einer Standarddatenbank  
 Im folgenden Beispiel wird ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename für den Benutzer `Albert` mit dem Kennwort `B5432-3M6` erstellt; dabei wird `corporate` als Standarddatenbank angegeben.  
  
```  
EXEC sp_addlogin 'Albert', 'B5432-3M6', 'corporate';  
GO  
```  
  
### <a name="c-creating-a-sql-server-login-that-has-a-different-default-language"></a>C. Erstellen einer SQL Server-Anmeldung mit einer anderen Standardsprache  
 Im folgenden Beispiel wird ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename für den Benutzer `TzTodorov` mit dem Kennwort `709hLKH7chjfwv` erstellt; dabei werden `AdventureWorks2012` als Standarddatenbank und `Bulgarian` als Standardsprache angegeben.  
  
```  
EXEC sp_addlogin 'TzTodorov', '709hLKH7chjfwv', 'AdventureWorks2012', N'български'  
```  
  
### <a name="d-creating-a-sql-server-login-that-has-a-specific-sid"></a>D: Erstellen einer SQL Server-Anmeldung mit einer bestimmten SID  
 Im folgenden Beispiel wird ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename für den Benutzer `Michael` mit dem Kennwort `B548bmM%f6` erstellt; dabei werden `AdventureWorks2012` als Standarddatenbank, `us_english` als Standardsprache und `0x0123456789ABCDEF0123456789ABCDEF` als SID angegeben.  
  
```  
EXEC sp_addlogin 'Michael', 'B548bmM%f6', 'AdventureWorks2012', 'us_english', 0x0123456789ABCDEF0123456789ABCDEF  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen der Anmeldung &#40;Transact-SQL-&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
