---
title: sp_dropsrvrolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropsrvrolemember
- sp_dropsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropsrvrolemember
ms.assetid: 7be99181-d221-49d0-9cb2-c930d8c044a0
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 213b8301a471e00107ce7d3ac6bf493e6aea87c4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85662466"
---
# <a name="sp_dropsrvrolemember-transact-sql"></a>sp_dropsrvrolemember (Transact-SQL)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Entfernt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen oder einen Windows-Benutzer bzw. eine -Gruppe aus einer festen Serverrolle.

> [!IMPORTANT]
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Alter Server Role](../../t-sql/statements/alter-server-role-transact-sql.md) .

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntax

```
sp_dropsrvrolemember [ @loginame = ] 'login' , [ @rolename = ] 'role'  
```

## <a name="arguments"></a>Argumente

**[ @loginame =]** '_Login_'  
Der Name einer Anmeldung, die aus der festen Serverrolle entfernt werden soll. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. der *Anmelde* Name muss vorhanden sein.  

**[ @rolename =]** '_Rolle_'  
Der Name einer Serverrolle. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. die *Rolle* muss einen der folgenden Werte aufweisen:  

-   Serverrollen  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin 
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Nur mithilfe von sp_dropsrvrolemember können Anmeldenamen aus einer festen Serverrolle entfernt werden. Verwenden Sie sp_droprolemember, um ein Mitglied aus einer Datenbankrolle zu entfernen.  
  
 Es ist nicht möglich, den Anmeldenamen sa aus einer festen Serverrolle zu entfernen.  
  
 sp_dropsrvrolemember kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin oder sowohl die ALTER ANY LOGIN-Berechtigung auf dem Server als auch die Mitgliedschaft in der Rolle, aus der das Mitglied gelöscht wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Anmeldename `JackO` aus der festen Serverrolle `sysadmin` entfernt.  
  
```sql
EXEC sp_dropsrvrolemember 'JackO', 'sysadmin';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Server Rolle &#40;Transact-SQL-&#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
 [Löschen der Server Rolle &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
