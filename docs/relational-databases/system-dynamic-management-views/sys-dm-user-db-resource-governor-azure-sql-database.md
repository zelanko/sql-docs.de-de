---
title: sys. DM _user_db_resource_governance (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2019
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
ms.openlocfilehash: ea07ba28efc4ac50fdeef04bb1b3643c359ead28
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176254"
---
# <a name="sysdm_user_db_resource_governance-transact-sql"></a>sys. DM _user_db_resource_governance (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Gibt ressourcengovernancekonfiguration und Kapazitäts Einstellungen für eine Azure SQL-Datenbank-Datenbank zurück.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_id**|ssNoversion|Die ID der Datenbank, die innerhalb eines Azure SQL-Datenbankservers eindeutig ist.|
|**logical_database_guid**|UNIQUEIDENTIFIER|Die logische GUID für die Benutzerdatenbank und bleibt während der Lebensdauer einer Benutzerdatenbank bestehen.  Durch das Umbenennen oder Festlegen einer Datenbank auf ein anderes SLO wird die GUID nicht geändert. |
|**physical_database_guid**|UNIQUEIDENTIFIER|Physische GUID für eine Benutzerdatenbank, die während der Lebensdauer der physischen Instanz der Benutzerdatenbank verbleibt. Das Festlegen auf ein anderes SLO bewirkt, dass diese Spalte geändert wird.|
|**server_name**|NVARCHAR|Der Name des logischen Servers.|
|**database_name**|NVARCHAR|Der Name der logischen Datenbank.|
|**slo_name**|NVARCHAR|Servicelevelziel und Hardware Generierung.|
|**dtu_limit**|ssNoversion|DTU-Grenzwert der Datenbank (null für VCore).|
|**cpu_limit**|ssNoversion|Vcore-Limit von Database (null für DTU-Datenbanken).|
|**min_cpu**|TINYINT|Minimaler CPU-Prozentsatz, der von der Benutzer Arbeitsauslastung verwendet werden kann.|
|**max_cpu**|TINYINT|Maximaler CPU-Prozentsatz, der von der Benutzer Arbeitsauslastung verwendet werden kann.|
|**cap_cpu**|TINYINT|Obergrenze der CPU-Prozent für Benutzer Arbeits Auslastungs Gruppen.|
|**min_cores**|SMALLINT|Anzahl der von SQL verwendeten CPUs.|
|**max_dop**|SMALLINT|Maximaler Grad an Parallelität, der von der Benutzer Arbeitsauslastung verwendet wird.|
|**min_memory**|ssNoversion|Minimaler Arbeitsspeicher Prozentsatz, der von der Benutzer Auslastung verwendet werden kann.|
|**max_memory**|ssNoversion|Maximaler Arbeitsspeicher Prozentsatz, der von der Benutzer Auslastung verwendet werden kann.|
|**max_sessions**|ssNoversion|Das Sitzungs Limit für die Benutzergruppe.|
|**max_memory_grant**|ssNoversion|Maximale Arbeitsspeicher Zuweisung für jede Abfrage in der Benutzer Arbeitsauslastung in Prozent.|
|**max_db_memory**|ssNoversion|Maximale Arbeitsspeicher Begrenzung für den Pufferpool für die Arbeitsauslastung der Benutzerdatenbank|
|**govern_background_io**|bit|Gibt an, ob Hintergrund Schreibvorgänge für die Benutzergruppe abgerechnet werden.|
|**min_db_max_size_in_mb**|BIGINT|Minimale maximale Größe der Datenbankdatei in MB.|
|**max_db_max_size_in_mb**|BIGINT|Maximale maximale Datenbankdatei in MB.|
|**default_db_max_size_in_mb**|BIGINT|Maximale Standardgröße für die Datenbankdatei in MB.|
|**db_file_growth_in_mb**|BIGINT|Standardmäßiges Wachstum der Azure-Datenbankdatei in MB.|
|**initial_db_file_size_in_mb**|BIGINT|Standardgröße der Datenbankdatei in MB.|
|**log_size_in_mb**|BIGINT|Standardgröße der Protokolldatei in MB.|
|**instance_cap_cpu**|ssNoversion|CPU-Abdeckung auf Instanzebene.|
|**instance_max_log_rate**|BIGINT|Die Rate der Protokoll Generierungs Rate auf Instanzebene in Byte pro Sekunde.|
|**instance_max_worker_threads**|ssNoversion|Grenzwert für Arbeits Thread auf Instanzebene.|
|**replica_type**|ssNoversion|Der Replikat-Typ, wobei 0 Primär und 1 sekundär ist.|
|**max_transaction_size**|BIGINT|Maximaler von einer Transaktion verwendeter Protokoll Speicher in KB.|
|**checkpoint_rate_mbps**|ssNoversion|Prüf Punkt Bandbreite in Mbit/s.|
|**checkpoint_rate_io**|ssNoversion|Prüfpunkt-e/a-Rate in ios pro Sekunde|
|**last_updated_date_utc**|DATETIME|Datum und Uhrzeit der letzten Einstellungs Änderung oder Neukonfiguration.|
|**primary_group_id**|ssNoversion|ID der primären Benutzer Arbeits Auslastungs Gruppe.|
|**primary_group_max_workers**|ssNoversion|Workerlimit auf der Ebene der Arbeitsauslastung der primären Benutzer|
|**primary_min_log_rate**|BIGINT|Minimale Protokoll Rate (Byte/Sek.) auf der Ebene der Arbeits Auslastungs Gruppe der primären Benutzer.|
|**primary_max_log_rate**|BIGINT|Maximale Protokoll Rate (Byte/Sek.) auf der Ebene der Arbeits Auslastungs Gruppe der primären Benutzer.|
|**primary_group_min_io**|ssNoversion|Minimale e/a auf der Ebene der Arbeitsauslastung der primären Benutzer.|
|**primary_group_max_io**|ssNoversion|Maximale e/a auf Arbeits Auslastungs Gruppenebene der primären Benutzer|
|**primary_group_min_cpu**|float|Minimaler CPU-Prozentsatz auf der Ebene der Arbeitsauslastung der primären Benutzer.|
|**primary_group_max_cpu**|float|Maximaler CPU-Prozentsatz auf der Ebene der Arbeitsauslastung der primären Benutzer.|
|**primary_log_commit_fee**|ssNoversion|Die richtlinienrichtliniencommit-Gebühr auf der Ebene der Arbeitsauslastung der primären|
|**primary_pool_max_workers**|ssNoversion|Workerlimit auf der Ebene des primären Benutzer Pools.
|**pool_max_io**|ssNoversion|Maximale e/a-Beschränkung auf der Ebene des primären Benutzer Pools.|
|**govern_db_memory_in_resource_pool**|bit|Gibt an, ob die maximale Größe des Pufferpools auf Ressourcenpool Ebene geregelt wird. Wird normalerweise für Datenbanken in elastischen Pools festgelegt.|
|**volume_local_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für lokales Volume (z. b. C:, D:).|
|**volume_managed_xstore_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für Remote Speicherkonto.|
|**volume_external_xstore_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für das Remote Speicherkonto, das von Azure SQL DB-Sicherungen und Telemetrie verwendet wird.|
|**volume_type_local_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für alle lokalen Volumes.|
|**volume_type_managed_xstore_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für alle Remote Speicher Konten, die von der Instanz verwendet werden.|
|**volume_type_external_xstore_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für alle Remote Speicher Konten, die von Azure SQL DB-Sicherungen und Telemetriedaten für die Instanz verwendet werden.|
|**volume_pfs_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für Storage Premium.|
|**volume_type_pfs_iops**|ssNoversion|Obergrenze für IOS pro Sekunde für den gesamten von der Instanz verwendeten Storage Premium-Speicher.|
|||

## <a name="permissions"></a>Berechtigungen

Diese Sicht erfordert die VIEW DATABASE STATE-Berechtigung.

## <a name="remarks"></a>Hinweise

Benutzer können auf diese dynamische Verwaltungs Sicht für die Ressourcensteuerungs-Konfigurations-und Kapazitäts Einstellungen für eine Azure SQL-DatenbankDatenbank zugreifen. 

> [!IMPORTANT]
> Die meisten Daten, die von dieser DMV festgestellt werden, sind für den internen Gebrauch vorgesehen und können geändert werden.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden die maximalen Daten der instanzdatenprotokollierung nach Datenbankname im Datenbankserver für eine einzelne oder in einem Pool zusammengefasste Datenbank zurückgegeben

```
SELECT database_name,
       primary_max_log_rate
FROM sys.dm_user_db_resource_governance
ORDER BY database_name DESC;  
```

## <a name="see-also"></a>Siehe auch

- [Governance für Transaktionsprotokoll Raten](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [DTU-Ressourcen Limits für einzelne Datenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [Ressourcen Limits für einzelne Datenbank-vkerne](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
