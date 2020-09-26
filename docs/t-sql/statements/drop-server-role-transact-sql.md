---
description: DROP SERVER ROLE (Transact-SQL)
title: DROP SERVER ROLE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SERVER ROLE
- DROP_SERVER_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, DROP
- DROP SERVER ROLE statement
ms.assetid: a2a1e6e6-e40c-4d6a-81be-d197b80bf226
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5a8f5b2204323c0da73371ba1298bc2b0f636e1a
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379662"
---
# <a name="drop-server-role-transact-sql"></a>DROP SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

  Entfernt eine benutzerdefinierte Serverrolle.  
  
 Benutzerdefinierte Serverrollen sind neu in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
DROP SERVER ROLE role_name  
```  
  
## <a name="arguments"></a>Argumente  
 *role_name*  
 Gibt die benutzerdefinierte Serverrolle an, die vom Server gelöscht werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Benutzerdefinierte Serverrollen, die sicherungsfähige Elemente besitze, können nicht vom Server gelöscht werden. Wenn eine benutzerdefinierte Serverrolle mit sicherungsfähigen Elementen gelöscht werden soll, müssen Sie zunächst den Besitz der sicherungsfähigen Elemente übertragen oder sie aus der Datenbank löschen.  
  
 Benutzerdefinierte Serverrollen, die über Elemente verfügen, können nicht gelöscht werden. Um eine benutzerdefinierte Serverrolle mit Mitgliedern zu löschen, müssen Sie zuerst Mitglieder der Rolle mit [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) entfernen.  
  
 Feste Serverrollen können nicht entfernt werden.  
  
 Sie können die [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)-Katalogsicht abfragen, um Informationen zu Rollenmitgliedschaften anzuzeigen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die Serverrolle oder die ALTER ANY SERVER ROLE-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-to-drop-a-server-role"></a>A. Löschen einer Serverrolle  
 Im folgenden Beispiel wird die Serverrolle `purchasing` gelöscht.  
  
```sql  
DROP SERVER ROLE purchasing;  
GO  
```  
  
### <a name="b-to-view-role-membership"></a>B. Anzeigen der Rollenmitgliedschaft  
 Um die Rollenmitgliedschaft anzuzeigen, verwenden Sie die Seite **Serverrolle (Mitglieder)** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], oder führen Sie die folgende Abfrage aus:  
  
```sql  
SELECT SRM.role_principal_id, SP.name AS Role_Name,   
SRM.member_principal_id, SP2.name  AS Member_Name  
FROM sys.server_role_members AS SRM  
JOIN sys.server_principals AS SP  
    ON SRM.Role_principal_id = SP.principal_id  
JOIN sys.server_principals AS SP2   
    ON SRM.member_principal_id = SP2.principal_id  
ORDER BY  SP.name,  SP2.name  
```  
  
### <a name="c-to-view-role-membership"></a>C. Anzeigen der Rollenmitgliedschaft  
 Um zu ermitteln, ob eine Serverrolle eine andere Serverrolle besitzt, führen Sie die folgende Abfrage aus:  
  
```sql  
SELECT SP1.name AS RoleOwner, SP2.name AS Server_Role  
FROM sys.server_principals AS SP1  
JOIN sys.server_principals AS SP2  
    ON SP1.principal_id = SP2.owning_principal_id   
ORDER BY SP1.name ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
