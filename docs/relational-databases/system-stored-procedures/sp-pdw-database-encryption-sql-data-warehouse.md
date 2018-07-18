---
title: sp_pdw_database_encryption aktiviert werden (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-objects
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6508d150df663a6e95437d0b6b3bfd0c8f65906f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052228"
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption aktiviert werden (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Verwendung **sp_pdw_database_encryption aktiviert werden** So aktivieren Sie die transparente datenverschlüsselung auf für eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Appliance. Wenn **sp_pdw_database_encryption aktiviert werden** auf 1 festgelegt, verwendet der **ALTER DATABASE** Anweisung, um eine Datenbank mit TDE zu verschlüsseln.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Parameter  
 [ **@enabled=** ] *enabled*  
 Bestimmt, ob die transparente datenverschlüsselung aktiviert ist. *aktiviert* ist **Int**, und kann einen der folgenden Werte:  
  
-   0 = Deaktiviert  
  
-   1 = Aktiviert  
  
 Ausführen von **sp_pdw_database_encryption aktiviert werden** ohne Parameter gibt den aktuellen Status von TDE auf dem Gerät als skalare Resultset zurück: 0 für deaktiviert oder 1 für aktiviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn der TDE aktiviert ist, mithilfe von **sp_pdw_database_encryption aktiviert werden**, die Tempdb-Datenbank gelöscht, neu erstellt und verschlüsselt. Aus diesem Grund kann der für TDE auf einer Appliance aktiviert werden, während andere aktive Sitzungen, die mithilfe von ' tempdb ' vorhanden sind. Aktivieren oder Deaktivieren von TDE auf einer Appliance ist eine Aktion, die den Zustand der Anwendung, in den meisten Fällen ändert einmal in der Lebensdauer der Anwendung ausgeführt werden soll, und sollte ausgeführt werden, wenn kein Datenverkehr, auf dem Gerät vorliegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Sysadmin** feste Datenbankrolle oder **CONTROL SERVER** Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird TDE auf dem Gerät.  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [Sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
