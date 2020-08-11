---
title: Planen der SIS-Pakete in Azure | Microsoft-Dokumentation
description: Übersicht über die verfügbaren Methoden zum Planen der Ausführung von SSIS-Paketen, die für Azure SQL-Datenbank bereitgestellt sind.
ms.date: 05/29/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: f6aef5ff65ee10c01cecd012eb1f35d5b2aab136
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823775"
---
# <a name="schedule-the-execution-of-sql-server-integration-services-ssis-packages-deployed-in-azure"></a>Planen der Ausführung von in Azure bereitgestellten SSIS-Paketen

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]



Sie können die Ausführung von SSIS-Paketen planen, die im SSISDB-Katalog eines Azure SQL-Datenbank-Servers bereitgestellt sind, indem Sie eine der in diesem Artikel beschriebenen Methoden verwenden. Sie können ein Paket direkt oder indirekt als Teil einer Azure Data Factory-Pipeline planen. Eine Übersicht über SSIS in Azure finden Sie unter [Migration von SQL Server Integration Services-Workloads in die Cloud per Lift und Shift](ssis-azure-lift-shift-ssis-packages-overview.md).

- Direktes Planen eines Pakets

  - [Planen mit der Option „Zeitplan“ in SQL Server Management Studio (SSMS)](#ssms)

  - [SQL-Datenbank für elastische Aufträge](#elastic)

  - [SQL Server-Agent](#agent)

- [Indirektes Planen eines Pakets als Teil einer Azure Data Factory-Pipeline](#activity)


## <a name="schedule-a-package-with-ssms"></a><a name="ssms"></a> Planen eines Pakets mit SSMS

In SQL Server Management Studio (SSMS) können Sie mit der rechten Maustaste auf ein Paket klicken, das in der SSIS-Katalogdatenbank SSISDB bereitgestellt wird, und **Zeitplan** auswählen, um das Dialogfeld **Neuer Zeitplan** zu öffnen. Weitere Informationen finden Sie unter [Planen der Ausführung von SSIS-Paketen in Azure mit SSMS](ssis-azure-schedule-packages-ssms.md).

Dieses Feature erfordert SQL Server Management Studio, Version 17.7 oder höher. Die neueste Version von SSMS können Sie unter [Herunterladen von SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md) abrufen.

## <a name="schedule-a-package-with-sql-database-elastic-jobs"></a><a name="elastic"></a> Planen eines Pakets mit SQL-Datenbank für elastische Aufträge

Weitere Informationen zu elastischen Aufträgen auf SQL-Datenbank finden Sie unter [Verwalten von Scale Out-Clouddatenbanken](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Voraussetzungen

Sie müssen zunächst folgende Schritte ausführen, damit Sie elastische Aufträge verwenden können, um SSIS-Pakete zu planen, die in der SSIS-Katalogdatenbank auf einem Azure SQL-Datenbank-Server gespeichert sind:

1.  Installieren und Konfigurieren Sie die Komponenten für Aufträge für die elastische Datenbank. Informationen dazu finden Sie unter [Installieren von Aufträgen für die elastische Datenbank – Übersicht](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Erstellen Sie datenbankbezogene Anmeldeinformationen, die Aufträge nutzen können, um Befehle an die SSIS-Katalogdatenbank zu senden. Informationen dazu finden Sie unter [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) (Erstellen von datenbankbezogenen Anmeldeinformationen (Transact-SQL))](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Erstellen eines elastischen Auftrags

Sie können den Auftrag erstellen, indem Sie ein Transact-SQL-Skript verwenden, das dem im folgenden Beispiel dargestellten Skript gleicht:

```sql
-- Create Elastic Jobs target groupÂ 
EXECÂ jobs.sp_add_target_group 'TargetGroup'Â 

-- Add Elastic Jobs target group memberÂ 
EXECÂ jobs.sp_add_target_group_memberÂ @target_group_name='TargetGroup',Â 
    @target_type='SqlDatabase',Â @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB'Â 

-- Add a job to schedule SSIS package execution
EXECÂ jobs.sp_add_jobÂ @job_name='ExecutePackageJob',Â @description='Description',Â 
    @schedule_interval_type='Minutes',Â @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXECÂ jobs.sp_add_jobstepÂ @job_name='ExecutePackageJob',Â 
    @command=N'DECLAREÂ @exe_idÂ bigintÂ 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1,Â 
            @execution_id=@exe_idÂ OUTPUT       Â 
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0',Â 
    @credential_name='YourDBScopedCredentials',Â 
    @target_group_name='TargetGroup'Â 

-- Enable the job scheduleÂ 
EXECÂ jobs.sp_update_jobÂ @job_name='ExecutePackageJob',Â @enabled=1,Â 
    @schedule_interval_type='Minutes',Â @schedule_interval_count=60Â 
```

## <a name="schedule-a-package-with-sql-server-agent-on-premises"></a><a name="agent"></a> Lokales Planen eines Pakets mit SQL Server-Agent

Weitere Informationen zu SQL Server-Agent finden Sie unter [SQL Server Agent Jobs for Packages (Aufträge für SQL Server-Agent für Pakete)](../packages/sql-server-agent-jobs-for-packages.md).

### <a name="prerequisite---create-a-linked-server"></a>Voraussetzung: Erstellen Sie einen Verbindungsserver

Bevor Sie SQL Server-Agent lokal zum Planen der Ausführung von auf einem Azure SQL-Datenbank-Server gespeicherten Paket verwenden können, müssen Sie SQL-Datenbank-Server als Verbindungsserver zu Ihrem lokalen SQL Server hinzufügen.

1.  **Einrichten des Verbindungsservers**

    ```sql
    -- Add the SSISDB database on your Azure SQL Database as a linked server to your SQL Server on premises
    EXEC sp_addlinkedserver
        @server='myLinkedServer', -- Name your linked server
        @srvproduct='',     
        @provider='sqlncli', -- Use SQL Server native client
        @datasrc='<server_name>.database.windows.net', -- Add your Azure SQL Database server endpoint
        @location='',
        @provstr='',
        @catalog='SSISDB'  -- Add SSISDB as the initial catalog
    ```

2.  **Einrichten der Anmeldeinformationen für den Verbindungsserver**

    ```sql
    -- Add your Azure SQL Database server admin credentials
    EXEC sp_addlinkedsrvlogin
        @rmtsrvname = 'myLinkedServer',
        @useself = 'false',
        @rmtuser = 'myUsername', -- Add your server admin username
        @rmtpassword = 'myPassword' -- Add your server admin password
    ```

3.  **Einrichten der Verbindungsserveroptionen**

    ```sql
    EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;
    ```

Weitere Informationen finden Sie unter [Erstellen von Verbindungsservern](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) und [Linked Servers (Verbindungsserver)](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Erstellen eines Auftrags für SQL Server-Agent

Erstellen Sie mithilfe eines Auftragsschritts einen Auftrag, der die gespeicherten SSIS-Katalog-Prozeduren `[catalog].[create_execution]` und `[catalog].[start_execution]` aufruft, um ein Paket lokal mit SQL Server-Agent zu planen. Weitere Informationen finden Sie unter [SQL Server Agent Jobs for Packages (Aufträge für SQL Server-Agent für Pakete)](../packages/sql-server-agent-jobs-for-packages.md).

1.  Stellen Sie in SQL Server Management Studio eine Verbindung mit der lokalen SQL Server-Datenbank her, auf der Sie den Auftrag erstellen möchten.

2.  Klicken Sie mit der rechten Maustaste auf den Knoten **SQL Server-Agent**, wählen Sie **Neu** aus, und klicken Sie anschließend auf **Auftrag**, damit das Dialogfeld **Neuer Auftrag** geöffnet wird.

3.  Wählen Sie im Dialogfeld **Neuer Auftrag** die Seite **Schritte** aus, und klicken Sie dann auf **Neu**, um das Dialogfeld **Neuer Auftragsschritt** zu öffnen.

4.  Wählen Sie im Dialogfeld **Neuer Auftragsschritt**`SSISDB` als **Datenbank** aus.

5.  Geben Sie im Feld **Befehl** ein Transact-SQL-Skript ein, das dem im folgenden Beispiel dargestellten Skript gleicht:

    ```sql
    -- T-SQL script to create and start SSIS package execution using SSISDB stored procedures
    DECLARE @return_valueÂ int,Â @exe_idÂ bigintÂ 

    EXEC @return_valueÂ =Â [YourLinkedServer].[SSISDB].[catalog].[create_execution]Â 
        @folder_name=N'folderName',Â @project_name=N'projectName',Â 
        @package_name=N'packageName',Â @use32bitruntime=0,Â @runincluster=1,Â @useanyworker=1,
        @execution_id=@exe_idÂ OUTPUTÂ 

    EXEC [YourLinkedServer].[SSISDB].[catalog].[set_execution_parameter_value] @exe_id,
        @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution]Â @execution_id=@exe_id
    ```

6.  Stellen Sie die Konfiguration und die Planung des Auftrags fertig.

## <a name="schedule-a-package-as-part-of-an-azure-data-factory-pipeline"></a><a name="activity"></a> Planen eines Pakets als Teil einer Azure Data Factory-Pipeline

Sie können ein Paket indirekt planen, indem Sie einen Trigger verwenden, um eine Azure Data Factory-Pipeline auszuführen, die ein SSIS-Paket ausführt.

Verwenden Sie einen der folgenden Trigger, um eine Data Factory-Pipeline zu planen:

- [Zeitplantrigger](https://docs.microsoft.com/azure/data-factory/how-to-create-schedule-trigger)

- [Trigger für rollierende Fenster](https://docs.microsoft.com/azure/data-factory/how-to-create-tumbling-window-trigger)

- [Ereignisbasierter Trigger](https://docs.microsoft.com/azure/data-factory/how-to-create-event-trigger)

Verwenden Sie eine der folgenden Aktivitäten, um ein SSIS-Paket als Teil einer Data Factory-Pipeline auszuführen:

- [Ausführen einer SSIS-Paketaktivität](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity)

- [Aktivität der gespeicherten Prozedur](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity)

## <a name="next-steps"></a>Nächste Schritte

Überprüfen Sie die Optionen für das Ausführen von SSIS-Paketen, die in Azure bereitgestellt wurden. Weitere Informationen finden Sie unter [Ausführen eines SSIS-Pakets in Azure](ssis-azure-run-packages.md).
