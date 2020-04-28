---
title: sp_pdw_database_encryption (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 47d7aca62ddbf2637b54d77171a08817b842555c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008912"
---
# <a name="sp_pdw_database_encryption-sql-data-warehouse"></a>sp_pdw_database_encryption (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Verwenden Sie **sp_pdw_database_encryption** , um die transparente Datenverschlüsselung für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ein Gerät zu aktivieren. Wenn **sp_pdw_database_encryption** auf 1 festgelegt ist, verwenden Sie die **ALTER DATABASE** -Anweisung, um eine Datenbank mithilfe von TDE zu verschlüsseln.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Parameter  
`[ @enabled = ] enabled`Bestimmt, ob die transparente Datenverschlüsselung aktiviert ist. *aktiviert* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen:  
  
-   0 = Deaktiviert  
  
-   1 = Aktiviert  
  
 Wenn Sie **sp_pdw_database_encryption** ohne Parameter ausführen, wird der aktuelle Status von TDE auf dem Gerät als skalares Resultset zurückgegeben: 0 für deaktiviert oder 1 für aktiviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn TDE mit **sp_pdw_database_encryption**aktiviert ist, wird die tempdb-Datenbank gelöscht, neu erstellt und verschlüsselt. Aus diesem Grund kann der TDE nicht auf einem Gerät aktiviert werden, während andere aktive Sitzungen mit tempdb verwendet werden. Das Aktivieren oder Deaktivieren von TDE auf einer Appliance ist eine Aktion, die den Zustand des Geräts ändert. in den meisten Fällen wird davon ausgegangen, dass die Appliance in den meisten Fällen einmal ausgeführt wird, und sollte ausgeführt werden, wenn kein Datenverkehr auf dem Gerät vorhanden ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Daten Bank Rolle **sysadmin** oder die **Control Server** -Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird TDE auf dem Gerät aktiviert.  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
