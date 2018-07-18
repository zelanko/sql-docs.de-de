---
title: sp_backup_config_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8ebeca4b0a1c9079f8786303207bcbae4dfe74c3
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38035278"
---
# <a name="managedbackupspbackupconfigschedule-transact-sql"></a>sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Konfiguriert die Zeitplanoptionen für den automatisierten oder benutzerdefinierte [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
    
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
##  <a name="Arguments"></a> Argumente  
 @database_name  
 Der Name der Datenbank, für die verwaltete Sicherung in einer bestimmten Datenbank aktiviert werden soll. Wenn der Wert NULL oder *, und klicken Sie dann diese verwaltete Sicherung für alle Datenbanken auf dem Server gilt.  
  
 @scheduling_option  
 Geben Sie "System", für die sicherungsplanung System gesteuert. Geben Sie "Benutzerdefiniert" für einen benutzerdefinierten Zeitplan, der von den anderen Paratmeters definiert.  
  
 @full_backup_freq_type  
 Der Typ der Frequenz für die verwaltete Sicherung, die auf "Täglich" oder "Wöchentlich" festgelegt werden können.  
  
 @days_of_week  
 Die Tage der Woche für die Sicherungen bei @full_backup_freq_type ist auf wöchentlich festgelegt. Geben Sie die vollständige Zeichenfolge-Namen, z. B. "Montag".  Sie können auch mehr als einen Tag-Namen, die durch einen senkrechten Strich getrennt angeben. Z. B. N'Monday | Mittwoch | Freitag ".  
  
 @backup_begin_time  
 Die Startzeit des Sicherungsfensters. Sicherungen werden nicht außerhalb des Fensters Zeit, die durch eine Kombination von definiert wird gestartet @backup_begin_time und @backup_duration.  
  
 @backup_duration  
 Die Dauer der Zeitfenster für Sicherungen. Beachten Sie, dass es keine Garantie gibt, dass Sicherungen während des Zeitfensters, definiert durch abgeschlossen werden, @backup_begin_time und @backup_duration. Sicherungsvorgänge, die in diesem Zeitfenster gestartet wurden, aber die Dauer des Fensters überschreiten, werden nicht abgebrochen werden.  
  
 @log_backup_freq  
 Dies bestimmt die Häufigkeit der Sicherungen des Transaktionsprotokolls. Diese Sicherungen erfolgen in regelmäßigen Abständen und nicht auf dem angegebenen Zeitplan für die Datenbank gesichert wird. @log_backup_freq kann in Minuten oder Stunden und 0 ist ungültig. Dies bedeutet, dass keine protokollsicherungen. Deaktivieren von protokollsicherungen wird nur für Datenbanken mit einer einfachen Wiederherstellungsmodell geeignet sein.  
  
> [!NOTE]  
>  Wenn das Wiederherstellungsmodell von simple in full geändert wird, müssen Sie die Log_backup_freq von 0 auf einen Wert ungleich 0 neu konfigurieren.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **Db_backupoperator** -Datenbankrolle mit **ALTER ANY CREDENTIAL** Berechtigungen und **EXECUTE** Berechtigungen für **Sp_delete_ Backuphistory** gespeicherte Prozedur.  
  
## <a name="see-also"></a>Siehe auch  
 [managed_backup. sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
