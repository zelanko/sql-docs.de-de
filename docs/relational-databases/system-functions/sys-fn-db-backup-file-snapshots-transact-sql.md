---
title: Sys. fn_db_backup_file_snapshots (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7845ef36347d9131ed6991674b4e09b23ee34155
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670430"
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>Sys. fn_db_backup_file_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt zurück, die Datenbankdateien zugeordnete Azure-Momentaufnahmen. Wenn die angegebene Datenbank nicht gefunden wird, oder wenn die Datenbankdateien nicht in Microsoft Azure-Blob-Speicherdienst gespeichert sind, werden keine Zeilen zurückgegeben. Verwenden von dieser Systemfunktion in Verbindung mit der **sp_delete_backup_file_snapshot** gespeicherte Systemprozedur, um zu identifizieren und löschen verwaiste Sicherungsdatei-Momentaufnahmen. Weitere Informationen finden Sie unter [Dateimomentaufnahme-Sicherungen für Datenbankdateien in Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>Argumente  
 *Datenbankname*  
 Der Name der Datenbank, die abgefragt wird. Wenn der Wert NULL ist, wird diese Funktion im aktuellen Datenbankbereich ausgeführt.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|Die Datei-ID für die Datenbank. Lässt keine NULL-Werte zu.|  
|snapshot_time|**nvarchar(260)**|Der Zeitstempel der Momentaufnahme wie er von der REST-API zurückgegeben wird. Gibt NULL zurück, wenn keine Momentaufnahme vorhanden ist.|  
|snapshot_url|**nvarchar(360)**|Die vollständige URL der Datei-Momentaufnahme. Gibt NULL, wenn keine Momentaufnahme vorhanden sein.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung für die Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
