---
title: Sp_delete_backup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fbf04bbd9b60a99a2e972db139daaf8bb4361389
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43037453"
---
# <a name="spdeletebackup-transact-sql"></a>Sp_delete_backup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Löscht alle Momentaufnahmen und die Sicherungsdatei, die einen Snapshot Sicherungssatz aus der angegebenen Datenbank umfassen. Diese gespeicherte Systemprozedur ist die einzige empfohlene Methode zum Verwalten von Sicherungssätzen Momentaufnahme. Weitere Informationen finden Sie unter [Dateimomentaufnahme-Sicherungen für Datenbankdateien in Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_delete_backup   
    [ @backup_url = ] backup_metadata_file_url  
    ,[ [ @db_name = ] database_name | NULL ]  
```  
  
## <a name="arguments"></a>Argumente  
 *[ @backup_url =] Backup_meta_file_url*  
 Die URL der Sicherung gelöscht werden muss, die wodurch alle Momentaufnahmen, die mit den angegebenen Sicherungssatz einschließlich die Sicherungsdatei selbst gelöscht.  
  
 *[ @db_name =] Datenbankname*  
 Der Name der Datenbank mit der Momentaufnahme gelöscht werden soll. Wenn ein Datenbankname angegeben wird, das System stellt sicher, dass die sicherungs-URL bereitgestellt wird, ist eine sicherungs-URL für die angegebene Datenbank und verwendet [Sp_delete_backup_file_snapshot &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) jede Momentaufnahme löschen. Wenn kein Datenbankname angegeben wird, wird diese Überprüfung nicht ausgeführt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert ALTER ANY DATABASE-Berechtigung oder ALTER-Berechtigung für die angegebene Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
