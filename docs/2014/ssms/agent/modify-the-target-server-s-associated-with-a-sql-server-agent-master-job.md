---
title: Ändern der Ziel Server, die einem SQL Server-Agent Master Auftrag zugeordnet sind | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 176e73b6-08aa-48ec-b349-e84b431e65cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b7b5ab114366cdafe40b7a70f523fef43eb11d8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048774"
---
# <a name="modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a>Ändern der einem Masterauftrag für den SQL Server-Agent zugewiesenen Zielserver
  In diesem Thema wird beschrieben, wie Sie die Zielserver, die einem Masterauftrag für den SQL Server-Agent zugewiesen sind, mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **Ändern der Zielserver, die einem Masterauftrag für den SQL Server-Agent zugewiesen sind, mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Ein Masterauftrag für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent kann nicht gleichzeitig lokale Server und Remoteserver als Ziel haben.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie können nur Aufträge ändern, die in Ihrem Besitz sind, es sei denn, Sie sind ein Mitglied der festen Serverrolle **sysadmin** . Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a>So ändern Sie die Zielserver, die einem Masterauftrag für den SQL Server-Agent zugewiesen sind  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, der den Auftrag mit dem zu ändernden Zielserver enthält.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um den Ordner **Aufträge** zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Auftrag, dessen Zielserver Sie ändern möchten, und wählen Sie **Eigenschaften**aus.  
  
5.  Wählen Sie im Dialogfeld **Auftrags Eigenschaften-**_job_name_ unter **Seite auswählen**die Option **Ziele**aus. Weitere Informationen zu den verfügbaren Optionen auf dieser Seite finden Sie unter [Auftrags Eigenschaften: Seite "neue Aufträge &#40;Ziele"&#41;](job-properties-new-job-targets-page.md).  
  
6.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-target-server-currently-associated-with-a-sql-server-agent-master-job"></a>So löschen Sie einen Zielserver, der derzeit einem Masterauftrag für den SQL Server-Agent zugewiesen ist  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- removes the server SEATTLE2 from processing the Weekly Sales Backupsjob   
    -- assumes that the Weekly Sales Backups job exists  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_delete_jobserver &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql).  
  
#### <a name="to-associate-a-target-server-with-the-current-sql-server-agent-master-job"></a>So weisen Sie dem aktuellen Masterauftrag für den SQL Server-Agent einen Zielserver zu  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2   
    -- assumes that the Weekly Sales Backups job already exists and that   
    -- SEATTLE2 is registered as a target server for the current instance  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_add_jobserver &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).  
  
  
