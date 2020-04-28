---
title: sys. dm_user_db_resource_governance (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/17/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governance
- sys.resource_governance_TSQL
- resource_governance
- resource_governance_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governance catalog view
ms.assetid: ''
author: joesackmsft
ms.author: josack
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: aa7c7e7a7c510f797377c3cbbceb7c2751418da3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74165920"
---
# <a name="sysdm_user_db_resource_governance-transact-sql"></a>sys. dm_user_db_resource_governance (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Gibt die tatsächlichen Konfigurations- und Kapazitätseinstellungen zurück, die von Ressourcenkontrollmechanismen in der aktuellen Datenbank oder im Pool für elastische Datenbanken verwendet werden.
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**database_id**|INT|Die ID der Datenbank, die innerhalb eines Azure SQL-Datenbankservers eindeutig ist.|
|**logical_database_guid**|UNIQUEIDENTIFIER|Logische GUID für die Benutzerdatenbank, die während der Lebensdauer einer Benutzerdatenbank verbleibt.  Durch das Umbenennen der Datenbank oder das Ändern des servicelevelziels wird dieser Wert nicht geändert.|
|**physical_database_guid**|UNIQUEIDENTIFIER|Physische GUID für eine Benutzerdatenbank, die während der Lebensdauer der physischen Instanz der Benutzerdatenbank verbleibt. Wenn Sie das servicelevelziel der Datenbank ändern, wird dieser Wert geändert.|
|**server_name**|NVARCHAR|Der Name des logischen Servers.|
|**database_name**|NVARCHAR|Der Name der logischen Datenbank.|
|**slo_name**|NVARCHAR|Servicelevelziel, einschließlich Hardware Generierung.|
|**dtu_limit**|INT|DTU-Grenzwert der Datenbank (null für VCore).|
|**cpu_limit**|INT|Vcore-Limit von Database (null für DTU-Datenbanken).|
|**min_cpu**|TINYINT|Der MIN_CPU_PERCENT Wert des Ressourcenpools für die Benutzer Auslastung. Siehe [Ressourcen Pool Konzepte](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor-resource-pool?#resource-pool-concepts).|
|**max_cpu**|TINYINT|Der MAX_CPU_PERCENT Wert des Ressourcenpools für die Benutzer Auslastung. Siehe [Ressourcen Pool Konzepte](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor-resource-pool?#resource-pool-concepts).|
|**cap_cpu**|TINYINT|Der CAP_CPU_PERCENT Wert des Ressourcenpools für die Benutzer Auslastung. Siehe [Ressourcen Pool Konzepte](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor-resource-pool?#resource-pool-concepts).|
|**min_cores**|SMALLINT|Nur interne Verwendung.|
|**max_dop**|SMALLINT|Der MAX_DOP Wert für die Benutzer Arbeits Auslastungs Gruppe. Siehe [Erstellen einer Arbeits](https://docs.microsoft.com/sql/t-sql/statements/create-workload-group-transact-sql)Auslastungs Gruppe|
|**min_memory**|INT|Der MIN_MEMORY_PERCENT Wert des Ressourcenpools für die Benutzer Auslastung. Siehe [Ressourcen Pool Konzepte](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor-resource-pool?#resource-pool-concepts).|
|**max_memory**|INT|Der MAX_MEMORY_PERCENT Wert des Ressourcenpools für die Benutzer Auslastung. Siehe [Ressourcen Pool Konzepte](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor-resource-pool?#resource-pool-concepts).|
|**max_sessions**|INT|Die maximal zulässige Anzahl von Sitzungen in der Benutzer Arbeits Auslastungs Gruppe.|
|**max_memory_grant**|INT|Der request_max_memory_grant_percent Wert für die Benutzer Arbeits Auslastungs Gruppe. Siehe [Erstellen einer Arbeits](https://docs.microsoft.com/sql/t-sql/statements/create-workload-group-transact-sql)Auslastungs Gruppe|
|**max_db_memory**|INT|Nur interne Verwendung.|
|**govern_background_io**|bit|Nur interne Verwendung.|
|**min_db_max_size_in_mb**|BIGINT|Der minimale max_size Wert für eine Datendatei in MB. Siehe [sys. database_files](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).|
|**max_db_max_size_in_mb**|BIGINT|Der maximale max_size Wert für eine Datendatei in MB. Siehe [sys. database_files](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).|
|**default_db_max_size_in_mb**|BIGINT|Der Standard max_size Wert für eine Datendatei in MB. Siehe [sys. database_files](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).|
|**db_file_growth_in_mb**|BIGINT|Standard Zuwachs Inkrement für eine Datendatei in MB. Siehe [sys. database_files](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).|
|**initial_db_file_size_in_mb**|BIGINT|Die Standardgröße für die neue Datendatei in MB. Siehe [sys. database_files](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).|
|**log_size_in_mb**|BIGINT|Die Standardgröße für die neue Protokolldatei in MB. Siehe [sys. database_files](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).|
|**instance_cap_cpu**|INT|Nur interne Verwendung.|
|**instance_max_log_rate**|BIGINT|Limit für die Protokoll Generierungs Rate für die SQL Server Instanz (in Bytes pro Sekunde). Gilt für alle von der-Instanz generierten Protokolle, `tempdb` einschließlich und anderer System Datenbanken. Bezieht sich in einem Pool für elastische Datenbanken auf Protokolle, die von allen Datenbanken im Pool generiert werden.|
|**instance_max_worker_threads**|INT|Der Arbeits Thread Grenzwert für die SQL Server Instanz.|
|**replica_type**|INT|Der Replikat-Typ, wobei 0 Primär und 1 sekundär ist.|
|**max_transaction_size**|BIGINT|Maximaler von einer Transaktion verwendeter Protokoll Speicher in KB.|
|**checkpoint_rate_mbps**|INT|Nur interne Verwendung.|
|**checkpoint_rate_io**|INT|Nur interne Verwendung.|
|**last_updated_date_utc**|datetime|Datum und Uhrzeit der letzten Einstellungs Änderung oder Neukonfiguration in UTC.|
|**primary_group_id**|INT|Die ID der Arbeits Auslastungs Gruppe für die Arbeitsauslastung des Benutzers auf dem primären Replikat|
|**primary_group_max_workers**|INT|Arbeits ThreadLimit für die Benutzer Arbeits Auslastungs Gruppe.|
|**primary_min_log_rate**|BIGINT|Minimale Protokoll Rate in Bytes pro Sekunde auf der Ebene der Benutzer Arbeits Auslastungs Gruppe. Die Ressourcenkontrolle versucht nicht, die Protokoll Rate unterhalb dieses Werts zu verringern.|
|**primary_max_log_rate**|BIGINT|Maximale Protokoll Rate in Bytes pro Sekunde auf der Ebene der Benutzer Arbeits Auslastungs Gruppe. Die Ressourcenkontrolle lässt keine Protokoll Rate oberhalb dieses Werts zu.|
|**primary_group_min_io**|INT|Minimaler IOPS-Aufwand für die Benutzer Arbeits Auslastungs Gruppe. Die Ressourcenkontrolle versucht nicht, IOPS unterhalb dieses Werts zu verringern.|
|**primary_group_max_io**|INT|Maximaler IOPS-Wert für die Benutzer Arbeits Auslastungs Gruppe. Die Ressourcenkontrolle lässt keine IOPS oberhalb dieses Werts zu.|
|**primary_group_min_cpu**|float|Minimaler CPU-Prozentsatz für die Benutzer Arbeits Auslastungs Gruppenebene. Die Ressourcenkontrolle versucht nicht, die CPU-Auslastung unterhalb dieses Werts zu verringern.|
|**primary_group_max_cpu**|float|Maximaler CPU-Prozentsatz für die Benutzer Arbeits Auslastungs Gruppenebene. Die Ressourcenkontrolle lässt keine CPU-Auslastung oberhalb dieses Werts zu.|
|**primary_log_commit_fee**|INT|Die protokolllitionscommit-Commit-Gebühr für die Benutzer Arbeits Auslastungs Gruppe in Bytes. Eine commitgebühr erhöht die Größe der einzelnen Protokoll-e/a-Vorgänge um einen bestimmten Wert für die Protokollierung der Protokoll Raten. Die tatsächliche Protokoll-e/a für den Speicher wird nicht angehoben.|
|**primary_pool_max_workers**|INT|Der Arbeits Thread Grenzwert für den workloadpool der Benutzer.|
|**pool_max_io**|INT|Maximaler IOPS-Grenzwert für den workloadpool für die Benutzer Auslastung.|
|**govern_db_memory_in_resource_pool**|bit|Nur interne Verwendung.|
|**volume_local_iops**|INT|Nur interne Verwendung.|
|**volume_managed_xstore_iops**|INT|Nur interne Verwendung.|
|**volume_external_xstore_iops**|INT|Nur interne Verwendung.|
|**volume_type_local_iops**|INT|Nur interne Verwendung.|
|**volume_type_managed_xstore_iops**|INT|Nur interne Verwendung.|
|**volume_type_external_xstore_iops**|INT|Nur interne Verwendung.|
|**volume_pfs_iops**|INT|Nur interne Verwendung.|
|**volume_type_pfs_iops**|INT|Nur interne Verwendung.|
|||

## <a name="permissions"></a>Berechtigungen

Diese Sicht erfordert die VIEW DATABASE STATE-Berechtigung.

## <a name="remarks"></a>Bemerkungen

Eine Beschreibung der Ressourcenkontrolle in der Azure SQL-Datenbank finden Sie unter [Ressourceneinschränkungen für SQL-Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server).

> [!IMPORTANT]
> Die meisten Daten, die von dieser DMV zurückgegeben werden, sind für den internen Gebrauch vorgesehen und können jederzeit geändert werden.

## <a name="examples"></a>Beispiele

Die folgende Abfrage, die im Kontext einer Benutzerdatenbank ausgeführt wird, gibt die maximale Protokoll Rate und die maximalen IOPS auf der Benutzer Arbeits Auslastungs Gruppe und auf der Ressourcenpool Ebene zurück. Für eine einzelne Datenbank wird eine Zeile zurückgegeben. Für eine Datenbank in einem Pool für elastische Datenbanken wird eine Zeile für jede Datenbank im Pool zurückgegeben.

```
SELECT database_name,
       primary_group_id,
       primary_max_log_rate,
       primary_group_max_io,
       pool_max_io
FROM sys.dm_user_db_resource_governance
ORDER BY database_name;  
```

## <a name="see-also"></a>Weitere Informationen

- [Ressourcenkontrolle](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor)
- [sys.dm_resource_governor_resource_pools (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql)
- [sys.dm_resource_governor_workload_groups (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql)
- [sys. dm_resource_governor_resource_pools_history_ex (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-history-ex-azure-sql-database)
- [sys.dm_resource_governor_workload_groups_history_ex (Azure SQL-Datenbank)](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-history-ex-azure-sql-database)
- [Transaktionsprotokollratengovernance](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Einzeldatenbank: DTU-Ressourcenlimits](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [Einzeldatenbank: V-Kern-Ressourcenlimits](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
