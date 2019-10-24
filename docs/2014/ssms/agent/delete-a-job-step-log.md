---
title: Löschen ein Auftragsschrittprotokolls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cd6cefd41ea223b91445042ff3cee9090074feeb
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783186"
---
# <a name="delete-a-job-step-log"></a>Löschen eines Auftragsschrittprotokolls
  In diesem Thema wird beschrieben, wie Sie ein Auftragsschrittprotokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents löschen.  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So löschen Sie ein Auftragsschrittprotokoll des SQL Server-Agents mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Wenn Auftragsschritte gelöscht werden, werden auch die entsprechenden Ausgabeprotokolle gelöscht.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie können nur Aufträge ändern, die in Ihrem Besitz sind, es sei denn, Sie sind ein Mitglied der festen Serverrolle **sysadmin** .  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>So löschen Sie ein Auftragsschrittprotokoll des SQL Server-Agents  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie ändern möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Löschen Sie im Dialogfeld **Auftragseigenschaften** den ausgewählten Auftragsschritt.  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>So löschen Sie ein Auftragsschrittprotokoll des SQL Server-Agents  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```sql
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).  
  
##  <a name="SMO"></a>Verwenden von SQL Server Management Objects  
 Verwenden Sie die `DeleteJobStepLogs`-Methoden der `Job`-Klasse in einer Programmiersprache Ihrer Wahl, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
```powershell
# Delete all job step log files that have ID values larger than 5.  
$srv = New-Object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```
