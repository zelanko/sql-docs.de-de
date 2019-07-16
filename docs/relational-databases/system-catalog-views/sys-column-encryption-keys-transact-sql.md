---
title: Sys. column_encryption_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_encryption_keys
- column_encryption_keys_TSQL
- sys.column_encryption_keys_TSQL
- column_encryption_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_keys catalog view
ms.assetid: 43980dd8-b9b1-4869-a304-2c183ae8977d
author: VanMSFT
ms.author: vanto
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8fd9177ad646a8086e00f9494e7e73488aace53d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140100"
---
# <a name="syscolumnencryptionkeys--transact-sql"></a>Sys. column_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-xxx-md.md)]

  Gibt Informationen zur Verschlüsselung von spaltenverschlüsselungsschlüsseln (CEKs) erstellt, mit der [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) Anweisung. Jede Zeile stellt einen CEK.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des CMK.|  
|**column_encryption_key_id**|**int**|Die ID des CEK.|  
|**create_date**|**datetime**|Datum, an der CEK erstellt wurde.|  
|**modify_date**|**datetime**|Datum, an der letzten der CEK Änderung.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW ANY COLUMN ENCRYPTION KEY** Berechtigung.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted &#40;Datenbank-Engine&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
