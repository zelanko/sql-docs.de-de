---
title: sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: bb13e323-a984-4462-8b6d-6019c38ddd9d
author: ronortloff
ms.author: rortloff
ms.reviewer: ''
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 323b7602fd375bc393828663f1d2c749332dc9ac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67463481"
---
# <a name="sp_pdw_database_encryption_regenerate_system_keys-sql-data-warehouse"></a>sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Verwenden Sie **sp_pdw_database_encryption_regenerate_system_keys** , um das Zertifikat und den Verschlüsselungsschlüssel für interne Datenbanken zu drehen, die verschlüsselt werden, wenn TDE auf dem Gerät aktiviert ist. einschließlich `tempdb`, zu verwenden. Dies ist nur erfolgreich, wenn TDE aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption_regenerate_system_keys  ;  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Die Prozedur weist keine Parameter auf.  
  
 Diese Prozedur sollte verwendet werden, wenn der Datenverkehr in der Appliance gering ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Daten Bank Rolle **sysadmin** oder die **Control Server** -Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Verschlüsselungsschlüssel für die Datenbank neu generiert.  
  
```sql  
EXEC sys.sp_pdw_database_encryption_regenerate_system_keys;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_pdw_database_encryption &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
