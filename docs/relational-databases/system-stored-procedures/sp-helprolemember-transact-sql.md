---
title: sp_helprolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprolemember_TSQL
- sp_helprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprolemember
ms.assetid: 42797510-aa5d-4564-85ac-27418419af9c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 12d66cfa4668c8ca91d82d00cfa5abd4504e76eb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719285"
---
# <a name="sp_helprolemember-transact-sql"></a>sp_helprolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu den direkten Mitgliedern einer Rolle in der aktuellen Datenbank zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helprolemember [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] ' role '`Der Name einer Rolle in der aktuellen Datenbank. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. *role* muss in der aktuellen Datenbank vorhanden sein. Wenn *role* nicht angegeben wird, werden alle Rollen zurückgegeben, die mindestens ein Mitglied aus der aktuellen Datenbank enthalten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**DbRole**|**sysname**|Name der Rolle in der aktuellen Datenbank.|  
|**Membername**|**sysname**|Name eines Mitglieds von **DbRole**.|  
|**MemberSID**|**varbinary(85)**|Sicherheits-ID von **MemberName**.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Datenbank geschachtelte Rollen enthält, ist **MemberName** möglicherweise der Name einer Rolle. **sp_helprolemember** zeigt keine Mitgliedschaft an, die über geschachtelte Rollen erworben wurde. Beispiel: Wenn User1 Mitglied von Role1 und Role1 Mitglied von Role2 ist, gibt `EXEC sp_helprolemember 'Role2'`; Role1, aber nicht die Mitglieder von Role1 (in diesem Beispiel User1) zurück. Um geschachtelte Mitgliedschaften zurückzugeben, müssen Sie **sp_helprolemember** wiederholt für jede geschachtelte Rolle ausführen.  
  
 Mithilfe von **sp_helpsrvrolemember** zeigen Sie die Mitglieder einer festen Serverrolle an.  
  
 Verwenden Sie [IS_ROLEMEMBER &#40;Transact-SQL-&#41;](../../t-sql/functions/is-rolemember-transact-sql.md) , um die Rollen Mitgliedschaft für einen angegebenen Benutzer zu überprüfen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Mitglieder der `Sales` -Rolle angezeigt.  
  
```  
EXEC sp_helprolemember 'Sales';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
