---
title: Sp_grantdbaccess (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grantdbaccess
- sp_grantdbaccess_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantdbaccess
ms.assetid: 3eb09513-03f1-42f8-9917-3a1f3a579bec
ms.author: vanto
manager: craigg
ms.openlocfilehash: b35e2baef80dbacf039b9c767f7798ddba0d90a9
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591554"
---
# <a name="spgrantdbaccess-transact-sql"></a>sp_grantdbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt der aktuellen Datenbank einen Datenbankbenutzer hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) .  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_grantdbaccess [ @loginame = ] 'login'  
    [ , [ @name_in_db = ] 'name_in_db' [ OUTPUT ] ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@loginame =** ] **"**_Anmeldung_ **"**  
 Der Name der Windows-Gruppe, Windows-Anmeldung oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung, die dem neuen Datenbankbenutzer zugeordnet ist. Namen von Windows-Gruppen und Windows-Anmeldungen müssen mit einem Windows-Domänennamen im Format *Domain*\\*login*gekennzeichnet werden, wie z. B. **LONDON\Joeb**. Der Anmeldename darf noch keinem Benutzer in der Datenbank zugewiesen sein. *login* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [  **@name_in_db=**] **"**_Name_in_db_**"** [ **Ausgabe**]  
 Der Name für den neuen Datenbankbenutzer. *name_in_db* ist eine OUTPUT-Variable vom Datentyp **sysname**. Der Standardwert ist NULL. Wenn dieses Argument nicht angegeben ist, wird *login* verwendet. Bei Angabe als OUTPUT-Variable mit dem Wert NULL, **@name_in_db** nastaven NA hodnotu *Anmeldung*. *name_in_db* darf in der aktuellen Datenbank noch nicht vorhanden sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_grantdbaccess** ruft CREATE USER auf, wodurch zusätzliche Optionen unterstützt werden. Informationen zum Erstellen von Datenbankbenutzern finden Sie unter [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md). Wenn Sie einen Datenbankbenutzer aus einer Datenbank entfernen möchten, verwenden Sie hierzu [DROP USER](../../t-sql/statements/drop-user-transact-sql.md).  
  
 **sp_grantdbaccess** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Setzt die Mitgliedschaft in der festen Datenbankrolle **db_owner** oder in der festen Datenbankrolle **db_accessadmin** voraus.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der aktuellen Datenbank mithilfe von `CREATE USER` ein Datenbankbenutzer für den Windows-Anmeldenamen `Edmonds\LolanSo` hinzugefügt. Der neue Benutzer erhält den Namen `Lolan`. Dies ist die bevorzugte Methode zum Erstellen eines Datenbankbenutzers.  
  
```  
CREATE USER Lolan FOR LOGIN [Edmonds\LolanSo];  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
