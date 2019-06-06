---
title: Erstellen und Ausführen von Aufträgen für SQL Server unter Linux | Microsoft-Dokumentation
description: In diesem Tutorial veranschaulicht, wie SQL Server-Agent-Auftrag unter Linux ausgeführt wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.openlocfilehash: d7df0ed46d9ded592a8cebc6571c5ec1e1b1f486
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705119"
---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Erstellen und Ausführen von SQL Server-Agent-Aufträgen unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server-Aufträge werden verwendet, um regelmäßig die gleiche Sequenz von Befehlen in der SQL Server-Datenbank ausführen. Dieses Tutorial enthält ein Beispiel zum Erstellen eines SQL Server-Agent-Auftrags unter Linux mithilfe von Transact-SQL und SQL Server Management Studio (SSMS).

> [!div class="checklist"]
> * Installieren von SQL Server-Agent unter Linux
> * Erstellen eines neuen Auftrags zum Ausführen von täglichen datenbanksicherungen
> * Planen und Ausführen des Auftrags
> * Führen Sie die gleichen Schritte aus, in SSMS (optional)

Bekannte Probleme mit SQL Server-Agent für Linux finden Sie unter den [– Anmerkungen zu dieser](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Die folgenden Voraussetzungen sind erforderlich, um dieses Lernprogramm abzuschließen:

* Linux-Computer mit den folgenden Voraussetzungen:
  * SQL Server ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), oder [Ubuntu](quickstart-install-connect-ubuntu.md)) mit Befehlszeilentools.

Die folgenden Voraussetzungen sind optional:

* Windows-Computer mit SSMS:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) für optionale Schritte von SSMS.

## <a name="enable-sql-server-agent"></a>SQL Server-Agent aktivieren

Um SQL Server-Agent für Linux zu verwenden, müssen Sie zuerst SQL Server-Agent auf einem Computer aktivieren, die bereits SQL Server installiert ist.

1. Um SQL Server-Agent zu aktivieren, führen Sie in den folgenden Schritt aus.
  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  ```

1. Starten Sie SQL Server mit dem folgenden Befehl neu:
  ```bash
  sudo systemctl restart mssql-server
  ```

> [!NOTE]
> Ab SQL Server 2017 CU4, SQL Server-Agent ist im Lieferumfang der **Mssql-Server** Packen und ist standardmäßig deaktiviert. Für Agent vor dem CU4 finden Sie unter eingerichtet [Installieren von SQL Server-Agent für Linux](sql-server-linux-setup-sql-agent.md).

## <a name="create-a-sample-database"></a>Erstellen einer Beispieldatenbank

Verwenden Sie die folgenden Schritte aus, um das Erstellen einer Beispieldatenbank mit dem Namen **SampleDB**. Diese Datenbank wird für den täglichen Sicherungsauftrag verwendet.

1. Öffnen Sie auf Ihren Linux-Computer eine Bash-terminal-Sitzung ein.

1. Verwendung **Sqlcmd** zum Ausführen einer Transact-SQL **CREATE DATABASE** Befehl.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'CREATE DATABASE SampleDB'
   ```

1. Stellen Sie sicher, dass die Datenbank erstellt wird, indem Sie die Datenbanken auf dem Server auflisten.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'SELECT Name FROM sys.Databases'
   ```

## <a name="create-a-job-with-transact-sql"></a>Erstellen eines Auftrags mit Transact-SQL

Die folgenden Schritte erstellen ein SQL Server-Agent-Auftrags unter Linux mit Transact-SQL-Befehlen. Der Auftrag ausgeführt wird, eine tägliche Sicherung der-Beispieldatenbank, **SampleDB**.

> [!TIP]
> Sie können alle T-SQL-Client verwenden, die Befehle ausführen. Zum Beispiel unter Linux können Sie [Sqlcmd](sql-server-linux-setup-tools.md) oder [Visual Studio Code](sql-server-linux-develop-use-vscode.md). Sie können von einem Remotecomputer Windows Server auch Abfragen in SQL Server Management Studio (SSMS) ausführen oder verwenden die Benutzeroberfläche für die auftragsverwaltung, die im nächsten Abschnitt beschrieben wird.

1. Verwendung [Sp_add_job](../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md) zum Erstellen eines Auftrags mit dem Namen `Daily SampleDB Backup`.

   ```sql
   -- Adds a new job executed by the SQLServerAgent service
   -- called 'Daily SampleDB Backup'
   USE msdb ;
   GO
   EXEC dbo.sp_add_job
      @job_name = N'Daily SampleDB Backup' ;
   GO
   ```

1. Rufen Sie [Sp_add_jobstep](../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md) Sie einen Auftragsschritt zu erstellen, eine Sicherung erstellt, die `SampleDB` Datenbank.

   ```sql
   -- Adds a step (operation) to the job
   EXEC sp_add_jobstep
      @job_name = N'Daily SampleDB Backup',
      @step_name = N'Backup database',
      @subsystem = N'TSQL',
      @command = N'BACKUP DATABASE SampleDB TO DISK = \
         N''/var/opt/mssql/data/SampleDB.bak'' WITH NOFORMAT, NOINIT, \
         NAME = ''SampleDB-full'', SKIP, NOREWIND, NOUNLOAD, STATS = 10',
      @retry_attempts = 5,
      @retry_interval = 5 ;
   GO
   ```

1. Erstellen Sie dann einen täglichen Zeitplan für den Auftrag mit [Sp_add_schedule](../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md).

   ```sql
   -- Creates a schedule called 'Daily'
   EXEC dbo.sp_add_schedule
      @schedule_name = N'Daily SampleDB',
      @freq_type = 4,
      @freq_interval = 1,
      @active_start_time = 233000 ;
   USE msdb ;
   GO
   ```

1. Fügen Sie den Zeitplan für Aufträge an den Auftrag mit [Sp_attach_schedule](../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md).

   ```sql
   -- Sets the 'Daily' schedule to the 'Daily SampleDB Backup' Job
   EXEC sp_attach_schedule
      @job_name = N'Daily SampleDB Backup',
      @schedule_name = N'Daily SampleDB';
   GO
   ```

1. Verwendung [Sp_add_jobserver](../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md) ein Zielserver den Auftrag zuweisen. In diesem Beispiel ist das Ziel des lokalen Servers.

   ```sql
   EXEC dbo.sp_add_jobserver
      @job_name = N'Daily SampleDB Backup',
      @server_name = N'(LOCAL)';
   GO
   ```
1. Starten Sie den Auftrag mit [Sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).

   ```sql
   EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
   GO
   ```

## <a name="create-a-job-with-ssms"></a>Erstellen eines Auftrags mit SSMS

Sie können auch erstellen und Verwalten von Aufträgen mithilfe von SQL Server Management Studio (SSMS) für Windows.

1. Starten Sie SSMS auf Windows, und eine Verbindung mit Ihrem virtuellen SQL Server-Instanz. Weitere Informationen finden Sie unter [Verwalten von SQL Server unter Linux mit SSMS](sql-server-linux-manage-ssms.md).

1. Stellen Sie sicher, dass Sie eine Beispieldatenbank mit dem Namen erstellt haben **SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

1. Stellen Sie sicher, dass die SQL-Agent wurde [installiert](sql-server-linux-setup-sql-agent.md) und ordnungsgemäß konfiguriert sind. Suchen Sie das Pluszeichen neben SQL Server-Agent im Objekt-Explorer. Wenn SQL Server-Agent nicht aktiviert ist, starten Sie den **Mssql-Server** Service unter Linux.

   ![Stellen Sie sicher, dass SQL Server-Agent installiert wurde](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)

1. Erstellen Sie einen neuen Auftrag.

   ![Erstellen eines neuen Auftrags](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)

1. Benennen Sie dem Auftrag, und erstellen Sie Ihre Auftragsschritt.

   ![Erstellen eines Auftragsschritts](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)

1. Geben Sie welchem Subsystem, das Sie verwenden möchten und welche Aktion der Auftragsschritt ausführen soll.

   ![Auftrags-subsystem](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

   ![Auftrags-Aktion](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

1. Erstellen Sie einen neuen Auftragszeitplan.

   ![Auftragszeitplan](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)

   ![Auftragszeitplan](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

1. Starten des Auftrags an.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:

> [!div class="checklist"]
> * Installieren von SQL Server-Agent unter Linux
> * Verwenden Sie Transact-SQL und gespeicherte Systemprozeduren, um Aufträge zu erstellen.
> * Erstellen Sie einen Auftrag, der täglichen Sicherungen der Datenbank ausführt.
> * Verwenden von SSMS UI erstellen und Verwalten von Aufträgen

Als Nächstes untersuchen Sie andere Funktionen für das Erstellen und Verwalten von Aufträgen:

> [!div class="nextstepaction"]
>[SQL Server-Agent-Dokumentation](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)
