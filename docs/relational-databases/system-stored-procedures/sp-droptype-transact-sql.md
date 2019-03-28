---
title: Sp_droptype (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droptype_TSQL
- sp_droptype
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droptype
ms.assetid: e78464ac-2370-4c4e-9cc0-06aebc07cec5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5004bbdefe29ec13142c66d333f346643261aeb2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527902"
---
# <a name="spdroptype-transact-sql"></a>sp_droptype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Löscht einen Aliasdatentyp aus **Systypes**.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droptype [ @typename = ] 'type'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @typename = ] 'type'` Ist der Name eines Alias-Datentyps, die Sie besitzen. *Typ* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-type"></a>Rückgabecode-Typ  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die **Typ** alias-Datentyp kann nicht gelöscht werden, wenn Tabellen oder andere Datenbankobjekte, die darauf verweisen.  
  
> [!NOTE]  
>  Ein Aliasdatentyp kann nicht gelöscht werden, wenn er in einer Tabellendefinition verwendet wird oder wenn eine Regel oder ein Standard an ihn gebunden ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Db_owner** feste Datenbankrolle oder der **Db_ddladmin** festen Datenbankrolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Aliasdatentyp `birthday` gelöscht.  
  
> [!NOTE]  
>  Dieser Aliasdatentyp muss bereits vorhanden sein. Andernfalls wird eine Fehlermeldung zurückgegeben.  
  
```  
USE master;  
GO  
EXEC sp_droptype 'birthday';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addtype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
