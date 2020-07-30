---
title: sys. database_credentials (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_credentials
- sys.database_credentials_TSQL
- database_credentials
- database_credentials_TSQL
helpviewer_keywords:
- sys.database_credentials catalog view
ms.assetid: 796322df-e62a-45bf-b519-89e1d521abce
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b78875b7c6f3440bd747045d1b90d0f8ef323c4
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394885"
---
# <a name="sysdatabase_credentials-transact-sql"></a>sys. database_credentials (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Gibt eine Zeile für jede Daten Bank weite Anmelde Information in der Datenbank zurück.  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [sys. database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) .    
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID der Daten Bank weit gültigen Anmelde Informationen. Ist in der Datenbank eindeutig.|  
|name|**sysname**|Name der Daten Bank weit gültigen Anmelde Informationen. Ist in der Datenbank eindeutig.|  
|credential_identity|**nvarchar(4000)**|Name der zu verwendenden Identität. In der Regel ist dies ein Windows-Benutzer. Er muss nicht eindeutig sein.|  
|create_date|**datetime**|Zeitpunkt, zu dem die Daten Bank weit gültigen Anmelde Informationen erstellt wurden.|  
|modify_date|**datetime**|Zeitpunkt, zu dem die Daten Bank weit gültigen Anmelde Informationen zuletzt geändert wurden.|  
|target_type|**nvarchar (100)**|Typ der Daten Bank weit gültigen Anmelde Informationen. Gibt NULL für Daten Bank weit gültige Anmelde Informationen zurück.|  
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
  
  
