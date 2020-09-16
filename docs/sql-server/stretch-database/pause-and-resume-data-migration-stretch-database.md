---
description: Anhalten und Fortsetzen der Datenmigration (Stretch Database)
title: Anhalten und Fortsetzen der Datenmigration
ms.date: 06/14/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, pausing and resuming
- pausing Stretch Database
- resuming Stretch Database
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 5146c258c099c487643ca343ecd06402fc623c84
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468962"
---
# <a name="pause-and-resume-data-migration-stretch-database"></a>Anhalten und Fortsetzen der Datenmigration (Stretch Database)
[!INCLUDE [sqlserver2016-windows-only](../../includes/applies-to-version/sqlserver2016-windows-only.md)]


  Zum Anhalten oder Fortsetzen der Migration von Daten zu Azure wählen Sie **Stretch** für eine Tabelle in SQL Server Management Studio, und wählen Sie dann **Anhalten** , um die Datenmigration anzuhalten, bzw. **Fortsetzen** , um die Datenmigration fortzusetzen. Sie können auch Transact-SQL verwenden, um die Migration von Daten anzuhalten oder fortzusetzen.  
  
 Halten Sie die Datenmigration für einzelne Tabellen an, wenn Sie Probleme auf dem lokalen Server behandeln oder die verfügbare Netzwerkbandbreite maximieren möchten.  

## <a name="pause-data-migration"></a>Anhalten der Datenmigration  
  
### <a name="use-sql-server-management-studio-to-pause-data-migration"></a>Verwenden von SQL Server Management Studio zum Anhalten der Datenmigration  
  
1.  Wählen Sie in SQL Server Management Studio im Objekt-Explorer die für die Streckung aktivierte Tabelle aus, für die Sie die Datenmigration anhalten möchten.  
  
2.  Klicken Sie mit der rechten Maustaste, und wählen Sie **Stretch**. Wählen Sie dann **Anhalten**aus.  
  
### <a name="use-transact-sql-to-pause-data-migration"></a>Verwenden von Transact-SQL zum Anhalten der Datenmigration  
 Führen Sie den folgenden Befehl aus.  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO 
```  
  
## <a name="resume-data-migration"></a>Fortsetzen der Datenmigration  
  
### <a name="use-sql-server-management-studio-to-resume-data-migration"></a>Verwenden von SQL Server Management Studio zum Fortsetzen der Datenmigration  
  
1.  Wählen Sie in SQL Server Management Studio im Objekt-Explorer die für die Streckung aktivierte Tabelle aus, für die Sie die Datenmigration fortsetzen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste, und wählen Sie **Stretch**. Wählen Sie dann **Fortsetzen**.  
  
### <a name="use-transact-sql-to-resume-data-migration"></a>Verwenden von Transact-SQL zum Fortsetzen der Datenmigration  
 Führen Sie den folgenden Befehl aus.  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>   
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
 GO
```  

## <a name="check-whether-migration-is-active-or-paused"></a>Überprüfen Sie, ob die Migration aktiv ist oder angehalten wurde.

### <a name="use-sql-server-management-studio-to-check-whether-migration-is-active-or-paused"></a>Verwenden Sie SQL Server Management Studio, um zu überprüfen, ob die Migration aktiv ist oder angehalten wurde.
Öffnen Sie in SQL Server Management Studio die Option **Stretch Database-Überwachung** , und überprüfen Sie den Wert der Spalte **Migrationsstatus** . Weitere Informationen finden Sie unter [Überwachung und Problembehandlung für die Datenmigration](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).

### <a name="use-transact-sql-to-check-whether-migration-is-active-or-paused"></a>Überprüfen Sie mit Transact-SQL, ob die Migration aktiv ist oder angehalten wurde.
Fragen Sie die Katalogsicht **sys.remote_data_archive_tables** ab, und überprüfen Sie den Wert der Spalte **is_migration_paused** . Weitere Informationen finden Sie unter [sys.remote_data_archive_tables](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md).

## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[Überwachung und Problembehandlung bei der Datenmigration](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  
