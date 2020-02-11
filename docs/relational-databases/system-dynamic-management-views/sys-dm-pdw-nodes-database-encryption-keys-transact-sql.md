---
title: sys. dm_pdw_nodes_database_encryption_keys (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e7fd02b2-5d7e-4816-a0af-b58ae2ac3f7a
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c319259d8997db2ff39d90b408056d03eb008782
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401641"
---
# <a name="sysdm_pdw_nodes_database_encryption_keys-transact-sql"></a>sys. dm_pdw_nodes_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Gibt Informationen über den Verschlüsselungsstatus einer Datenbank und die ihr zugeordneten Verschlüsselungsschlüssel für die Datenbank zurück. **sys. dm_pdw_nodes_database_encryption_keys** stellt diese Informationen für jeden Knoten bereit. Weitere Informationen zur Datenbankverschlüsselung finden Sie unter [transparent Data Encryption (SQL Server PDW)](../../analytics-platform-system/transparent-data-encryption.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID der physischen Datenbank auf jedem Knoten.|  
|encryption_state|**int**|Gibt an, ob die Datenbank auf diesem Knoten verschlüsselt oder nicht verschlüsselt ist.<br /><br /> 0 = Kein Verschlüsselungsschlüssel für die Datenbank vorhanden, keine Verschlüsselung<br /><br /> 1 = Unverschlüsselt<br /><br /> 2 = Verschlüsselung wird ausgeführt<br /><br /> 3 = Verschlüsselt.<br /><br /> 4 = Schlüsseländerung wird ausgeführt<br /><br /> 5 = Entschlüsselung wird ausgeführt<br /><br /> 6 = Schutz Änderung wird ausgeführt (das Zertifikat, das den Verschlüsselungsschlüssel für die Datenbank verschlüsselt, wird geändert.)|  
|create_date|**datetime**|Zeigt das Datum der Erstellung des Verschlüsselungsschlüssels an.|  
|regenerate_date|**datetime**|Zeigt das Datum der Neugenerierung des Verschlüsselungsschlüssels an.|  
|modify_date|**datetime**|Zeigt das Datum der Änderung des Verschlüsselungsschlüssels an.|  
|set_date|**datetime**|Zeigt das Datum der Anwendung des Verschlüsselungsschlüssels auf die Datenbank an.|  
|opened_date|**datetime**|Zeigt das Datum an, an dem der Datenbankschlüssel zuletzt geöffnet wurde.|  
|key_algorithm|**varchar (?)**|Zeigt den Algorithmus an, der für den Schlüssel verwendet wird.|  
|key_length|**int**|Zeigt die Länge des Schlüssels an.|  
|encryptor_thumbprint|**varbin**|Zeigt den Fingerabdruck der Verschlüsselung an.|  
|percent_complete|**wirkliche**|Prozentualer Anteil der bereits abgeschlossenen Änderung des Verschlüsselungsstatus einer Datenbank. Dieser Wert ist 0, wenn es keine Statusänderung gibt.|  
|node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird `sys.dm_pdw_nodes_database_encryption_keys` eine Joins mit anderen Systemtabellen durchführt, um den Verschlüsselungs Status für die einzelnen Knoten der durch TDE geschützten Datenbanken anzugeben.  
  
```  
SELECT D.database_id AS DBIDinMaster, D.name AS UserDatabaseName,   
PD.pdw_node_id AS NodeID, DM.physical_name AS PhysDBName,   
keys.encryption_state  
FROM sys.dm_pdw_nodes_database_encryption_keys AS keys  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON keys.database_id = PD.database_id AND keys.pdw_node_id = PD.pdw_node_id  
JOIN sys.pdw_database_mappings AS DM  
    ON DM.physical_name = PD.physical_name  
JOIN sys.databases AS D  
    ON D.database_id = DM.database_id  
ORDER BY D.database_id, PD.pdw_node_ID;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [Erstellen eines Daten Bank Verschlüsselungsschlüssels &#40;Transact-SQL-&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [Alter Database-Verschlüsselungsschlüssel &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [Drop Database Encryption Key &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  

