---
title: managed_backup. sp_backup_config_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/20/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_schedule_TSQL
- managed_backup.sp_backup_config_schedule
- managed_backup.sp_backup_config_schedule_TSQL
- sp_backup_config_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_schedule
- sp_backup_config_schedule
ms.assetid: 82541160-d1df-4061-91a5-6868dd85743a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7bb477901dee22c70bb47cd0eaf7da5eb163b7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "77507533"
---
# <a name="managed_backupsp_backup_config_schedule-transact-sql"></a>managed_backup. sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Konfiguriert die automatisierten oder benutzerdefinierten Planungsoptionen [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]für.  
    
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```vb  
EXEC managed_backup.sp_backup_config_schedule   
    [@database_name = ] 'database_name'
    ,[@scheduling_option = ] {'Custom' | 'System'}  
    ,[@full_backup_freq_type = ] {'Daily' | 'Weekly'}  
    ,[@days_of_week = ] 'days_of_the_week'  
    ,[@backup_begin_time = ] 'begin time of the backup window'  
    ,[@backup_duration = ] 'backup window length'  
    ,[@log_backup_freq = ] 'frequency of log backup'  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 @database_name  
 Der Datenbankname für die Aktivierung der verwalteten Sicherung für eine bestimmte Datenbank. Wenn NULL oder * ist, gilt diese verwaltete Sicherung für alle Datenbanken auf dem Server.  
  
 @scheduling_option  
 Geben Sie "System" für die System gesteuerte Sicherungs Planung an. Geben Sie "Custom" für einen benutzerdefinierten Zeitplan an, der von den anderen Parametern definiert wird.  
  
 @full_backup_freq_type  
 Der Häufigkeitstyp für den verwalteten Sicherungs Vorgang, der auf "täglich" oder "wöchentlich" festgelegt werden kann.  
  
 @days_of_week  
 Die Wochentage für die Sicherungen, wenn @full_backup_freq_type auf wöchentlich festgelegt ist. Geben Sie vollständige Zeichen folgen Namen wie "Montag" an.  Sie können auch mehr als einen Tagnamen angeben, der durch eine Pipe getrennt ist. Beispielsweise n ' Montag | Mittwoch | Freitag '.  
  
 @backup_begin_time  
 Die Startzeit des Sicherungs Fensters. Sicherungen werden außerhalb des Zeitfensters, das durch eine Kombination aus @backup_begin_time und @backup_durationdefiniert wird, nicht gestartet.  
  
 @backup_duration  
 Die Dauer des Zeitfensters für die Sicherung. Beachten Sie, dass es keine Garantie gibt, dass Sicherungen während des durch @backup_begin_time und @backup_durationdefinierten Zeitfensters abgeschlossen werden. Sicherungs Vorgänge, die in diesem Zeitfenster gestartet werden, aber die Dauer des Fensters überschreiten, werden nicht abgebrochen.  
  
 @log_backup_freq  
 Dadurch wird die Häufigkeit der Transaktionsprotokoll Sicherungen bestimmt. Diese Sicherungen erfolgen in regelmäßigen Abständen anstelle des Zeitplans, der für die Datenbanksicherungen festgelegt wurde. @log_backup_freqkann innerhalb von Minuten oder Stunden liegen `0:00` und ist gültig und weist auf keine Protokoll Sicherungen hin. Die Deaktivierung von Protokoll Sicherungen ist nur für Datenbanken mit einem einfachen Wiederherstellungs Modell geeignet.  
  
> [!NOTE]  
>  Wenn das Wiederherstellungs Modell von einfach in vollständig geändert wird, müssen Sie die log_backup_freq von `0:00` auf einen Wert ungleich 0 (null) umkonfigurieren.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **db_backupoperator** Daten Bank Rolle mit **ALTER ANY CREDENTIAL** -Berechtigungen und **Execute** -Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [managed_backup. sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
