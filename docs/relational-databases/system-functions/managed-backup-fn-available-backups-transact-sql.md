---
title: managed_backup. fn_available_backups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_available_backups
- smart_admin.fn_available_backups_TSQL
- fn_available_backups_TSQL
- fn_available_backups
dev_langs:
- TSQL
helpviewer_keywords:
- fn_available_backups
- smart_admin.fn_available_backups
ms.assetid: 7aa84474-16e5-49bd-a703-c8d1408ef107
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c9cbad2124420f62f50c8497fcc5baa21720634
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052886"
---
# <a name="managed_backupfn_available_backups-transact-sql"></a>managed_backup. fn_available_backups (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen der verfügbaren Sicherungsdateien für die angegebene Datenbank zurück. Die zurückgegebenen Sicherungsdateien sind von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] erstellte Sicherungen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
managed_backup.fn_available_backups ([@database_name = ] 'database name')  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 @database_name  
 Der Name der Datenbank. Ist vom Datentyp @database_name nvarchar (512).  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
 Für die Tabelle ist eine eindeutige gruppierte Einschränkung aktiv (database_guid, backup_start_date und first_lsn, backup_type).   
Wenn eine Datenbank gelöscht und anschließend erneut erstellt wird, werden die Sicherungssätze für alle Datenbanken zurückgegeben. Die Ausgabe wird nach der database_guid sortiert, anhand derer die jeweiligen Datenbanken eindeutig identifiziert werden.   
Bei Lücken in der LSN, die eine Unterbrechung der Protokollkette anzeigen, enthält die Tabelle eine spezielle Zeile für jedes fehlende LSN-Segment.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|Backup_path|NVARCHAR(260) COLLATE Latin1_General_CI_AS_KS_WS|Die URL der Sicherungsdatei.|  
|backup_type|Nvarchar (6)|' DB ' für die Datenbanksicherung ' log ' für die Protokoll Sicherung|  
|expiration_date|DATETIME|Das Datum, zu dem die Löschung dieser Datei erwartet wird. Diese Einstellung basiert auf der Fähigkeit der Datenbank, zu einem bestimmten Zeitpunkt während der angegebenen Beibehaltungsdauer eine Wiederherstellung durchzuführen.|  
|database_guid|UNIQUEIDENTIFIER|Der GUID-Wert für die angegebene Datenbank.  Mit einer GUID wird eine Datenbank eindeutig angegeben.|  
|first_lsn|NUMERIC(25, 0)|Protokollfolgenummer des ersten oder ältesten Protokolldatensatzes im Sicherungssatz. Kann den Wert NULL haben.|  
|last_lsn|NUMERIC(25, 0)|Protokollfolgenummer des nächsten Protokolldatensatzes nach dem Sicherungssatz. Kann den Wert NULL haben.|  
|backup_start_date|DATETIME|Datum und Uhrzeit des Beginns des Sicherungsvorgangs.|  
|backup_finish_date|NVARCHAR(128)|Datum und Uhrzeit des Endes des Sicherungsvorgangs.|  
|machine_name|NVARCHAR(128)|Der Name des Computers, auf dem die SQL Server-Instanz installiert ist und auf dem [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ausgeführt wird.|  
|last_recovery_fork_id|UNIQUEIDENTIFIER|Identifikationsnummer für die endende Wiederherstellungs Verzweigung.|  
|first_recovery_fork_id|UNIQUEIDENTIFIER|ID des ersten Wiederherstellungs-Verzweigungspunkts. Bei Datensicherungen ist first_recovery_fork_guid mit last_recovery_fork_guid identisch.|  
|fork_point_lsn|NUMERIC(25, 0)|Wenn first_recovery_fork_id ungleich last_recovery_fork_id ist, entspricht dieser Wert der Protokollfolgenummer des Verzweigungspunkts. Andernfalls ist der Wert NULL.|  
|availability_group_guid|UNIQUEIDENTIFIER|Wenn eine Datenbank eine Always on Datenbank ist, ist dies die GUID der Verfügbarkeits Gruppe. Andernfalls ist dieser Wert NULL.|  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert **Select** -Berechtigungen für diese Funktion.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle verfügbaren Sicherungen aufgelistet, die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank "MyDB" gesichert wurden.  
  
```  
SELECT *   
FROM msdb.managed_backup.fn_available_backups ('MyDB')  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server verwaltete Sicherung auf Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)   
 [Wiederherstellen von in Microsoft Azure gespeicherten Sicherungen](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
