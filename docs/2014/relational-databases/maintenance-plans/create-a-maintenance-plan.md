---
title: Erstellen eines Wartungsplans | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- maintenance plans [SQL Server], creating
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3df0c1cd06427deb051a9c4214d03084b44c6f9b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85024683"
---
# <a name="create-a-maintenance-plan"></a>Erstellen eines Wartungsplans
  In diesem Thema wird beschrieben, wie Sie einen Einzelserver- oder Multiserverwartungsplan in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellen. Bei Verwendung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]stehen Ihnen zwei Methoden zum Erstellen der Wartungspläne zur Verfügung: der Wartungsplanungs-Assistent und die Entwurfsoberfläche. Der Assistent eignet sich am besten für das Erstellen von grundlegenden Wartungsplänen; wenn Sie die Entwurfsoberfläche zum Erstellen eines Plans verwenden, können Sie erweiterten Workflow nutzen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **Erstellen eines Wartungsplans mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Wenn Sie einen Multiserver-Wartungsplan erstellen möchten, muss eine Multiserverumgebung mit einem Masterserver und mindestens einem Zielserver konfiguriert sein. Multiserver-Wartungspläne müssen auf dem Masterserver erstellt und verwaltet werden. Diese Pläne können auf Zielservern zwar angezeigt, jedoch nicht verwaltet werden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen ein Mitglied der festen Server Rolle **sysadmin** sein, um Wartungspläne erstellen oder verwalten zu können.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-maintenance-plan-using-the-maintenance-plan-wizard"></a>So erstellen Sie einen Wartungsplan mithilfe des Wartungsplanungs-Assistenten  
  
1.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um den Server zu erweitern, auf dem Sie einen Wartungsplan erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Wartungspläne** , und wählen Sie **Wartungsplanungs-Assistent**aus.  
  
4.  Führen Sie die Schritte des Assistenten aus, um einen Wartungsplan zu erstellen. Weitere Informationen finden Sie unter [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md).  
  
#### <a name="to-create-a-maintenance-plan-using-the-design-surface"></a>So erstellen Sie mithilfe der Entwurfsoberfläche einen Wartungsplan  
  
1.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um den Server zu erweitern, auf dem Sie einen Wartungsplan erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Wartungspläne** , und wählen Sie **Neuer Wartungsplan**aus.  
  
4.  Erstellen Sie einen Wartungsplan anhand der Schritte unter [Erstellen eines Wartungsplans &#40;Entwurfsoberfläche für Wartungspläne&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-maintenance-plan"></a>So erstellen Sie einen Wartungsplan  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE msdb;  
    GO  
    --  Adds a new job, executed by the SQL Server Agent service, called "HistoryCleanupTask_1".  
    EXEC dbo.sp_add_job  
       @job_name = N'HistoryCleanupTask_1',   
       @enabled = 1,   
       @description = N'Clean up old task history' ;   
    GO  
    -- Adds a job step for reorganizing all of the indexes in the HumanResources.Employee table to the HistoryCleanupTask_1 job.   
    EXEC dbo.sp_add_jobstep  
        @job_name = N'HistoryCleanupTask_1',   
        @step_name = N'Reorganize all indexes on HumanResources.Employee table',   
        @subsystem = N'TSQL',   
        @command = N'USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_LoginID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_rowguid ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX PK_Employee_BusinessEntityID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    ',   
        @retry_attempts = 5,   
        @retry_interval = 5 ;   
    GO  
    -- Creates a schedule named RunOnce that executes every day when the time on the server is 23:00.   
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',   
        @freq_type = 4,   
        @freq_interval = 1,   
        @active_start_time = 233000 ;   
    GO  
    -- Attaches the RunOnce schedule to the job HistoryCleanupTask_1.   
    EXEC sp_attach_schedule  
       @job_name = N'HistoryCleanupTask_1'  
       @schedule_name = N'RunOnce' ;   
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter  
  
-   [sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
  
