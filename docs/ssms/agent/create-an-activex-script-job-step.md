---
title: Erstellen eines ActiveX-Skript-Auftragsschritts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a6ac4c4174b814577340b2d571c2f9b76944482a
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696988"
---
# <a name="create-an-activex-script-job-step"></a>Create an ActiveX Script Job Step
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird beschrieben, wie Sie einen Auftragsschritt des [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, der ein ActiveX-Skript in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder SQL Server Management Objects ausführt, erstellen und definieren können.  
  
-   **Vorbereitungen:**  
  
    [Einschränkungen](#Restrictions)  
  
    [Security](#Security)  
  
-   **So erstellen Sie einen Transact-SQL-Auftragsschritt mit**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="Restrictions"></a>Einschränkungen  
[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
### <a name="Security"></a>Sicherheit  
Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-an-activex-script-job-step"></a>So erstellen Sie einen ActiveX-Skript-Auftragsschritt  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erstellen Sie einen neuen Auftrag, oder klicken Sie mit der rechten Maustaste auf einen vorhandenen Auftrag, und klicken Sie dann auf **Eigenschaften**. Weitere Informationen zum Erstellen eines Auftrags finden Sie unter [Erstellen von Aufträgen](../../ssms/agent/create-jobs.md).  
  
3.  Klicken Sie im Dialogfeld **Auftragseigenschaften** auf die Seite **Schritte** und dann auf **Neu**.  
  
4.  Geben Sie im Dialogfeld **Neuer Auftragsschritt** unter **Schrittname**einen Schrittnamen für den Auftrag ein.  
  
5.  Klicken Sie in der Liste **Typ** auf **ActiveX-Skript**.  
  
6.  Wählen Sie in der Liste **Ausführen als** das Proxykonto mit den Anmeldeinformationen für den Auftrag aus.  
  
7.  Wählen Sie die **Sprache** aus, in der das Skript geschrieben wurde. Klicken Sie alternativ auf **Andere** , und geben Sie dann den Namen der [!INCLUDE[msCoName](../../includes/msconame_md.md)] ActiveX-Skriptsprache ein, in der das Skript geschrieben wird.  
  
8.  Geben Sie im Feld **Befehl** die Skriptsyntax ein, die für den Auftragsschritt ausgeführt wird. Klicken Sie alternativ auf **Öffnen** , und wählen Sie eine Datei aus, die die Skriptsyntax enthält.  
  
9. Klicken Sie auf die Seite **Erweitert** , um die folgenden Optionen für den Auftragsschritt festzulegen: welche Aktion bei der erfolgreichen oder fehlerhaften Ausführung des Auftragsschrittes jeweils auszuführen ist, wie oft der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent versuchen soll, den Auftragsschritt auszuführen, und wie viele Wiederholungsversuche unternommen werden sollen.  
  
## <a name="TSQL"></a>Verwenden von Transact-SQL  
  
#### <a name="to-create-an-activex-script-job-step"></a>So erstellen Sie einen ActiveX-Skript-Auftragsschritt  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde_md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- create an ActiveX Script job step written in VBScript that creates a restore point  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a restore point',  
        @subsystem = N'ACTIVESCRIPTING',  
        @command = N'Const RESTORE_POINT = 20  
  
    strComputer = "."  
    Set objWMIService = GetObject("winmgmts:" _  
        & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\default")  
  
    Set objItem = objWMIService.Get("SystemRestore")  
    errResults = objItem.Restore(RESTORE_POINT)',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
Weitere Informationen finden Sie unter [sp_add_jobstep (Transact-SQL)](https://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Verwendung von SQL Server Management Objects  
**So erstellen Sie einen ActiveX-Skript-Auftragsschritt**  
  
Verwenden Sie die **JobStep** -Klasse indem Sie eine von Ihnen ausgewählte Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell verwenden.  
  
