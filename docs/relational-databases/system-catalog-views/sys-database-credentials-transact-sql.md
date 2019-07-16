---
title: database_credentials (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2521d9543c71d9dee298fbb58518163fd45fbfdc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67999527"
---
# <a name="sysdatabasecredentials-transact-sql"></a>database_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Gibt eine Zeile für jede Datenbank von datenbankweit gültigen Anmeldeinformationen in der Datenbank.  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) stattdessen.    
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID der datenbankweit gültigen Anmeldeinformationen. In der Datenbank eindeutig ist.|  
|NAME|**sysname**|Name der Datenbank von datenbankweit gültigen Anmeldeinformationen. In der Datenbank eindeutig ist.|  
|credential_identity|**nvarchar(4000)**|Name der zu verwendenden Identität. In der Regel ist dies ein Windows-Benutzer. Er muss nicht eindeutig sein.|  
|create_date|**datetime**|Zeitpunkt, zu dem die datenbankweit gültige Anmeldeinformationen erstellt wurde.|  
|modify_date|**datetime**|Zeitpunkt, an der datenbankweit gültigen Anmeldeinformationen zuletzt geändert wurde.|  
|target_type|**nvarchar(100)**|Typ der Datenbank von datenbankweit gültigen Anmeldeinformationen. Gibt NULL für die Datenbank beschränkt Anmeldeinformationen.|  
|target_id|**int**|Die ID des Objekts, das die datenbankweit gültigen Anmeldeinformationen zugeordnet ist. Gibt 0 zurück, für die Datenbank beschränkt, Anmeldeinformationen|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `CONTROL`-Berechtigung für die Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Anmeldeinformationen &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
