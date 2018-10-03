---
title: Backupmediafamily (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7dc119aaaf24457bc9267ee750ce82a9a4a69104
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687258"
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Medienfamilie. Wenn sich eine Medienfamilie in einem gespiegelten Mediensatz befindet, verfügt die Familie über eine separate Zeile für jede Spiegelung im Mediensatz. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
    
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Eindeutige ID, die den Mediensatz kennzeichnet, in dem diese Familie ein Element ist. Verweise **backupmediaset(media_set_id)**|  
|**family_sequence_number**|**tinyint**|Position dieser Medienfamilie im Mediensatz.|  
|**media_family_id**|**uniqueidentifier**|Eindeutige ID, die die Medienfamilie kennzeichnet. Kann den Wert NULL haben.|  
|**media_count**|**int**|Anzahl der Medien in der Medienfamilie. Kann den Wert NULL haben.|  
|**logical_device_name**|**nvarchar(128)**|Name dieses Sicherungsmediums in **sys.backup_devices.name**. Wenn dies ein temporäres Sicherungsmedium ist (im Gegensatz zu einem dauerhaften Sicherungsmedium, das in vorhanden **Sys. backup_devices**), den Wert der **Logical_device_name** ist NULL.|  
|**physical_device_name**|**nvarchar(260)**|Physischer Name des Sicherungsmediums. Kann den Wert NULL haben. Dieses Feld wird von sicherungs-und Wiederherstellungsprozesses gemeinsam genutzt. Es kann es sich um den ursprünglichen Sicherungsziel oder der ursprüngliche Quellpfad für die Wiederherstellung enthalten. Je nachdem, ob sicherungs- oder Wiederherstellungsvorgang zuerst auf einem Server für eine Datenbank aufgetreten ist. Beachten Sie, dass es sich bei aufeinander folgenden Wiederherstellungen aus der gleichen Datei zu sichern wird den Pfad, unabhängig von deren Standort nicht zum Zeitpunkt der Wiederherstellung aktualisiert. Aus diesem Grund **"physical_device_name"** Feld kann nicht verwendet werden, um die verwendete Wiederherstellungspfad finden Sie unter.|  
|**device_type**|**tinyint**|Typ des Sicherungsmediums:<br /><br /> 2 = Datenträger<br /><br /> 5 = Band<br /><br /> 7 = Virtuelles Medium<br /><br /> 9 = Azure-Speicher<br /><br /> 105 = ein dauerhaftes Sicherungsmedium.<br /><br /> Kann den Wert NULL haben.<br /><br /> Alle permanenter Medien-Namen und Nummern finden Sie in **Sys. backup_devices**.|  
|**physical_block_size**|**int**|Physische Blockgröße, die zum Schreiben der Medienfamilie verwendet wurde. Kann den Wert NULL haben.|  
|**Spiegelserver**|**tinyint**|Spiegelnummer (0-3).|  
  
## <a name="remarks"></a>Hinweise  
 RESTORE VERIFYONLY FROM *Backup_device* WITH LOADHISTORY füllt die Spalten der **Backupmediaset** Tabelle mit den entsprechenden Werten aus dem mediensatzheader.  
  
 Um die Anzahl der Zeilen in dieser Tabelle und in anderen Tabellen sicherungs- und Verlaufstabellen zu verringern, führen Sie die [Sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) gespeicherte Prozedur.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern und Wiederherstellen von Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
