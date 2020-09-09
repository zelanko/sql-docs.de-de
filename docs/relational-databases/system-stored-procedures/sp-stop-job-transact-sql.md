---
description: sp_stop_job (Transact-SQL)
title: sp_stop_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_stop_job_TSQL
- sp_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stop_job
ms.assetid: 64b4cc75-99a0-421e-b418-94e37595bbb0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c9f44d705f9aff418312a9f8d0f1a9a9f8012216
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551203"
---
# <a name="sp_stop_job-transact-sql"></a>sp_stop_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Weist den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent an, die Ausführung des Auftrags zu beenden.  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_stop_job   
      [@job_name =] 'job_name'  
    | [@job_id =] job_id   
    | [@originating_server =] 'master_server'  
    | [@server_name =] 'target_server'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_name = ] 'job_name'` Der Name des Auftrags, der beendet werden soll. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @job_id = ] job_id` Die ID des Auftrags, der beendet werden soll. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @originating_server = ] 'master_server'` Der Name des Master Servers. Wenn angegeben, werden alle Multiserveraufträge beendet. *master_server* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Geben Sie diesen Parameter nur an, wenn Sie **sp_stop_job** auf einem Zielserver aufrufen.  
  
> [!NOTE]  
>  Es kann jeweils nur einer der ersten drei Parameter angegeben werden.  
  
`[ @server_name = ] 'target_server'` Der Name des bestimmten Zielservers, auf dem ein Multiserverauftrag beendet werden soll. *target_server* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Geben Sie diesen Parameter nur an, wenn Sie **sp_stop_job** auf einem Master Server für einen Multiserverauftrag aufrufen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_stop_job** sendet ein Stoppsignal an die Datenbank. Einige Prozesse können sofort beendet werden, und einige müssen einen stabilen Punkt (oder einen Einstiegspunkt zum Codepfad) erreichen, bevor Sie beendet werden können. Bei einigen zeitaufwändigen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen, etwa BACKUP, RESTORE oder einigen DBCC-Befehlen, kann es längere Zeit dauern, bis sie abgeschlossen sind. Wenn diese ausgeführt werden, kann es einige Zeit dauern, bis der Auftrag abgebrochen wird. Der Abbruch eines Auftrags führt dazu, dass ein entsprechender Eintrag im Auftragsverlauf aufgezeichnet wird.  
  
 Wenn ein Auftrag aktuell einen Schritt des Typs **CmdExec** oder **PowerShell**ausführt, wird der ausgeführte Prozess (z. b. MyProgram.exe) vorzeitig beendet. Ein vorzeitiger Abbruch kann unvorhersehbare Folgen haben, z. B. dass Dateien, die von dem Prozess verwendet wurden, geöffnet bleiben. Folglich sollten **sp_stop_job** nur in extremen Fällen verwendet werden, wenn der Auftrag Schritte des Typs **CmdExec** oder **PowerShell**enthält.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** und **SQLAgentReaderRole** können nur Aufträge unterbinden, deren Besitzer Sie sind. Mitglieder von **SQLAgentOperatorRole** können alle lokalen Aufträge, einschließlich derjenigen, die sich im Besitz anderer Benutzer befinden, Abbrechen. Mitglieder von **sysadmin** können alle lokalen und Multiserveraufträge abbrechen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Auftrag `Weekly Sales Data Backup` beendet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_stop_job  
    N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_delete_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
