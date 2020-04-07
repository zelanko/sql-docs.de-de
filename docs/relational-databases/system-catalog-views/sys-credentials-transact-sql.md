---
title: sys.credentials (Transact-SQL) | Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f87378897256f8b4fae26b30263577bedede6175
ms.sourcegitcommit: c6a2efe551e37883c1749bdd9e3c06eb54ccedc9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752890"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-asdw-pdw-md.md)]

  Gibt eine Zeile für jede Anmeldeinformation auf Serverebene zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID der Anmeldeinformationen. Ist im Server eindeutig.|  
|name|**Sysname**|Name der Anmeldeinformationen. Ist im Server eindeutig.|  
|credential_identity|**nvarchar(4000)**|Name der zu verwendenden Identität. In der Regel ist dies ein Windows-Benutzer. Er muss nicht eindeutig sein.|  
|create_date|**datetime**|Der Zeitpunkt, zu dem die Anmeldeinformationen erstellt wurden.|  
|modify_date|**datetime**|Der Zeitpunkt, zu dem die Anmeldeinformationen zuletzt geändert wurden.|  
|target_type|**nvarchar(100)**|Anmeldeinformationstyp. Gibt NULL für herkömmliche Anmeldeinformationen und CRYPTOGRAPHIC PROVIDER für einem Kryptografieanbieter zugeordnete Anmeldeinformationen zurück. Weitere Informationen zu externen Schlüsselverwaltungsanbietern finden Sie unter [Erweiterbares Schlüsselmanagement &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**int**|ID des Objekts, dem die Anmeldeinformationen zugeordnet werden. Gibt 0 für herkömmliche Anmeldeinformationen und einen Wert ungleich 0 für einem Kryptografieanbieter zugeordnete Anmeldeinformationen zurück. Weitere Informationen zu externen Schlüsselverwaltungsanbietern finden Sie unter [Erweiterbares Schlüsselmanagement &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>Bemerkungen  
Anmeldeinformationen auf Datenbankebene finden Sie unter [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert `VIEW ANY DEFINITION` entweder `ALTER ANY CREDENTIAL` eine Berechtigung oder eine Berechtigung. Darüber hinaus darf dem Prinzipal die Berechtigung nicht verweigert `VIEW ANY DEFINITION` werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Anmeldeinformationen &#40;Datenbankmodul&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Sicherheitskatalogansichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Principals &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
