---
title: xp_revokelogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_revokelogin
- xp_revokelogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_revokelogin
ms.assetid: b3fa7678-dba4-4537-be94-5ae63ca11f81
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b09c799e553990715a8dd4f30bcd4adc9ce9dda1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890719"
---
# <a name="xp_revokelogin-transact-sql"></a>xp_revokelogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Hebt den Zugriff einer Windows-Gruppe oder eines Windows-Benutzers auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Drop Login](../../t-sql/statements/drop-login-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_revokelogin {[@loginame=] 'login'}  
```  
  
## <a name="arguments"></a>Argumente  
`[ @loginame = ] 'login'`Der Name des Windows-Benutzers oder der Windows-Gruppe, aus dem der Zugriff widerrufen werden soll. *login* muss den Domänennamen beinhalten, z. B. **[ADVWKS\sylvester1]**. *login* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie stattdessen DROP LOGIN.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_denylogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
