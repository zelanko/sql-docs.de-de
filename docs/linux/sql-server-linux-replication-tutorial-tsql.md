---
title: Konfigurieren von SQL Server-Replikation unter Linux | Microsoft-Dokumentation
description: Dieses Tutorial veranschaulicht das Konfigurieren von SQL Server-Snapshotreplikation unter Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 13359f151ef1453a7bc8b2020dc4cd8db9a13b80
ms.sourcegitcommit: 97463ffe99915f3bbdf298e6e6b8d170e738ea7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "49390832"
---
# <a name="configure-replication-with-t-sql"></a>Konfigurieren der Replikation mit T-SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)] 

In diesem Tutorial konfigurieren Sie SQL Server-Snapshotreplikation unter Linux mit zwei Instanzen von SQL Server mithilfe von Transact-SQL. Dem Verleger und Verteiler dieselbe Instanz sein werden, und der Abonnenten werden auf einer separaten Instanz.

> [!div class="checklist"]
> * Aktivieren von SQL Server-Replikations-Agents für Linux
> * Erstellen einer Beispieldatenbank
> * Der momentaufnahmeordner für SQL Server-Agents-Zugriff konfigurieren
> * Konfigurieren des Verteilers
> * Konfigurieren des Verlegers
> * Konfigurieren von Veröffentlichung und Artikeln
> * Konfigurieren von Abonnenten 
> * Führen Sie die Replikationsaufträge

Alle Konfigurationen können konfiguriert werden, mit [gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

## <a name="prerequisites"></a>Erforderliche Komponenten  
Um dieses Tutorial abzuschließen, benötigen Sie:

- Zwei Instanzen von SQL Server mit der neuesten Version von SQL Server unter Linux
- Ein Tool zum Problem T-SQL-Abfragen zum Einrichten der Replikation, z. B. SQLCMD oder SSMS

  Finden Sie unter [Verwenden von SSMS zum Verwalten von SQLServer unter Linux](./sql-server-linux-manage-ssms.md).

## <a name="detailed-steps"></a>Die Schritte im Detail

1. Aktivieren Sie SQL Server-Replikations-Agents für Linux aktivieren Sie SQL Server-Agents Replikations-Agents verwenden. Führen Sie auf beiden Hostcomputern die folgenden Befehle im Terminal ein. 

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  sudo systemctl restart mssql-server
  ```

1. Erstellen Sie die Beispieldatenbank und eine Tabelle auf Ihre Herausgeber Erstellen einer Beispieldatenbank und eine Tabelle, die als die Artikel für eine Veröffentlichung fungiert.

  ```sql
  CREATE DATABASE Sales
  GO
  USE [SALES]
  GO 
  CREATE TABLE CUSTOMER([CustomerID] [int] NOT NULL, [SalesAmount] [decimal] NOT NULL)
  GO 
  INSERT INTO CUSTOMER (CustomerID, SalesAmount) VALUES (1,100),(2,200),(3,300)
  ```

  Erstellen Sie auf der anderen SQL Server-Instanz, dem Abonnenten, die Datenbank, um den Artikeln zu erhalten.

  ```sql
  CREATE DATABASE Sales
  GO
  ```

1. Erstellen Sie der momentaufnahmeordner für SQL Server-Agents zum Lesen und schreiben, auf dem Verteiler, erstellen den momentaufnahmeordner und gewähren von Zugriff für "Mssql" Benutzer 

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

1. Konfigurieren des Verteilers In diesem Beispiel, der Verleger werden sich auch auf dem Verteiler. Führen Sie die folgenden Befehle auf dem Verleger die Instanz für die Verteilung sowie konfigurieren.

  ```sql
  DECLARE @distributor AS sysname
  DECLARE @distributorlogin AS sysname
  DECLARE @distributorpassword AS sysname
  -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
  SET @distributor = N'<distributor instance name>'--in this example, it will be the name of the publisher
  SET @distributorlogin = N'<distributor login>'
  SET @distributorpassword = N'<distributor password>'
  -- Specify the distribution database. 
  
  use master
  exec sp_adddistributor @distributor = @distributor -- this should be the hostname

  -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
  exec sp_adddistributiondb @database = N'distribution', @log_file_size = 2, @deletebatchsize_xact = 5000, @deletebatchsize_cmd = 2000, @security_mode = 0, @login = @distributorlogin, @password = @distributorpassword
  GO

  DECLARE @snapshotdirectory AS nvarchar(500)
  SET @snapshotdirectory = N'/var/opt/mssql/data/ReplData/'

  -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
  use [distribution] 
  if (not exists (select * from sysobjects where name = 'UIProperties' and type = 'U ')) 
         create table UIProperties(id int) 
  if (exists (select * from ::fn_listextendedproperty('SnapshotFolder', 'user', 'dbo', 'table', 'UIProperties', null, null))) 
         EXEC sp_updateextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties' 
  else 
         EXEC sp_addextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties'
  GO
  ```

1. Konfigurieren Sie Verleger, führen die folgenden TSQL-Befehle auf dem Verleger.

  ```sql
  DECLARE @publisher AS sysname
  DECLARE @distributorlogin AS sysname
  DECLARE @distributorpassword AS sysname
  -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
  SET @publisher = N'<instance name>' 
  SET @distributorlogin = N'<distributor login>'
  SET @distributorpassword = N'<distributor password>'
  -- Specify the distribution database. 

  -- Adding the distribution publishers
  exec sp_adddistpublisher @publisher = @publisher, 
  @distribution_db = N'distribution', 
  @security_mode = 0, 
  @login = @distributorlogin, 
  @password = @distributorpassword, 
  @working_directory = N'/var/opt/mssql/data/ReplData', 
  @trusted = N'false', 
  @thirdparty_flag = 0, 
  @publisher_type = N'MSSQLSERVER'
  GO
  ```

1. Konfigurieren Sie Veröffentlichung Auftragsausführung die folgenden TSQL-Befehle auf dem Verleger.

  ```sql
  DECLARE @replicationdb AS sysname
  DECLARE @publisherlogin AS sysname
  DECLARE @publisherpassword AS sysname
  SET @replicationdb = N'Sales'
  SET @publisherlogin = N'<Publisher login>'
  SET @publisherpassword = N'<Publisher Password>'

  use [Sales]
  exec sp_replicationdboption @dbname = N'Sales', @optname = N'publish', @value = N'true'
  
  -- Add the snapshot publication
  exec sp_addpublication 
  @publication = N'SnapshotRepl', 
  @description = N'Snapshot publication of database ''Sales'' from Publisher ''<PUBLISHER HOSTNAME>''.',
  @retention = 0, 
  @allow_push = N'true', 
  @repl_freq = N'snapshot', 
  @status = N'active', 
  @independent_agent = N'true'

  exec sp_addpublication_snapshot @publication = N'SnapshotRepl', 
  @frequency_type = 1, 
  @frequency_interval = 1, 
  @frequency_relative_interval = 1, 
  @frequency_recurrence_factor = 0, 
  @frequency_subday = 8, 
  @frequency_subday_interval = 1, 
  @active_start_time_of_day = 0,
  @active_end_time_of_day = 235959, 
  @active_start_date = 0, 
  @active_end_date = 0, 
  @publisher_security_mode = 0, 
  @publisher_login = @publisherlogin, 
  @publisher_password = @publisherpassword
  ```

1. Erstellen Sie Artikel aus der Tabelle "sales" führen Sie die folgenden TSQL-Befehle auf dem Verleger.

  ```sql
  use [Sales]
  exec sp_addarticle 
  @publication = N'SnapshotRepl', 
  @article = N'customer', 
  @source_owner = N'dbo', 
  @source_object = N'customer', 
  @type = N'logbased', 
  @description = null, 
  @creation_script = null, 
  @pre_creation_cmd = N'drop', 
  @schema_option = 0x000000000803509D,
  @identityrangemanagementoption = N'manual', 
  @destination_table = N'customer', 
  @destination_owner = N'dbo', 
  @vertical_partition = N'false'
  ```

1. Konfigurieren Sie Abonnement führen die folgenden TSQL-Befehle auf dem Verleger an.

  ```sql
  DECLARE @subscriber AS sysname
  DECLARE @subscriber_db AS sysname
  DECLARE @subscriberLogin AS sysname
  DECLARE @subscriberPassword AS sysname
  SET @subscriber = N'<Instance Name>' -- for example, MSSQLSERVER
  SET @subscriber_db = N'Sales'
  SET @subscriberLogin = N'<Subscriber Login>'
  SET @subscriberPassword = N'<Subscriber Password>'

  use [Sales]
  exec sp_addsubscription 
  @publication = N'SnapshotRepl', 
  @subscriber = @subscriber,
  @destination_db = @subscriber_db, 
  @subscription_type = N'Push', 
  @sync_type = N'automatic', 
  @article = N'all', 
  @update_mode = N'read only', 
  @subscriber_type = 0

  exec sp_addpushsubscription_agent 
  @publication = N'SnapshotRepl', 
  @subscriber = @subscriber,
  @subscriber_db = @subscriber_db, 
  @subscriber_security_mode = 0, 
  @subscriber_login =  @subscriberLogin,
  @subscriber_password =  @subscriberPassword,
  @frequency_type = 1,
  @frequency_interval = 0, 
  @frequency_relative_interval = 0, 
  @frequency_recurrence_factor = 0, 
  @frequency_subday = 0, 
  @frequency_subday_interval = 0, 
  @active_start_time_of_day = 0, 
  @active_end_time_of_day = 0, 
  @active_start_date = 0, 
  @active_end_date = 19950101
  GO
  ```

1. Ausführen von Replikations-Agent-Aufträge

  Führen Sie die folgende Abfrage zum Abrufen einer Liste von Aufträgen:

  ```sql
  SELECT name, date_modified FROM msdb.dbo.sysjobs order by date_modified desc
  ```

  Führen Sie den momentaufnahmeauftrag Replikation, um die Momentaufnahme zu generieren:

  ```sql
  USE msdb;  
  --generate snapshot of publications, for example
  EXEC dbo.sp_start_job N'PUBLISHER-PUBLICATION-SnapshotRepl-1'
  GO
  ```

  Führen Sie den momentaufnahmeauftrag Replikation, um die Momentaufnahme zu generieren:

  ```sql
  USE msdb;  
  --distribute the publication to subscriber, for example
  EXEC dbo.sp_start_job N'DISTRIBUTOR-PUBLICATION-SnapshotRepl-SUBSCRIBER'
  GO
  ```

1. Abonnenten herstellen und Abfragen von replizierten Daten 

  Überprüfen Sie auf dem Abonnenten die die Replikation funktioniert, indem Sie die folgende Abfrage ausführen:

  ```sql
  SELECT * from [Sales].[dbo].[CUSTOMER]
  ```

In diesem Tutorial haben Sie den SQL Server-Snapshotreplikation unter Linux mit zwei Instanzen von SQL Server mithilfe von Transact-SQL konfiguriert.

> [!div class="checklist"]
> * Aktivieren von SQL Server-Replikations-Agents für Linux
> * Erstellen einer Beispieldatenbank
> * Der momentaufnahmeordner für SQL Server-Agents-Zugriff konfigurieren
> * Konfigurieren des Verteilers
> * Konfigurieren des Verlegers
> * Konfigurieren von Veröffentlichung und Artikeln
> * Konfigurieren von Abonnenten 
> * Führen Sie die Replikationsaufträge

## <a name="see-also"></a>Siehe auch

Ausführliche Informationen zur Replikation finden Sie unter [Dokumentation zu SQL Server-Replikation](../relational-databases/replication/sql-server-replication.md).

## <a name="next-steps"></a>Nächste Schritte

[Konzepte: SQLServer-Replikation unter Linux](sql-server-linux-replication.md)

[Gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
