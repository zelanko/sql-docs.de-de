---
description: ALTER ROLE (Transact-SQL)
title: ALTER ROLE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_ROLE_TSQL
- ALTER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database roles
- ALTER ROLE statement
- renaming database roles
- database roles [SQL Server], modifying
- names [SQL Server], database roles
ms.assetid: e1e83caa-17cc-4871-b2db-2711339fb64f
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4bf7faa22088fd00c646a5760923e7e6a64a9eac
ms.sourcegitcommit: 3efd8bbf91f4f78dce3a4ac03348037d8c720e6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91024448"
---
# <a name="alter-role-transact-sql"></a>ALTER ROLE (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Fügt Mitglieder zu einer Datenbankrolle hinzu, entfernt Mitglieder einer Datenbankrolle oder ändert den Namen einer benutzerdefinierten Datenbankrolle.  
  
> [!NOTE]  
>  Wenn Sie Rollen durch Hinzufügen oder Löschen von Mitgliedern in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ändern möchten, können Sie [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) und [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) verwenden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
-- Syntax for SQL Server (starting with 2012) and Azure SQL Database  
  
ALTER ROLE  role_name  
{  
       ADD MEMBER database_principal  
    |  DROP MEMBER database_principal  
    |  WITH NAME = new_name  
}  
[;]  
```  
  
 
```syntaxsql
-- Syntax for SQL Server 2008, Azure Synapse Analytics and Parallel Data Warehouse
  
-- Change the name of a user-defined database role  
ALTER ROLE role_name   
    WITH NAME = new_name  
[;]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *role_name*  
 **Gilt für:**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab 2008), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Gibt die Datenbankrolle an, die geändert werden soll.  
  
 ADD MEMBER *database_principal*  
 **Gilt für:**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab 2012), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Legt fest, dass der Datenbankprinzipal einer Datenbankrolle als Mitglied hinzugefügt werden soll.  
  
-   *database_principal* ist ein Datenbankbenutzer oder eine benutzerdefinierte Datenbankrolle.  
  
-   *database_principal* darf keine feste Datenbankrolle oder ein Serverprinzipal sein.  
  
DROP MEMBER *database_principal*  
 **Gilt für:**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab 2012), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Legt fest, dass für den Datenbankprinzipal die Mitgliedschaft einer Datenbankrolle gelöscht werden soll.  
  
-   *database_principal* ist ein Datenbankbenutzer oder eine benutzerdefinierte Datenbankrolle.  
  
-   *database_principal* darf keine feste Datenbankrolle oder ein Serverprinzipal sein.  
  
WITH NAME = *new_name*  
 **Gilt für:**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab 2008), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Legt fest, dass der Name einer benutzerdefinierten Datenbankrolle geändert werden soll. Der neue Name darf nicht bereits in der Datenbank vorhanden sein.  
  
 Durch das Ändern des Namens einer Datenbankrolle werden die ID-Nummer, der Besitzer oder Berechtigungen der Rolle nicht geändert.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieses Befehls benötigen Sie mindestens eine der folgenden Berechtigungen oder Gruppenmitgliedschaften:  
  
-   die **ALTER**-Berechtigung für die Rolle  
-   die **ALTER ANY ROLE**-Berechtigung für die Datenbank  
-   die Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**  
  
Zum Ändern der Mitgliedschaft einer festen Datenbankrolle benötigen Sie darüber hinaus:  
  
-   die Mitgliedschaft in der festen Datenbankrolle **db_owner**  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
 Sie können den Namen einer festen Datenbankrolle nicht ändern.  
  
## <a name="metadata"></a>Metadaten  
 Die folgenden Systemsichten enthalten Informationen zu Datenbankrollen und Datenbankprinzipalen:  
  
-   [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
-   [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-change-the-name-of-a-database-role"></a>A. Ändern eines Datenbankrollennamens  
 **Gilt für:**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab 2008), [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 Im folgenden Beispiel wird der Name der `buyers`-Rolle in `purchasing` geändert.   Dieses Beispiel kann in der [AdventureWorks](https://msftdbprodsamples.codeplex.com/)-Musterdatenbank ausgeführt werden.
  
```sql  
ALTER ROLE buyers WITH NAME = purchasing;  
```  
  
### <a name="b-add-or-remove-role-members"></a>B. Hinzufügen oder Entfernen von Rollenmitgliedern  
 **Gilt für:**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab 2012), [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 In folgendem Beispiel wird eine neue Datenbankrolle mit dem Namen `Sales` erstellt. Dieser wird der Datenbankbenutzer Barry als Mitglied hinzugefügt. Anschließend wird dieses Mitglied wieder entfernt.   Dieses Beispiel kann in der [AdventureWorks](https://msftdbprodsamples.codeplex.com/)-Musterdatenbank ausgeführt werden.
  
```sql  
CREATE ROLE Sales;  
ALTER ROLE Sales ADD MEMBER Barry;  
ALTER ROLE Sales DROP MEMBER Barry;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
