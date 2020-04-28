---
title: sys. database_role_members (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_role_members_TSQL
- sys.database_role_members
- database_role_members_TSQL
- database_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_role_members catalog view
ms.assetid: ed1b019d-ca48-4db3-85df-cf6d2db591cf
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1bbbcf04cdb141cff25565360d82714eed1e98f1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68079467"
---
# <a name="sysdatabase_role_members-transact-sql"></a>sys.database_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jedes Mitglied jeder Datenbankrolle zurück.  Datenbankbenutzer, Anwendungs Rollen und andere Daten bankrollen können Mitglieder einer Daten Bank Rolle sein. Um Mitglieder zu einer Rolle hinzuzufügen, verwenden Sie die [Alter Role](../../t-sql/statements/alter-role-transact-sql.md) - `ADD MEMBER` Anweisung mit der-Option. Fügen Sie mit [sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) ein, um die Namen `principal_id` der Werte zurückzugeben.
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|Die Daten Bank Prinzipal-ID der Rolle.|  
|**member_principal_id**|**int**|Die Daten Bank Prinzipal-ID des Mitglieds.|  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann die eigenen Rollenmitgliedschaften anzeigen. Zum Anzeigen anderer Rollen Mitgliedschaften ist die Mitgliedschaft in `db_securityadmin` der Fixed-Daten `VIEW DEFINITION` Bank Rolle oder in der-Datenbank erforderlich.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="example"></a>Beispiel  
 Mit der folgenden Abfrage werden die Mitglieder der Daten bankrollen zurückgegeben.  
  
```  
SELECT DP1.name AS DatabaseRoleName,   
   isnull (DP2.name, 'No members') AS DatabaseUserName   
 FROM sys.database_role_members AS DRM  
 RIGHT OUTER JOIN sys.database_principals AS DP1  
   ON DRM.role_principal_id = DP1.principal_id  
 LEFT OUTER JOIN sys.database_principals AS DP2  
   ON DRM.member_principal_id = DP2.principal_id  
WHERE DP1.type = 'R'
ORDER BY DP1.name;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
[Alter Role (Transact-sqll)](../../t-sql/statements/alter-role-transact-sql.md)      
[sys.server_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
  


