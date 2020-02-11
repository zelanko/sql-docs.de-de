---
title: sp_change_users_login (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/13/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_users_login
- sp_change_users_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_users_login
ms.assetid: 1554b39f-274b-4ef8-898e-9e246b474333
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0594066f044288757e5e31f8e078fabb4c2f3775
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68120228"
---
# <a name="sp_change_users_login-transact-sql"></a>sp_change_users_login (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ordnet einen vorhandenen Datenbankbenutzer einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen zu. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Alter User](../../t-sql/statements/alter-user-transact-sql.md) .  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_change_users_login [ @Action = ] 'action'   
    [ , [ @UserNamePattern = ] 'user' ]   
    [ , [ @LoginName = ] 'login' ]   
    [ , [ @Password = ] 'password' ]  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @Action= ] "*Action*"  
 Beschreibt die von der Prozedur durchzuführende Aktion. *Action* ist vom Datentyp **varchar (10)**. die *Aktion* kann einen der folgenden Werte aufweisen.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Auto_Fix**|Verknüpft einen Benutzereintrag in der sys.database_principals-Systemkatalogsicht in der aktuellen Datenbank mit einem gleichlautenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen. Ist kein gleichlautender Anmeldename vorhanden, wird er erstellt. Überprüfen Sie das Ergebnis der **Auto_Fix** -Anweisung, um zu bestätigen, dass tatsächlich der richtige Link erstellt wurde. Vermeiden Sie die Verwendung von **Auto_Fix** in sicherheitsrelevanten Situationen.<br /><br /> Wenn Sie **Auto_Fix**verwenden, müssen Sie *Benutzer* und *Kennwort* angeben, wenn die Anmeldung nicht bereits vorhanden ist. andernfalls müssen Sie den *Benutzer* angeben, aber das *Kennwort* wird ignoriert. der *Anmelde* Name muss NULL sein. der *Benutzer* muss ein gültiger Benutzer in der aktuellen Datenbank sein. Dem Anmeldenamen kann kein anderer Benutzer zugeordnet werden.|  
|**Report**|Listet die Benutzer und entsprechenden Sicherheits-IDs (SIDs) in der aktuellen Datenbank auf, die mit keinem Anmeldenamen verknüpft sind. *Benutzer*, *Anmelde*Name und *Kennwort* müssen NULL oder nicht angegeben sein.<br /><br /> Um die Berichts Option durch eine Abfrage mithilfe der Systemtabellen zu ersetzen, vergleichen Sie die Einträge in **sys. server_prinicpals** mit den Einträgen in **sys. database_principals**.|  
|**Update_One**|Verknüpft den angegebenen *Benutzer* in der aktuellen Datenbank mit einem vorhandenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Anmelde*Namen. *Benutzer* und *Anmeldung* müssen angegeben werden. Das *Kennwort* muss NULL oder nicht angegeben sein.|  
  
 [ @UserNamePattern= ] "*Benutzer*"  
 Der Name eines Benutzers in der aktuellen Datenbank. *User* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 [ @LoginName= ] "*Login*"  
 Der Name einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung. *Login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 [ @Password= ] '*Kennwort*'  
 Das Kennwort, das einem neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Namen zugewiesen wird, der durch Angabe von **Auto_Fix**erstellt wird. Wenn bereits ein entsprechender Anmelde Name vorhanden ist, werden der Benutzer und der Anmelde Name zugeordnet, und das *Kennwort* wird ignoriert. Wenn keine übereinstimmende Anmeldung vorhanden ist, erstellt sp_change_users_login einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neuen Anmelde Namen *und weist das Kennwort* als Kennwort für den neuen Anmelde Namen zu. *Password* ist vom **Datentyp vom Datentyp sysname**und darf nicht NULL sein.  
  
> **WICHTIG!** Verwenden Sie immer ein sicheres [Kennwort!](../../relational-databases/security/strong-passwords.md)
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|UserName|**sysname**|Datenbank-Benutzername.|  
|UserSID|**varbinary(85)**|Sicherheits-ID des Benutzers.|  
  
## <a name="remarks"></a>Bemerkungen  
 Mithilfe von sp_change_users_login kann ein Datenbankbenutzer in der aktuellen Datenbank mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verknüpft werden. Wenn sich der Anmeldename für einen Benutzer geändert hat, verknüpfen Sie den Benutzer mithilfe von sp_change_users_login mit dem neuen Anmeldenamen, ohne die Benutzerberechtigungen zu verlieren. Der neue *Anmelde* Name kann nicht SA sein, und der *Benutzer*darf nicht dbo, Guest oder ein INFORMATION_SCHEMA Benutzer sein.  
  
 sp_change_users_login kann nicht zum Erstellen einer Zuordnung zwischen Datenbankbenutzern und Prinzipalen, Zertifikaten oder asymmetrischen Schlüsseln auf Windows-Ebene verwendet werden.  
  
 sp_change_users_login kann nicht mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung, die anhand eines Windows-Prinzipals erstellt wurde, oder mit einer vom Benutzer (mithilfe von CREATE USER WITHOUT LOGIN) erstellten Anmeldung verwendet werden.  
  
 sp_change_users_login kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner". Nur Mitglieder der festen Server Rolle sysadmin können die **Auto_Fix** -Option angeben.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-showing-a-report-of-the-current-user-to-login-mappings"></a>A. Anzeigen eines Berichts der aktuellen Zuordnungen zwischen Benutzern und Anmeldenamen  
 Im folgenden Beispiel wird ein Bericht über die Benutzer in der aktuellen Datenbank und ihre Sicherheits-IDs erstellt.  
  
```  
EXEC sp_change_users_login 'Report';  
```  
  
### <a name="b-mapping-a-database-user-to-a-new-sql-server-login"></a>B. Zuordnen eines Datenbankbenutzers zu einer neuen SQL Server-Anmeldung  
 Im folgenden Beispiel wird ein Datenbankbenutzer einem neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen zugeordnet. Datenbankbenutzer `MB-Sales`, der zunächst einem anderen Anmeldenamen zugeordnet ist, wird dem Anmeldenamen `MaryB` zugeordnet.  
  
```  
--Create the new login.  
CREATE LOGIN MaryB WITH PASSWORD = '982734snfdHHkjj3';  
GO  
--Map database user MB-Sales to login MaryB.  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Update_One', 'MB-Sales', 'MaryB';  
GO  
```  
  
### <a name="c-automatically-mapping-a-user-to-a-login-creating-a-new-login-if-it-is-required"></a>C. Automatisches Zuordnen eines Benutzers zu einer Anmeldung und ggf. Erstellen einer neuen Anmeldung  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe von `Auto_Fix` eine Zuordnung zwischen einem vorhandenen Benutzer und einem gleichlautenden Anmeldenamen erstellt wird oder wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename `Mary` mit dem Kennwort `B3r12-3x$098f6` erstellt wird, wenn der Anmeldename `Mary` nicht vorhanden ist.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Auto_Fix', 'Mary', NULL, 'B3r12-3x$098f6';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Erstellen der Anmeldung &#40;Transact-SQL-&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_helplogins &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
