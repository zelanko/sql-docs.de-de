---
title: sys. database_scoped_credentials (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 03687ea50b04c96aa4dbafab9d02d2bbc33a14b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079421"
---
# <a name="sysdatabase_scoped_credentials-transact-sql"></a>sys. database_scoped_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Gibt eine Zeile für jede Daten Bank weite Anmelde Information in der Datenbank zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Name der Daten Bank weit gültigen Anmelde Informationen. Ist in der Datenbank eindeutig.|  
|credential_id|**int**|ID der Daten Bank weit gültigen Anmelde Informationen. Ist in der Datenbank eindeutig.|  
|principal_id|**int**|ID des Datenbankprinzipals, der der Besitzer des Schlüssels ist.|  
|credential_identity|**nvarchar(4000)**|Name der zu verwendenden Identität. In der Regel ist dies ein Windows-Benutzer. Er muss nicht eindeutig sein.|  
|create_date|**datetime**|Zeitpunkt, zu dem die Daten Bank weit gültigen Anmelde Informationen erstellt wurden.|  
|modify_date|**datetime**|Zeitpunkt, zu dem die Daten Bank weit gültigen Anmelde Informationen zuletzt geändert wurden.|  
|target_type|**nvarchar (100)**|Typ der Daten Bank weit gültigen Anmelde Informationen. Gibt `NULL` für Daten Bank weit gültige Anmelde Informationen zurück.|  
|target_id|**int**|ID des Objekts, dem die Daten Bank weit gültigen Anmelde Informationen zugeordnet sind. Gibt 0 für Daten Bank weit gültige Anmelde Informationen zurück.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `CONTROL`-Berechtigung für die Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anmelde Informationen &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Create Database scoped Credential &#40;Transact-SQL-&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [Alter Database scoped Credential &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [Drop Database scoped Credential &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
