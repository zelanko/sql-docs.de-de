---
description: sp_delete_jobsteplog (Transact-SQL)
title: sp_delete_jobsteplog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobsteplog
- sp_delete_jobsteplog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobsteplog
ms.assetid: e9ef4c99-abde-4038-b6a3-a25dcbaf0958
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0c656c5ff3a4a1c0798c881cd026fc7153acfae1
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89528227"
---
# <a name="sp_delete_jobsteplog-transact-sql"></a>sp_delete_jobsteplog (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftragsschrittprotokolle, die mit den Argumenten angegeben sind. Verwenden Sie diese gespeicherte Prozedur, um die **sysjobstepslogs** -Tabelle in der **msdb** -Datenbank beizubehalten.  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
       [ , [ @step_id = ] step_id | [ @step_name = ] 'step_name' ]  
       [ , [ @older_than = ] 'date' ]  
       [ , [ @larger_than = ] 'size_in_bytes' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] 'job_id'` Die ID des Auftrags, der das zu entfernende Auftrags Schritt Protokoll enthält. *job_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> **Hinweis:** Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @step_id = ] step_id` Die ID des Schritts im Auftrag, für den das Auftrags Schritt Protokoll gelöscht werden soll. Wenn Sie nicht eingeschlossen werden, werden alle Auftrags Schritt Protokolle im Auftrag gelöscht, es sei denn, ** \@ older_than** oder ** \@ larger_than** wurden angegeben. *step_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @step_name = ] 'step_name'` Der Name des Schritts im Auftrag, für den das Auftrags Schritt Protokoll gelöscht werden soll. *step_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> **Hinweis:** Es können entweder *step_id* oder *step_name* angegeben werden, beide können jedoch nicht angegeben werden.  
  
`[ @older_than = ] 'date'` Das Datum und die Uhrzeit des ältesten Auftrags Schritt Protokolls, das Sie aufbewahren möchten. Alle Auftragsschrittprotokolle vor diesem Datum und dieser Uhrzeit werden entfernt. *Date* ist vom **Datentyp DateTime**und hat den Standardwert NULL. Sowohl ** \@ older_than** als auch ** \@ larger_than** können angegeben werden.  
  
`[ @larger_than = ] 'size_in_bytes'` Die Größe des größten Auftrags Schritt Protokolls in Bytes, das Sie aufbewahren möchten. Alle Auftragsschrittprotokolle, die diese Größe überschreiten, werden entfernt. Sowohl ** \@ larger_than** als auch ** \@ older_than** können angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_delete_jobsteplog** in der **msdb** -Datenbank.  
  
 Wenn keine Argumente außer ** \@ job_id** oder ** \@ job_name** angegeben werden, werden alle Auftrags Schritt Protokolle für den angegebenen Auftrag gelöscht.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder von **sysadmin** können ein Auftrags Schritt Protokoll löschen, das im Besitz eines anderen Benutzers ist.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-removing-all-job-step-logs-from-a-job"></a>A. Entfernen aller Auftragsschrittprotokolle aus einem Auftrag  
 Im folgenden Beispiel werden alle Auftragsschrittprotokolle für den `Weekly Sales Data Backup`-Auftrag entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup';  
GO  
```  
  
### <a name="b-removing-the-job-step-log-for-a-particular-job-step"></a>B. Entfernen des Auftragsschrittprotokolls für einen bestimmten Auftragsschritt  
 Im folgenden Beispiel wird das Auftragsschrittprotokoll für Schritt 2 im `Weekly Sales Data Backup`-Auftrag entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 2;  
GO  
```  
  
### <a name="c-removing-all-job-step-logs-based-on-age-and-size"></a>C. Entfernen aller Auftragsschrittprotokolle auf Grundlage von Alter und Größe  
 Im folgenden Beispiel werden alle Auftragsschrittprotokolle aus dem `Weekly Sales Data Backup`-Auftrag entfernt, die älter sind als 12 Uhr mittags, 25. Oktober 2005, und die größer sind als 100 MB (Megabyte).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @older_than = '10/25/2005 12:00:00',  
    @larger_than = 104857600;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_help_jobsteplog &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
