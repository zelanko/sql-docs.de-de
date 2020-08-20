---
description: sp_delete_operator (Transact-SQL)
title: sp_delete_operator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_operator
- sp_delete_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_operator
ms.assetid: ff6c2c4b-e9fe-4d0c-bbc2-a2ddcc1acb95
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 22fcae3edb3d882826e80bdb7a359726eac930fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474323"
---
# <a name="sp_delete_operator-transact-sql"></a>sp_delete_operator (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt einen Operator.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_operator [ @name = ] 'name'   
     [ , [ @reassign_to_operator = ] 'reassign_operator' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Der Name des zu löschenden Operators. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @reassign_to_operator = ] 'reassign_operator'` Der Name eines Operators, dem die Warnungen des angegebenen Operators neu zugewiesen werden können. *reassign_operator* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Beim Entfernen eines Operators werden alle dem Operator zugeordneten Benachrichtigungen ebenfalls entfernt.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der festen Server Rolle **sysadmin** können **sp_delete_operator**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel löscht den Operator `François Ajenstat`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_operator @name = 'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
