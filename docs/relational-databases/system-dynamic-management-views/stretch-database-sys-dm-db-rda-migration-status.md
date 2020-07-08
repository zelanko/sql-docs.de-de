---
title: sys. dm_db_rda_migration_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 1e383b01ce40dbb03f5134bf5374b9b39bc2a99e
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053486"
---
# <a name="stretch-database---sysdm_db_rda_migration_status"></a>Stretch Database-sys. dm_db_rda_migration_status
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Enthält eine Zeile für jeden Batch von migrierten Daten aus jeder Stretch-aktivierten Tabelle in der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Batches werden anhand ihrer Startzeit und Endzeit identifiziert.  
  
 **sys. dm_db_rda_migration_status** ist auf den aktuellen Daten Bank Kontext beschränkt. Stellen Sie sicher, dass Sie sich im Daten Bank Kontext der Stretch-enable-Tabellen befinden, für die Sie den Migrationsstatus anzeigen möchten.  
  
 In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ist die Ausgabe von **sys. dm_db_rda_migration_status** auf 200 Zeilen beschränkt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Die ID der Tabelle, aus der die Zeilen migriert wurden.|  
|**database_id**|**int**|Die ID der Datenbank, aus der die Zeilen migriert wurden.|  
|**migrated_rows**|**bigint**|Die Anzahl der in diesem Batch migrierten Zeilen.|  
|**start_time_utc**|**datetime**|Die UTC-Zeit, zu der der Batch gestartet wurde.|  
|**end_time_utc**|**datetime**|Die UTC-Zeit, zu der der Batch beendet wurde.|  
|**error_number**|**int**|Wenn der Batch fehlschlägt, wird die Fehlernummer des aufgetretenen Fehlers angezeigt. andernfalls NULL.|  
|**error_severity**|**int**|Wenn der Batch fehlschlägt, wird der Schweregrad des aufgetretenen Fehlers verursacht. andernfalls NULL.|  
|**error_state**|**int**|Wenn der Batch fehlschlägt, wird der Status des aufgetretenen Fehlers angezeigt. andernfalls NULL.<br /><br /> Der **ERROR_STATE** gibt die Bedingung oder den Speicherort an, an dem der Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
