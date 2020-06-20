---
title: Erstellen eines Zeitplans | Microsoft-Dokumentation
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
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac71a61163dceb06697b61ef24fce2117d57cf2f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064540"
---
# <a name="create-a-schedule"></a>Create a Schedule
  Sie können einen Zeitplan für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder SQL Server Management Objects erstellen.  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So erstellen Sie einen Zeitplan mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-schedule"></a>So erstellen Sie einen Zeitplan  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz her, und erweitern Sie dann die Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, klicken Sie mit der rechten Maustaste auf **Aufträge**, und wählen Sie dann **Zeitpläne verwalten**.  
  
3.  Klicken Sie im Dialogfeld **Zeitpläne verwalten** auf **Neu**.  
  
4.  Geben Sie in das Feld **Name** einen Namen für den neuen Zeitplan ein.  
  
5.  Wenn der Zeitplan nicht unmittelbar nach seiner Erstellung wirksam werden soll, deaktivieren Sie das Kontrollkästchen **Aktiviert** .  
  
6.  Wählen Sie für **Zeitplantyp**eine der folgenden Möglichkeiten aus:  
  
    -   Um den Auftrag zu starten, wenn die CPUs eine Leerlaufbedingung erfüllen, klicken Sie auf **Starten, wenn sich die CPUs im Leerlauf befinden**.  
  
    -   Klicken Sie auf **Wiederholt**, wenn ein Zeitplan wiederholt ausgeführt werden soll. Um den wiederholten Zeitplan festzulegen, vervollständigen Sie im Dialogfeld die Gruppen **Häufigkeit**, **Häufigkeit pro Tag**und **Dauer** .  
  
    -   Wenn der Zeitplan nur einmal ausgeführt werden soll, klicken Sie auf **Einmal**. Um den **einmaligen** Zeitplan festzulegen, vervollständigen Sie im Dialogfeld die Gruppe **Einmalig** .  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-schedule"></a>So erstellen Sie einen Zeitplan  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```sql
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_add_schedule &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql).  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwenden von SQL Server Management Objects  
 **So erstellen Sie einen Zeitplan**  
  
 Verwenden Sie die `JobSchedule`-Klasse in einer von Ihnen ausgewählten Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
