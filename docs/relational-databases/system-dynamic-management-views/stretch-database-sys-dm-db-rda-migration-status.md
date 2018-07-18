---
title: dm_db_rda_migration_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e0ee1d106a9f52dd30518f9ead02847dc879ff2c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38048768"
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Stretch Database - dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Batch von migrierten Daten aus jeder Stretch-aktivierte Tabelle auf der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Batches werden durch ihre Start- und Endzeit identifiziert.  
  
 **dm_db_rda_migration_status** bezieht sich auf der aktuellen Datenbank verwendet. Stellen Sie sicher, dass Sie im Kontext Datenbank der Stretch-fähigen Tabellen sind für den Migrationsstatus angezeigt werden sollen.  
  
 In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], die Ausgabe des **dm_db_rda_migration_status** ist auf 200 Zeilen beschränkt.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Die ID der Tabelle aus der Zeilen migriert wurden.|  
|**database_id**|**int**|Die ID der Datenbank aus der Zeilen migriert wurden.|  
|**migrated_rows**|**bigint**|Die Anzahl der Zeilen, die in diesem Batch migriert werden.|  
|**start_time_utc**|**datetime**|Die UTC-Zeit, an dem der Batch gestartet wurde.|  
|**end_time_utc**|**datetime**|Die UTC-Zeit, an dem der Batch beendet.|  
|**error_number**|**int**|Wenn der Batch, die Fehlernummer des Fehlers ein Fehler, die aufgetreten sind auftritt; andernfalls Null.|  
|**error_severity**|**int**|Wenn der Batch, den Schweregrad des Fehlers ein Fehler, die aufgetreten sind auftritt; andernfalls Null.|  
|**error_state**|**int**|Wenn der Batch, den Status des Fehlers ein Fehler, die aufgetreten sind auftritt; andernfalls Null.<br /><br /> Die **Error_state** gibt an, die Bedingung oder den Speicherort, in dem der Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
