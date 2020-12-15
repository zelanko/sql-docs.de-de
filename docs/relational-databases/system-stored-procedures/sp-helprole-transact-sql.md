---
description: sp_helprole (Transact-SQL)
title: sp_helprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprole_TSQL
- sp_helprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprole
ms.assetid: b023103f-ccf3-44e2-b418-4be9bdd49f4a
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9832373d4b6c65ba16bfa83b8ef54cba963777c0
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97462711"
---
# <a name="sp_helprole-transact-sql"></a>sp_helprole (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt Informationen zu den Rollen in der aktuellen Datenbank zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helprole [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'` Der Name einer Rolle in der aktuellen Datenbank. *role* ist vom Datentyp **sysname** und hat den Standardwert NULL. *role* muss in der aktuellen Datenbank vorhanden sein. Falls *role* nicht angegeben wird, werden Informationen zu allen Rollen in der aktuellen Datenbank zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**RoleName**|**sysname**|Name der Rolle in der aktuellen Datenbank.|  
|**RoleId**|**smallint**|ID von **RoleName**.|  
|**Isapprole**|**int**|0 = **RoleName** ist keine Anwendungsrolle.<br /><br /> 1 = **RoleName** ist eine Anwendungsrolle.|  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe von **sp_helprotect** zeigen Sie die Berechtigungen an, die einer Rolle zugeordnet sind. Mithilfe von **sp_helprolemember** zeigen Sie die Mitglieder einer Datenbankrolle an.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage gibt alle Rollen in der aktuellen Datenbank zurück.  
  
```  
EXEC sp_helprole  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [sp_addapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [sp_droprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
