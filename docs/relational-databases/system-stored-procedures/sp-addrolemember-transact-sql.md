---
title: sp_addrolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrolemember_TSQL
- sp_addrolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrolemember
ms.assetid: a583c087-bdb3-46d2-b9e5-3921b3e6d10b
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c9e0d3152c6d60faff4c1c42410374287bd7d111
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030902"
---
# <a name="sp_addrolemember-transact-sql"></a>sp_addrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Fügt einer Datenbankrolle in der aktuellen Datenbank einen Datenbankbenutzer, eine Datenbankrolle, einen Windows-Anmeldenamen oder eine Windows-Gruppe hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Alter Role](../../t-sql/statements/alter-role-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```
sp_addrolemember [ @rolename = ] 'role', [ @membername = ] 'security_account'  

```    
  
## <a name="arguments"></a>Argumente  
 [ @rolename= ] "*Role*"  
 Der Name der Datenbankrolle in der aktuellen Datenbank. *Role* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @membername= ] "*security_account*"  
 Das Sicherheitskonto, das der Rolle hinzugefügt wird. *security_account* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *security_account* kann ein Datenbankbenutzer, eine Daten Bank Rolle, ein Windows-Anmelde Name oder eine Windows-Gruppe sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Mitglied, das einer Rolle mithilfe von sp_addrolemember hinzugefügt wird, erbt die Berechtigungen der Rolle. Falls das neue Mitglied ein Prinzipal auf Windows-Ebene ohne einen entsprechenden Datenbankbenutzer ist, wird ein Datenbankbenutzer erstellt, jedoch möglicherweise nicht vollständig der Anmeldung zugeordnet. Überprüfen Sie stets, ob die Anmeldung vorhanden ist und Zugriff auf die Datenbank hat.  
  
 Eine Rolle kann sich selbst nicht als Mitglied enthalten. Diese ringförmigen Definitionen sind ungültig, auch wenn die Mitgliedschaft nur indirekt durch eine Zwischenmitgliedschaft impliziert ist.  
  
 sp_addrolemember kann einer Rolle keine festgelegte Daten Bank Rolle, keine festgelegte Server Rolle oder dbo hinzufügen.
  
 Verwenden Sie ausschließlich sp_addrolemember, um einer Datenbankrolle ein Mitglied hinzuzufügen. Verwenden Sie [sp_addsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md), um einer Server Rolle ein Mitglied hinzuzufügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Für das Hinzufügen von Mitgliedern zu flexiblen Datenbankrollen muss eine der folgenden Bedingungen erfüllt sein:  
  
-   Mitgliedschaft in der Daten Bank Rolle "db_securityadmin" oder "db_owner".  
  
-   Mitgliedschaft in der Rolle, die die Rolle besitzt.  
  
-   **ALTER ANY ROLE** -Berechtigung oder **Alter** -Berechtigung für die Rolle.  
  
 Zum Hinzufügen von Mitgliedern zu festen Datenbankrollen ist die Mitgliedschaft in der festen Datenbankrolle db_owner erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-adding-a-windows-login"></a>A. Hinzufügen eines Windows-Anmeldenamens  
 Im folgenden Beispiel wird der Windows- `Contoso\Mary5` Anmelde Name `AdventureWorks2012` der-Datenbank `Mary5`als Benutzer hinzugefügt. Der Benutzer `Mary5` wird dann der `Production`-Rolle hinzugefügt.  
  
> [!NOTE]  
>  Da `Contoso\Mary5` als Datenbankbenutzer `Mary5` in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank bekannt ist, muss der Benutzername `Mary5` angegeben werden. Die Anweisung führt zu einem Fehler, es sei denn, es ist ein Anmeldename `Contoso\Mary5` vorhanden. Testen Sie dies, indem Sie einen Anmeldenamen Ihrer Domäne verwenden.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE USER Mary5 FOR LOGIN [Contoso\Mary5] ;  
GO  
```  
  
### <a name="b-adding-a-database-user"></a>B. Hinzufügen eines Datenbankbenutzers  
 Im folgenden Beispiel wird der Datenbankbenutzer `Mary5` der `Production`-Datenbankrolle in der aktuellen Datenbank hinzugefügt.  
  
```  
EXEC sp_addrolemember 'Production', 'Mary5';  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-adding-a-windows-login"></a>C. Hinzufügen eines Windows-Anmeldenamens  
 Im folgenden Beispiel wird der- `LoginMary` Anmelde Name `AdventureWorks2008R2` der-Datenbank `UserMary`als Benutzer hinzugefügt. Der Benutzer `UserMary` wird dann der `Production`-Rolle hinzugefügt.  
  
> [!NOTE]  
>  Da der Anmelde `LoginMary` Name als Datenbankbenutzer `UserMary` in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Datenbank bezeichnet wird, muss `UserMary` der Benutzername angegeben werden. Die Anweisung führt zu einem Fehler, es sei denn, es ist ein Anmeldename `Mary5` vorhanden. Anmeldungen und Benutzer haben normalerweise denselben Namen. In diesem Beispiel werden verschiedene Namen verwendet, um die Aktionen zu unterscheiden, die sich auf die Anmeldung oder den Benutzer auswirken  
  
```  
-- Uses AdventureWorks  
  
CREATE USER UserMary FOR LOGIN LoginMary ;  
GO  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
### <a name="d-adding-a-database-user"></a>D: Hinzufügen eines Datenbankbenutzers  
 Im folgenden Beispiel wird der Datenbankbenutzer `UserMary` der `Production`-Datenbankrolle in der aktuellen Datenbank hinzugefügt.  
  
```  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  
