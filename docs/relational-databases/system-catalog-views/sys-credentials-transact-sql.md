---
title: Sys.Credentials (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1931d0cb4a11f0fd1a7ddfb1a83a2bcebb0b94d9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43070193"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Gibt eine Zeile für die einzelnen Anmeldeinformationen auf Serverebene.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID der Anmeldeinformationen. Ist im Server eindeutig.|  
|NAME|**sysname**|Name der Anmeldeinformationen. Ist im Server eindeutig.|  
|credential_identity|**nvarchar(4000)**|Name der zu verwendenden Identität. In der Regel ist dies ein Windows-Benutzer. Er muss nicht eindeutig sein.|  
|create_date|**datetime**|Der Zeitpunkt, zu dem die Anmeldeinformationen erstellt wurden.|  
|modify_date|**datetime**|Der Zeitpunkt, zu dem die Anmeldeinformationen zuletzt geändert wurden.|  
|target_type|**nvarchar(100)**|Anmeldeinformationstyp. Gibt NULL für herkömmliche Anmeldeinformationen und CRYPTOGRAPHIC PROVIDER für einem Kryptografieanbieter zugeordnete Anmeldeinformationen zurück. Weitere Informationen zu Anbietern von Verwaltung externer Schlüssel finden Sie unter [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**int**|ID des Objekts, dem die Anmeldeinformationen zugeordnet werden. Gibt 0 für herkömmliche Anmeldeinformationen und einen Wert ungleich 0 für einem Kryptografieanbieter zugeordnete Anmeldeinformationen zurück. Weitere Informationen zu Anbietern von Verwaltung externer Schlüssel finden Sie unter [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>Hinweise  
Anmeldeinformationen auf Datenbankebene finden Sie unter [database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert entweder `VIEW ANY DEFINITION` Berechtigung oder `ALTER ANY CREDENTIAL` Berechtigung. Darüber hinaus der Prinzipal nicht verweigert werden muss `VIEW ANY DEFINITION` Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Anmeldeinformationen &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Prinzipale &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
