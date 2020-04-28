---
title: sp_delete_backup_file_snapshot (Transact-SQL) | Microsoft-Dokumentation
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.custom: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5afe5530-a404-4fa5-af3c-bc7c3ca43ce6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cf376712d51f542f6da5eaa8e89b53779eda0c07
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67941837"
---
# <a name="sp_delete_backup_file_snapshot-transact-sql"></a>sp_delete_backup_file_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Löscht einen angegebenen Sicherungssnapshot aus der angegebenen Datenbank. Verwenden Sie diese gespeicherte System Prozedur in Verbindung mit der Systemfunktion **sys. fn_db_backup_file_snapshots** , um verwaiste Sicherungs Momentaufnahmen zu identifizieren und zu löschen. Weitere Informationen finden Sie unter [Dateimomentaufnahme-Sicherungen für Datenbankdateien in Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_delete_backup_file_snapshot  
    [ @db_name = ] N'<database_name>  
    , [ @snapshot_url = ] N'<snapshot_url>  
```  
  
## <a name="arguments"></a>Argumente  
 *[ @db_name =] database_name*  
 Der Name der Datenbank mit der zu löschenden Momentaufnahme, die als Unicode-Zeichenfolge bereitgestellt wird.  
  
 *[ @snapshot_url =] snapshot_url*  
 Die URL der zu löschenden Momentaufnahme, die als Unicode-Zeichenfolge bereitgestellt wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY DATABASE-Berechtigung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. fn_db_backup_file_snapshots &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
