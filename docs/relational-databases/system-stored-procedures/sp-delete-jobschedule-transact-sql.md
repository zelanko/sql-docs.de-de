---
title: sp_delete_jobschedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobschedule
- sp_delete_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobschedule
ms.assetid: 82fbb48b-603a-4016-a7fb-1ce17fb76919
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8a74d7235b1faa80c1fe65f80717c39e7944f343
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85864271"
---
# <a name="sp_delete_jobschedule-transact-sql"></a>sp_delete_jobschedule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht einen Zeitplan für einen Auftrag.  
  
 **sp_delete_jobschedule** wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.  
  
  
## <a name="remarks"></a>Hinweise  
 Auftragszeitpläne können jetzt unabhängig von Aufträgen verwaltet werden. Verwenden Sie **sp_detach_schedule**, um einen Zeitplan von einem Auftrag zu entfernen. Verwenden Sie **sp_delete_schedule**, um einen Zeitplan zu löschen.  
  
> **Hinweis: sp_delete_jobschedule** unterstützt keine Zeitpläne, die an mehrere Aufträge angefügt sind. Wenn ein vorhandenes Skript **sp_delete_jobschedule** aufruft, um einen Zeitplan zu entfernen, der an mehrere Aufträge angefügt ist, gibt die Prozedur einen Fehler zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder der **sysadmin** -Rolle können jeden Auftragszeitplan löschen. Benutzer, die nicht Mitglied der **sysadmin** -Rolle sind, können nur Aufträge löschen, deren Besitzer sie sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_delete_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)   
 [Anzeigen oder Ändern von Aufträgen](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_help_jobschedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql.md)   
 [sp_update_jobschedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-jobschedule-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
