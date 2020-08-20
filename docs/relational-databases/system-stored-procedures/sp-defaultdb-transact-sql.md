---
description: sp_defaultdb (Transact-SQL)
title: sp_defaultdb (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_defaultdb_TSQL
- sp_defaultdb
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultdb
ms.assetid: 663b859f-c6da-4942-95a6-60b93d05654e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 649f107e29f68d03e47daa07251a2da40a4c2e55
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493354"
---
# <a name="sp_defaultdb-transact-sql"></a>sp_defaultdb (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Standarddatenbank für einen- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Namen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [Alter Login](../../t-sql/statements/alter-login-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_defaultdb [ @loginame = ] 'login', [ @defdb = ] 'database'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'` Der Anmelde Name. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. der *Anmelde* Name kann eine vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung oder ein Windows-Benutzer oder eine Windows-Gruppe sein. Falls für den Windows-Benutzer bzw. die Gruppe kein Anmeldename in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden ist, wird er automatisch hinzugefügt.  
  
`[ @defdb = ] 'database'` Der Name der neuen Standarddatenbank. *Database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. die *Datenbank* muss bereits vorhanden sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_defaultdb** ruft Alter Login auf. Diese Anweisung unterstützt weitere Optionen. Weitere Informationen zum Ändern der Standarddatenbank finden Sie unter [Alter Login &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
 **sp_defaultdb** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel legt [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] als Standarddatenbank für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]login`Victoria` fest.  
  
```  
EXEC sp_defaultdb 'Victoria', 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
