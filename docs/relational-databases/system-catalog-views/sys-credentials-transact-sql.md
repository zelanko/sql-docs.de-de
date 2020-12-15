---
description: sys.credentials (Transact-SQL)
title: sys. Anmelde Informationen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs:
- TSQL
helpviewer_keywords:
- sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3dfd50d16275a65c7e923a60c3c478b450e3e812
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473001"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-asdw-pdw-md.md)]

  Gibt eine Zeile für jede Anmelde Information auf Serverebene zurück.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID der Anmeldeinformationen. Ist im Server eindeutig.|  
|name|**sysname**|Name der Anmeldeinformationen. Ist im Server eindeutig.|  
|credential_identity|**nvarchar(4000)**|Name der zu verwendenden Identität. In der Regel ist dies ein Windows-Benutzer. Er muss nicht eindeutig sein.|  
|create_date|**datetime**|Der Zeitpunkt, zu dem die Anmeldeinformationen erstellt wurden.|  
|modify_date|**datetime**|Der Zeitpunkt, zu dem die Anmeldeinformationen zuletzt geändert wurden.|  
|target_type|**nvarchar (100)**|Anmeldeinformationstyp. Gibt NULL für herkömmliche Anmeldeinformationen und CRYPTOGRAPHIC PROVIDER für einem Kryptografieanbieter zugeordnete Anmeldeinformationen zurück. Weitere Informationen zu Anbietern externer Schlüsselverwaltung finden Sie unter [erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**int**|ID des Objekts, dem die Anmeldeinformationen zugeordnet werden. Gibt 0 für herkömmliche Anmeldeinformationen und einen Wert ungleich 0 für einem Kryptografieanbieter zugeordnete Anmeldeinformationen zurück. Weitere Informationen zu Anbietern externer Schlüsselverwaltung finden Sie unter [erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>Hinweise  
Informationen zu Anmelde Informationen auf Datenbankebene finden Sie unter [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert entweder die- `VIEW ANY DEFINITION` Berechtigung oder die- `ALTER ANY CREDENTIAL` Berechtigung. Außerdem darf dem Prinzipal die Berechtigung nicht verweigert werden `VIEW ANY DEFINITION` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Anmeldeinformationen &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
