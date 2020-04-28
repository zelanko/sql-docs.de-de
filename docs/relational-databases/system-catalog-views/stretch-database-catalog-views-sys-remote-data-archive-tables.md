---
title: sys. remote_data_archive_tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_tables
- sys.remote_data_archive_tables_TSQL
- remote_data_archive_tables
- remote_data_archive_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_tables catalog view
ms.assetid: 765069b7-60fd-414c-875f-3455460b75cd
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 65e42e6303b467abd38ddadb6be0c0d0fece46e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68018191"
---
# <a name="stretch-database-catalog-views---sysremote_data_archive_tables"></a>Stretch Database Katalog Sichten-sys. remote_data_archive_tables
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Remote Tabelle, in der Daten aus einer Stretch-aktivierten lokalen Tabelle gespeichert werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die Objekt-ID der Stretch-aktivierten lokalen Tabelle.|  
|**remote_database_id**|**int**|Der automatisch generierte lokale Bezeichner der Remote Datenbank.|  
|**remote_table_name**|**sysname**|Der Name der Tabelle in der Remote Datenbank, die der Stretch-aktivierten lokalen Tabelle entspricht.|  
|**filter_predicate**|**nvarchar(max)**|Das Filter Prädikat, falls vorhanden, das die zu migrierenden Zeilen in der zu migrierenden Tabelle identifiziert. Wenn der Wert null ist, ist die gesamte Tabelle für eine Migration berechtigt.<br /><br /> Weitere Informationen finden Sie unter [Aktivieren von Stretch Database für eine Tabelle](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) und [auswählen zu migrierender Zeilen mithilfe eines Filter Prädikats](~/sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).|  
|**migration_direction**|**tinyint**|Die Richtung, in der Daten zurzeit migriert werden. Die folgenden Werte sind verfügbar:<br/>1 (ausgehend)<br/>2 (eingehend)|  
|**migration_direction_desc**|**nvarchar(60)**|Die Beschreibung der Richtung, in der Daten gerade migriert werden. Die folgenden Werte sind verfügbar:<br/>Ausgehend (1)<br/>eingehend (2)|  
|**is_migration_paused**|**bit**|Gibt an, ob die Migration zurzeit angehalten ist.|  
|**is_reconciled**|**bit**| Gibt an, ob die Remote Tabelle und die SQL Server Tabelle synchronisiert sind.<br/><br/>Wenn **is_reconciled** den Wert 1 (true) hat, sind die Remote Tabelle und die SQL Server Tabelle synchron, und Sie können Abfragen ausführen, die die Remote Daten enthalten.<br/><br/>Wenn der Wert von **is_reconciled** 0 (false) ist, sind die Remote Tabelle und die SQL Server Tabelle nicht synchron. Vor kurzem migrierte Zeilen müssen erneut migriert werden. Dies tritt auf, wenn Sie die Azure-Remote Datenbank wiederherstellen oder wenn Sie Zeilen manuell aus der Remote Tabelle löschen. Bis Sie die Tabellen abgestimmt haben, können Sie keine Abfragen ausführen, die die Remote Daten enthalten. Führen Sie [sys. sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)aus, um die Tabellen abzustimmen. |  
  
## <a name="see-also"></a>Weitere Informationen  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

