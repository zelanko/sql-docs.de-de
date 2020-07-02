---
title: Backup File Group (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupfilegroup_TSQL
- backupfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], backupfilegroup system table
- backupfilegroup system table
ms.assetid: d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f35d035779b5d26fe47c41c06a2b91a39f8da407
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750381"
---
# <a name="backupfilegroup-transact-sql"></a>backupfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jede Dateigruppe in einer Datenbank zum Zeitpunkt der Sicherung. **Backup File Group** wird in der **msdb** -Datenbank gespeichert.  
  
> [!NOTE]  
>  Die **Backup File Group** -Tabelle zeigt die Dateigruppen Konfiguration der Datenbank und nicht den Sicherungs Satz. Verwenden Sie die Spalte **is_present** der Backup [File](../../relational-databases/system-tables/backupfile-transact-sql.md) -Tabelle, um zu ermitteln, ob eine Datei im Sicherungs Satz enthalten ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|Sicherungssatz, der diese Dateigruppe enthält.|  
|**name**|**sysname**|Name der Dateigruppe.|  
|**filegroup_id**|**int**|ID der Dateigruppe. Sie ist innerhalb der Datenbank eindeutig. Entspricht **data_space_id** in **sys. File Groups**.|  
|**filegroup_guid**|**uniqueidentifier**|GUID der Dateigruppe. Kann den Wert NULL haben.|  
|**type**|**char(2)**|Inhaltstyp. Folgende Werte sind möglich:<br /><br /> FG = Zeilendateigruppe<br /><br /> SL = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokolldateigruppe|  
|**type_desc**|**nvarchar(60)**|Beschreibung des Funktionstyps. Folgende Werte sind möglich:<br /><br /> ROWS_FILEGROUP<br /><br /> SQL_LOG_FILEGROUP|  
|**is_default**|**bit**|Die Standarddateigruppe, die verwendet wird, wenn keine Dateigruppe in CREATE TABLE oder CREATE INDEX angegeben ist.|  
|**is_readonly**|**bit**|1 = Die Dateigruppe ist schreibgeschützt.|  
|**log_filegroup_guid**|**uniqueidentifier**|Kann den Wert NULL haben.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!IMPORTANT]  
>  Ein Dateigruppenname kann in unterschiedlichen Datenbanken auftreten. Jede Dateigruppe verfügt jedoch über eine eigene GUID. Daher ist **(backup_set_id filegroup_guid)** ein eindeutiger Schlüssel, der eine Datei Gruppe in **Backup File Group**identifiziert.  
  
 RESTORE VERIFYONLY FROM *backup_device* mit LOADHISTORY füllt die Spalten der **Backup Mediaset** -Tabelle mit den entsprechenden Werten aus dem Medien Satz Header auf.  
  
 Führen Sie die gespeicherte Prozedur [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) aus, um die Anzahl der Zeilen in dieser Tabelle und in anderen Sicherungs-und Verlaufs Tabellen zu verringern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
