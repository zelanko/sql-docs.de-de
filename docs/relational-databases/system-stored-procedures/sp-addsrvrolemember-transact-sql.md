---
title: sp_addsrvrolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addsrvrolemember
- sp_addsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addsrvrolemember
ms.assetid: 777f0e09-8ee5-4cb2-a3ac-939d02c3cd22
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3077ba01cb982a5f4a3517f5d73b5d9e4436484b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85876441"
---
# <a name="sp_addsrvrolemember-transact-sql"></a>sp_addsrvrolemember (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Fügt einen Benutzernamen als Mitglied einer festen Serverrolle hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Alter Server Role](../../t-sql/statements/alter-server-role-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addsrvrolemember [ @loginame= ] 'login'   
    , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @loginame **=** ] **'**_Login_**'**  
 Der Name der Anmeldung, die der festen Serverrolle hinzugefügt wird. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. *Login* kann ein- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Name oder ein Windows-Anmelde Name sein. Sollte der Windows-Anmeldename noch nicht die Zugriffsrechte für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besitzen, so werden diese automatisch erteilt.  
  
 [ @rolename **=** ] **'**_Rolle_**'**  
 Der Name der festen Serverrolle, der der Anmeldename hinzugefügt wird. *Role* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. die folgenden Werte sind erforderlich:  
  
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
 Wenn ein Anmeldename einer festen Serverrolle hinzugefügt wird, erhält der Anmeldename die Berechtigungen dieser Rolle.  
  
 Die Rollenmitgliedschaft des Anmeldenamens sa und von public kann nicht geändert werden.  
  
 Verwenden Sie sp_addrolemember, um einer festen Datenbankrolle oder einer benutzerdefinierten Rolle ein Mitglied hinzuzufügen.  
  
 sp_addsrvrolemember kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Rolle, der das neue Mitglied hinzugefügt wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Windows-Anmeldename `Corporate\HelenS` der festen Serverrolle `sysadmin` hinzugefügt.  
  
```  
EXEC sp_addsrvrolemember 'Corporate\HelenS', 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sicherheitsfunktionen &#40;Transact-SQL-&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [Erstellen einer Server Rolle &#40;Transact-SQL-&#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-role-transact-sql.md)  
  
  
