---
title: Sp_defaultdb (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc9703b4310870105d3a0961c430699449da7ff3
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532982"
---
# <a name="spdefaultdb-transact-sql"></a>sp_defaultdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Standarddatenbank für eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_defaultdb [ @loginame = ] 'login', [ @defdb = ] 'database'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'` Ist der Anmeldename. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. *Anmeldung* kann sein, eine vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung oder einen Windows-Benutzer oder eine Gruppe. Falls für den Windows-Benutzer bzw. die Gruppe kein Anmeldename in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden ist, wird er automatisch hinzugefügt.  
  
`[ @defdb = ] 'database'` Ist der Name der neuen Standarddatenbank. *Datenbank* ist **Sysname**, hat keinen Standardwert. *Datenbank* muss bereits vorhanden sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_defaultdb** ruft ALTER LOGIN. Diese Anweisung unterstützt weitere Optionen. Weitere Informationen zum Ändern der Standarddatenbank, finden Sie unter [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
 **Sp_defaultdb** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel legt [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] als Standarddatenbank für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]login`Victoria` fest.  
  
```  
EXEC sp_defaultdb 'Victoria', 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
