---
title: sys. backup_devices (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backup_devices_TSQL
- backup_devices
- sys.backup_devices
- sys.backup_devices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], viewing information
- sys.backup_devices catalog view
ms.assetid: 457edaa4-aca1-4bd3-bf8d-734490b80fcd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f9299bdefc1c0c21d7144719139a0fb5fdd9a7d2
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279326"
---
# <a name="sysbackup_devices-transact-sql"></a>sys.backup_devices (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jedes Sicherungsmedium, das mithilfe von **sp_addumpdevice** registriert oder in erstellt wurde [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name des Sicherungsmediums. Ist im Sicherungssatz eindeutig.|  
|**type**|**tinyint**|Typ des Sicherungsmediums:<br /><br /> 2 = Datenträger<br /><br /> 3 = Diskette (veraltet)<br /><br /> 5 = Band<br /><br /> 6 = Pipe (veraltet)<br /><br /> 7 = Virtuelles Medium (für die optionale Verwendung von Drittsicherungsanbietern)<br /><br /> 9 = URL<br /><br />In der Regel werden nur Datenträger (2) und URL (9) verwendet.|  
|**type_desc**|**nvarchar(60)**|Beschreibung des Sicherungsmediumtyps:<br /><br /> DISK<br /><br /> DISKETTE (veraltet)<br /><br /> TAPE<br /><br /> PIPE (veraltet)<br /><br /> VIRTUAL_DEVICE (für die optionale Verwendung von Sicherungsdrittanbietern)<br /><br /> URL <br /><br /> In der Regel werden nur der Datenträger und die URL verwendet.|  
|**physical_name**|**nvarchar(260)**|Physischer Dateiname oder Pfad des Sicherungsmediums.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [Katalog Sichten für Datenbanken und Dateien &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
