---
title: sys. remote_data_archive_tables (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie sys. remote_data_archive_tables eine Zeile für jede Remote Tabelle enthält, in der Daten aus einer Stretch-aktivierten lokalen Tabelle gespeichert werden.
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
ms.openlocfilehash: c4b2b32181360b9974a3acfe85cb166d7ebd515d
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248139"
---
# <a name="stretch-database-catalog-views---sysremote_data_archive_tables"></a>Stretch Database Katalog Sichten-sys. remote_data_archive_tables
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

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
  
  

