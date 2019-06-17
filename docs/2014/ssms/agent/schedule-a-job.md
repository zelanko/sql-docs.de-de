---
title: Planen eines Auftrags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abb84377c48778d0c7244c13620fe192b5421ad6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666762"
---
# <a name="schedule-a-job"></a>Schedule a Job
  In diesem Thema wird beschrieben, wie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag geplant wird.  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So planen Sie einen Auftrag mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a>So erstellen Sie einen Zeitplan und weisen ihn einem Auftrag zu  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den zu planenden Auftrag, und klicken Sie auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Zeitpläne** aus, und klicken Sie dann auf **Neu**.  
  
4.  Geben Sie in das Feld **Name** einen Namen für den neuen Zeitplan ein.  
  
5.  Deaktivieren Sie das Kontrollkästchen **Aktiviert** , wenn der Zeitplan nicht unmittelbar nach seiner Erstellung wirksam werden soll.  
  
6.  Wählen Sie für **Zeitplantyp**eine der folgenden Möglichkeiten aus:  
  
    -   Klicken Sie auf **Automatisch starten, wenn der SQL Server-Agent startet** , um den Auftrag zu starten, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst gestartet wird.  
  
    -   Klicken Sie auf **Starten, wenn sich die CPUs im Leerlauf befinden** , um den Auftrag zu starten, wenn die CPUs eine Leerlaufbedingung erfüllen.  
  
    -   Klicken Sie auf **Wiederholt** , wenn ein Zeitplan wiederholt ausgeführt werden soll. Um den wiederholten Zeitplan festzulegen, vervollständigen Sie im Dialogfeld die Gruppen **Häufigkeit**, **Häufigkeit pro Tag**und **Dauer** .  
  
    -   Klicken Sie auf **Einmal** , wenn der Zeitplan nur einmal ausgeführt werden soll. Um den **Einmal** -Zeitplan festzulegen, vervollständigen Sie im Dialogfeld die Gruppe **Einmalig** .  
  
#### <a name="to-attach-a-schedule-to-a-job"></a>So weisen Sie einen Zeitplan einem Auftrag zu  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den zu planenden Auftrag, und klicken Sie auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Zeitpläne** aus, und klicken Sie dann auf **Auswählen**.  
  
4.  Wählen Sie den Zeitplan aus, den Sie zuweisen möchten, und klicken Sie auf **OK**.  
  
5.  Doppelklicken Sie im Dialogfeld **Auftragseigenschaften** auf den zugewiesenen Zeitplan.  
  
6.  Überprüfen Sie, ob das **Startdatum** ordnungsgemäß festgelegt ist. Falls nicht, legen Sie das Datum fest, an dem der Zeitplan starten soll, und klicken Sie auf **OK**.  
  
7.  Klicken Sie im Dialogfeld **Auftragseigenschaften** auf **OK**.  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-schedule-a-job"></a>So planen Sie einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [Sp_add_schedule &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) und [Sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql).  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 Verwenden Sie die `JobSchedule`-Klasse in einer von Ihnen ausgewählten Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
