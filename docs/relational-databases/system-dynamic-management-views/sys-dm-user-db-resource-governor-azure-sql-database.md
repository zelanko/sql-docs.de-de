---
title: Sys.dm_user_db_resource_governance (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2019
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
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
manager: craigg
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: bb4c43fa4193d9254d7f06f24bd903f974739e87
ms.sourcegitcommit: a9a03f9a7ec4dad507d2dfd5ca33571580114826
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567636"
---
# <a name="sysdmuserdbresourcegovernance-transact-sql"></a>sys.dm_user_db_resource_governance (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Gibt Ressourcen-Governance-Einstellungen für Konfiguration und Kapazität für eine Azure SQL-Datenbank zurück.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|ssNoversion|ID der Datenbank, eindeutig innerhalb einer Azure SQL-Datenbank-Server.|
|**logical_database_guid**|UNIQUEIDENTIFIER|Logische Guid für die Benutzerdatenbank und bleibt während des Lebenszyklus einer Benutzerdatenbank.  Umbenennen oder Festlegen einer Datenbank auf einen anderen SLO ändert nicht die GUID. |
|**physical_database_guid**|UNIQUEIDENTIFIER|Physische Guid für eine Benutzerdatenbank, die während des Lebenszyklus der physischen Instanz von der Benutzerdatenbank bleibt. Einstellung, um einen anderen SLO führt dazu, dass diese Spalte zu ändern.|
|**server_name**|NVARCHAR|Name des logischen Servers.|
|**database_name**|NVARCHAR|Name der logischen Datenbank.|
|**slo_name**|NVARCHAR|Service Level Objective und Hardware generieren.|
|**dtu_limit**|ssNoversion|DTU-Limit der Datenbank (NULL für v-Kern).|
|**cpu_limit**|ssNoversion|vCore-Grenze der Datenbank (NULL für DTU-Datenbanken).|
|**min_cpu**|TINYINT|Minimaler CPU-Prozentsatz, die von Benutzer-Workloads verwendet werden kann.|
|**max_cpu**|TINYINT|Maximaler CPU-Prozentsatz, die vom Benutzer-Workloads verwendet werden kann.|
|**cap_cpu**|TINYINT|Die Obergrenze der CPU-Prozentsatz für die Workload-Benutzergruppen.|
|**min_cores**|SMALLINT|Anzahl der CPUs, die von SQL verwendet.|
|**max_dop**|SMALLINT|Maximalen Grad an Parallelität, die von Benutzer-Workloads verwendet.|
|**min_memory**|ssNoversion|Mindestens Erforderlicher Arbeitsspeicher-Prozentsatz, die vom Benutzer-Workloads verwendet werden kann.|
|**max_memory**|ssNoversion|Maximaler Arbeitsspeicher-Prozentsatz, die vom Benutzer-Workloads verwendet werden kann.|
|**max_sessions**|ssNoversion|Maximale Sitzungen für Benutzer die Gruppe.|
|**max_memory_grant**|ssNoversion|Maximale arbeitsspeicherzuweisung für jede Abfrage in benutzerworkload, in Prozent.|
|**max_db_memory**|ssNoversion|Max Buffer Pool Arbeitsspeicher Cap für Benutzer DB-Workloads|
|**govern_background_io**|bit|Gibt an, ob Schreibvorgänge im Hintergrund Benutzergruppe in Rechnung gestellt werden.|
|**min_db_max_size_in_mb**|BIGINT|Minimale, maximale Datenbank Dateigröße in MB.|
|**max_db_max_size_in_mb**|BIGINT|Maximale Max Datenbankdatei in MB.|
|**default_db_max_size_in_mb**|BIGINT|Standardmäßige maximale Datenbank Dateigröße in MB an.|
|**db_file_growth_in_mb**|BIGINT|Standard-Wachstum der Azure Datenbankdatei in MB.|
|**initial_db_file_size_in_mb**|BIGINT|Standard-Datenbank Dateigröße in MB.|
|**log_size_in_mb**|BIGINT|Standardmäßige Protokolldateigröße in MB.|
|**instance_cap_cpu**|ssNoversion|CPU-Obergrenze auf Instanzebene.|
|**instance_max_log_rate**|BIGINT|Melden Sie sich Generation Rate Obergrenze auf Ebene der Serverinstanz, in Bytes pro Sekunde.|
|**instance_max_worker_threads**|ssNoversion|Begrenzung für die Worker-Threads auf Instanzebene.|
|**replica_type**|ssNoversion|Replikattyp, wobei 0 wird als primäres, und 1 ist.|
|**max_transaction_size**|BIGINT|Max. Speicherplatz verwendet, die durch eine Transaktion, in KB.|
|**checkpoint_rate_mbps**|ssNoversion|Prüfpunkt Bandbreite in Mbit/s.|
|**checkpoint_rate_io**|ssNoversion|Prüfpunkt in IOs-e/a-Rate pro Sekunde.|
|**last_updated_date_utc**|DATETIME|Datum und Uhrzeit der letzten einstellungsänderung oder Neukonfiguration.|
|**primary_group_id**|ssNoversion|Arbeitsauslastungsgruppe für die primären Benutzer-ID.|
|**primary_group_max_workers**|ssNoversion|Begrenzung für Worker auf Gruppenebene für Hauptbenutzer-arbeitsauslastung.|
|**primary_min_log_rate**|BIGINT|Minimale protokollrate (Bytes pro Sekunde) auf Gruppenebene für Hauptbenutzer-arbeitsauslastung.|
|**primary_max_log_rate**|BIGINT|Maximalen Rate (Byte / s) auf Gruppenebene für Hauptbenutzer-arbeitsauslastung.|
|**primary_group_min_io**|ssNoversion|Minimale e/a auf Gruppenebene für Hauptbenutzer-arbeitsauslastung.|
|**primary_group_max_io**|ssNoversion|Maximale e/a auf Gruppenebene für Hauptbenutzer-arbeitsauslastung.|
|**primary_group_min_cpu**|FLOAT|Minimaler CPU-Prozentsatz auf Gruppenebene für Hauptbenutzer-Workload zu beschränken.|
|**primary_group_max_cpu**|FLOAT|Maximaler CPU-Prozentsatz auf Gruppenebene für Hauptbenutzer-Workload zu beschränken.|
|**primary_log_commit_fee**|ssNoversion|Log Rate Governance Commit Gebühr auf Gruppenebene für Hauptbenutzer-arbeitsauslastung.|
|**primary_pool_max_workers**|ssNoversion|Begrenzung für Worker auf Ebene der primären Benutzer-Pool.
|**pool_max_io**|ssNoversion|Maximale e/a-Grenzwert auf Ebene der primären Benutzer-Pool.|
|**govern_db_memory_in_resource_pool**|bit|Der angibt, ob die maximale Größe des Pufferpools auf ressourcenpoolebene gesteuert wird. Legen Sie in der Regel für Datenbanken in Pools für elastische Datenbanken.|
|**volume_local_iops**|ssNoversion|IOs-pro Sekunde Obergrenze für die lokale Volume (z. B. "c:", "d:").|
|**volume_managed_xstore_iops**|ssNoversion|IOs-pro Sekunde Obergrenze für die remote-Storage-Konto.|
|**volume_external_xstore_iops**|ssNoversion|IOs-pro Sekunde Obergrenze für die remote-Storage-Konto, die von Azure SQL-Datenbank-Sicherungen und Telemetriedaten verwendet werden.|
|**volume_type_local_iops**|ssNoversion|IOs-pro Sekunde Obergrenze für alle lokalen Volumes.|
|**volume_type_managed_xstore_iops**|ssNoversion|IOs-pro Sekunde Obergrenze für alle remote-Speicherkonten, die von der Instanz verwendet.|
|**volume_type_external_xstore_iops**|ssNoversion|IOs pro zweite Abdeckung für alle Remoteserver Speicherkonten, die für die Instanz von Azure SQL-Datenbank-Sicherungen und Telemetrie verwendet.|
|**volume_pfs_iops**|ssNoversion|IOs-pro Sekunde Obergrenze für die File Storage Premium.|
|**volume_type_pfs_iops**|ssNoversion|IOs-pro Sekunde Abdeckung für alle Premium File Storage, die von der Instanz verwendeten.|
|||

## <a name="permissions"></a>Berechtigungen

Diese Sicht erfordert die VIEW DATABASE STATE-Berechtigung.

## <a name="remarks"></a>Hinweise

Benutzer können diese dynamische verwaltungssicht für Governance-Ressourcenkonfiguration und die kapazitätseinstellungen für eine Azure SQL-Datenbank zugreifen. 

> [!IMPORTANT]
> Die meisten Daten, die von dieser DMV verfügbar gemacht, die für den internen Gebrauch vorgesehen ist und unterliegt Änderungen.

## <a name="examples"></a>Beispiele

Im folgende Beispiel gibt die maximale Log Rate Instanzdaten anhand des Namens der Datenbank innerhalb der Datenbankserver für eine einzelne oder in einem Pool zusammengefassten Datenbank sortiert zurück.

```
SELECT database_name,
       primary_max_log_rate
FROM sys.dm_user_db_resource_governance
ORDER BY database_name DESC;  
```

## <a name="see-also"></a>Siehe auch

- [Transaction Log Rate governance](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Ressourceneinschränkungen für einzeldatenbanken-DTUS](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [Ressourceneinschränkungen für einzeldatenbanken vCore](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
