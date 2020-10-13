---
description: Create an ActiveX Script Job Step
title: Create an ActiveX Script Job Step
ms.custom: seo-lt-2019
ms.date: 10/06/2020
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: <= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8bac45061aa165808202b2a08b71618bd6513954
ms.sourcegitcommit: 610e3ebe21ac6575850a29641a32f275e71557e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91784991"
---
# <a name="create-an-activex-script-job-step"></a>Erstellen eines ActiveX-Skriptauftragsschritts

[!INCLUDE [sqlserver](../../includes/applies-to-version/sqlserver.md)]

Das ActiveX-Subsystem wird ab SQL Server 2016 nicht mehr unterstützt. Konvertieren Sie alle vorhandenen Auftragsschritte, die ActiveX-Skripts verwenden, in [PowerShell-Skriptauftragsschritte](create-a-powershell-script-job-step.md). Verwenden Sie in Zukunft PowerShell für die Entwicklung.

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details hierzu finden Sie unter [Unterschiede bei T-SQL zwischen SQL Server und Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Artikel wird beschrieben, wie Sie einen Auftragsschritt für den [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent in SQL Server 2014 und früher erstellen und definieren, der ein ActiveX-Skript mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects ausführt.  

## <a name="before-you-begin"></a>Vorbereitung  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Einschränkungen  

[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  

  
### <a name="security"></a><a name="Security"></a>Sicherheit  

Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="use-sql-server-management-studio"></a><a name="SSMS"></a>Verwenden von SQL Server Management Studio  
  
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
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Verwenden von Transact-SQL  
  
#### <a name="to-create-an-activex-script-job-step"></a>So erstellen Sie einen ActiveX-Skriptauftragsschritt  
  
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
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Verwendung von SQL Server Management Objects  
**So erstellen Sie einen ActiveX-Skript-Auftragsschritt**  
  
Verwenden Sie die **JobStep** -Klasse indem Sie eine von Ihnen ausgewählte Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell verwenden.  
  
