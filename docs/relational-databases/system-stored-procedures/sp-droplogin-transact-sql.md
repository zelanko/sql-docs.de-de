---
title: Sp_droplogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_droplogin
- sp_droplogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplogin
ms.assetid: e58684d1-c394-48de-906e-da6ee91100c3
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 644c15b1c0ebd400cffef2578596d633066a40e9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245350"
---
# <a name="spdroplogin-transact-sql"></a>sp_droplogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen. Dadurch wird der Zugriff auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter diesem Anmeldenamen verhindert.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droplogin [ @loginame = ] 'login'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@loginame =** ] **'***login***'**  
 Der Anmeldename, der entfernt werden soll. *login* ist vom Datentyp **sysname**und hat keinen Standardwert. *Anmeldung* muss bereits vorhanden sein, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_droplogin** ruft DROP LOGIN auf.  
  
 **sp_droplogin** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mithilfe von `DROP LOGIN` der Anmeldename `Victoria` aus einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt. Dies ist die bevorzugte Methode.  
  
```  
DROP LOGIN Victoria;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN & #40; Transact-SQL & #41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
