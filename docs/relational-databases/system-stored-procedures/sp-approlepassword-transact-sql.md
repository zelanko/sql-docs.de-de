---
description: sp_approlepassword (Transact-SQL)
title: sp_approlepassword (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_approlepassword
- sp_approlepassword_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_approlepassword
ms.assetid: 7967dc0b-bee2-4c63-b8e9-1c3ce2f5db2a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b375dac904decdaa096cfe0e0b1839cc0c3d2d8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464540"
---
# <a name="sp_approlepassword-transact-sql"></a>sp_approlepassword (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert das Kennwort einer Anwendungsrolle in der aktuellen Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [Alter Application Role](../../t-sql/statements/alter-application-role-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_approlepassword [ @rolename= ] 'role' , [ @newpwd = ] 'password'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'` Der Name der Anwendungs Rolle. *Role* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *role* muss in der aktuellen Datenbank vorhanden sein.  
  
`[ @newpwd = ] 'password'` Das neue Kennwort für die Anwendungs Rolle. *Password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Das *Kennwort* darf nicht NULL sein.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein NULL-Kennwort. Verwenden Sie ein sicheres Kennwort. Weitere Informationen finden Sie unter [Strong Passwords](../../relational-databases/security/strong-passwords.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_approlepassword** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY APPLICATION ROLE-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Kennwort für die `PayrollAppRole`-Anwendungsrolle auf `B3r12-36` festgelegt.  
  
```  
EXEC sp_approlepassword 'PayrollAppRole', '''B3r12-36';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Anwendungs Rollen](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_addapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_setapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
