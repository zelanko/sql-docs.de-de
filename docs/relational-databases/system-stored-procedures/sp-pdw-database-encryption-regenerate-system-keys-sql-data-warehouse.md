---
title: sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: bb13e323-a984-4462-8b6d-6019c38ddd9d
caps.latest.revision: 8
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8d99d5994e65eb00e8980bf95997571e9759863b
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="sppdwdatabaseencryptionregeneratesystemkeys-sql-data-warehouse"></a>sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Verwendung **Sp_pdw_database_encryption_regenerate_system_keys** drehen Sie das Zertifikat und Datenbank-Verschlüsselungsschlüssel für internen Datenbanken, die verschlüsselt werden, wenn TDE für die Anwendung aktiviert ist. einschließlich `tempdb`, zu verwenden. Dies ist nur erfolgreich, wenn TDE aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption_regenerate_system_keys  ;  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Die Prozedur hat keine Parameter.  
  
 Diese Prozedur sollte verwendet werden, wenn der Datenverkehr in der Einheit gering ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Sysadmin** feste Datenbankrolle oder **CONTROL SERVER** Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird die Datenbank-Verschlüsselungsschlüssel erneut generiert.  
  
```sql  
EXEC sys.sp_pdw_database_encryption_regenerate_system_keys;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_pdw_database_encryption aktiviert werden &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [Sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
