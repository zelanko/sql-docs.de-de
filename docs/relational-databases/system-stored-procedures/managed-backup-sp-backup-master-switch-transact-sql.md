---
title: managed_backup. sp_backup_master_switch (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
- sp_ backup_master_switch_TSQL
- smart_admin.sp_backup_master_switch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
ms.assetid: 1ed2b2b2-c897-41cc-bed5-1c6bc47b9dd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: eb140e5ff831373d2725bca82c70655c5745a658
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053536"
---
# <a name="managed_backupsp_backup_master_switch-transact-sql"></a>managed_backup. sp_backup_master_switch (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Hält [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] an bzw. setzt den Dienst fort.  
  
 Verwenden Sie diese gespeicherte Prozedur, um [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] vorübergehend anzuhalten und anschließend wieder fortzusetzen. Damit wird sichergestellt, dass alle Konfigurationseinstellungen erhalten bleiben und bei Fortsetzung der Vorgänge beibehalten werden. Beim Anhalten von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] wird die Beibehaltungsdauer nicht erzwungen. Das heißt, es erfolgt keine Überprüfung, um zu bestimmen, ob Dateien aus dem Speicher gelöscht werden müssen, ob Sicherungsdateien beschädigt sind oder ob eine Unterbrechung der Protokollkette vorliegt.  
  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC managed_backup.sp_backup_master_switch   
                     [@new_state = ] { 0 | 1}  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 @state  
 Legt den Status von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] fest. Der- @state Parameter ist " **Bit**". Beim Wert 0 werden die Vorgänge angehalten, während der Vorgang beim Wert 1 fortgesetzt wird.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="security"></a>Sicherheit  
 Beschreibt Sicherheitsaspekte in Bezug auf die statement.Include-Berechtigung in einem Unterabschnitt (H3-Überschrift). Erwägen Sie, ggf. weitere Unterabschnitte für Besitzverkettung und Überwachung einzuschließen.  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **db_backupoperator** Daten Bank Rolle mit **ALTER ANY CREDENTIAL** -Berechtigungen und **Execute** -Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory**.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel kann verwendet werden, um [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Instanz anzuhalten, für die es ausgeführt wird:  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
 Das folgende Beispiel kann verwendet werden, um [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] fortzusetzen.  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=1;  
Go  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltete SQL Server-Sicherung in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
