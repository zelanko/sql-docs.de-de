---
title: sp_grantlogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grantlogin_TSQL
- sp_grantlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantlogin
ms.assetid: 0c873d99-c3bf-4eb1-948b-a46cb235ccd4
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: a32826266a9e844b01b455116e18ae821f71e9c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055307"
---
# <a name="sp_grantlogin-transact-sql"></a>sp_grantlogin (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Create Login](../../t-sql/statements/create-login-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_grantlogin [@loginame=] 'login'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'`Der Name eines Windows-Benutzers oder einer Windows-Gruppe. Der Windows-Benutzer oder die Windows-Gruppe muss mit einem Windows-Domänen Namen in der Form " *Domäne*\\*Benutzer*" qualifiziert werden. z. b. **London\JoeB**. *Login* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_grantlogin** ruft Create Login auf, wodurch zusätzliche Optionen unterstützt werden. Weitere Informationen zum Erstellen von SQL Server Anmeldungen finden Sie unter [Create Login &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)  
  
 **sp_grantlogin** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `CREATE LOGIN` zum Erstellen eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamens für den Windows-Benutzer `Corporate\BobJ.` verwendet. Dies ist die bevorzugte Methode.  
  
```sql
CREATE LOGIN [Corporate\BobJ] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Erstellen der Anmeldung &#40;Transact-SQL-&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
