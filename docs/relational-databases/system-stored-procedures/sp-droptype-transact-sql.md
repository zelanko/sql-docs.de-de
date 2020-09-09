---
description: sp_droptype (Transact-SQL)
title: sp_droptype (Transact-SQL) | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d470c4f6f706db73f401511826a6dbcd5903d8d0
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536151"
---
# <a name="sp_droptype-transact-sql"></a>sp_droptype (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht einen Alias Datentyp aus **systypes**.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droptype [ @typename = ] 'type'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @typename = ] 'type'` Der Name eines Alias Datentyps, den Sie besitzen. *Type ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-type"></a>Rückgabe Codetyp  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Der **Typ** -Alias Datentyp kann nicht gelöscht werden, wenn Tabellen oder andere Datenbankobjekte darauf verweisen.  
  
> [!NOTE]  
>  Ein Aliasdatentyp kann nicht gelöscht werden, wenn er in einer Tabellendefinition verwendet wird oder wenn eine Regel oder ein Standard an ihn gebunden ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **db_owner** Fixed-Daten Bank Rolle oder der **db_ddladmin** Fixed-Daten Bank Rolle.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addtype &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
