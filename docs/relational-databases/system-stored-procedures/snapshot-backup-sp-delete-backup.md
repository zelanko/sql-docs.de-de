---
description: sp_delete_backup (Transact-SQL)
title: sp_delete_backup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cc62c8e07de682aa075371561d3c95187c7c86c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469757"
---
# <a name="sp_delete_backup-transact-sql"></a>sp_delete_backup (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Löscht alle Momentaufnahmen und die Sicherungsdatei, die einen Momentaufnahme-Sicherungs Satz aus der angegebenen Datenbank enthalten. Diese gespeicherte System Prozedur ist die einzige empfohlene Methode zum Verwalten von Momentaufnahme-Sicherungs Sätzen. Weitere Informationen finden Sie unter [Dateimomentaufnahme-Sicherungen für Datenbankdateien in Azure](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_delete_backup   
    [ @backup_url = ] backup_metadata_file_url  
    ,[ [ @db_name = ] database_name | NULL ]  
```  
  
## <a name="arguments"></a>Argumente  
 *[ @backup_url =] backup_meta_file_url*  
 Die URL der zu löschenden Sicherung, die alle Momentaufnahmen, die den angegebenen Sicherungs Satz enthalten, einschließlich der Sicherungsdatei selbst löscht.  
  
 *[ @db_name =] database_name*  
 Der Name der Datenbank mit der zu löschenden Momentaufnahme. Wenn ein Datenbankname angegeben wird, überprüft das System, ob die angegebene Backup-URL eine Sicherungs-URL für die angegebene Datenbank ist, und verwendet [sp_delete_backup_file_snapshot &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md) , um die einzelnen Momentaufnahmen zu löschen. Wenn kein Datenbankname angegeben wird, wird diese Daten Bank Überprüfung nicht durchgeführt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY DATABASE-Berechtigung oder die ALTER-Berechtigung für die angegebene Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. fn_db_backup_file_snapshots &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
