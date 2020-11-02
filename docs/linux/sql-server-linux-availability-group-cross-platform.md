---
title: Konfigurieren einer SQL Server Always On-Verfügbarkeitsgruppe unter Windows und Linux
description: Erfahren Sie, wie Sie eine SQL Server-Always On-Verfügbarkeitsgruppe mit einem Replikat auf einem Windows-Server und dem anderen Replikat auf einem Linux-Server erstellen.
author: VanMSFT
ms.author: vanto
ms.reviewer: vanto
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 3800029fb04f058f6f2a0f00ed3f859d1385782e
ms.sourcegitcommit: 67befbf7435f256e766bbce6c1de57799e1db9ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92523895"
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Konfigurieren einer SQL Server Always On-Verfügbarkeitsgruppe unter Windows und Linux (plattformübergreifend)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/applies-to-version/sqlserver2017.md)]

In diesem Artikel werden die Schritte zum Erstellen einer Always On-Verfügbarkeitsgruppe (VG) mit einem Replikat auf einem Windows-Server und dem anderen Replikat auf einem Linux-Server erläutert. Diese Konfiguration ist plattformübergreifend, da die Replikate unter unterschiedlichen Betriebssystemen ausgeführt werden. Verwenden Sie diese Konfiguration für die Migration von einer Plattform zur anderen oder zur Notfallwiederherstellung. Diese Konfiguration unterstützt keine Hochverfügbarkeit, da keine Clusterlösung vorhanden ist, um eine plattformübergreifende Konfiguration zu verwalten. 

![Hybride Replikate unter „NONE“](./media/sql-server-linux-availability-group-overview/image1.png)

Bevor Sie fortfahren, sollten Sie mit der Installation und Konfiguration für SQL Server-Instanzen unter Windows und Linux vertraut sein. 

## <a name="scenario"></a>Szenario

In diesem Szenario werden zwei Server unter verschiedenen Betriebssystemen ausgeführt. Auf einem Computer mit Windows Server 2016 namens `WinSQLInstance` wird das primäre Replikat gehostet. Auf einem Linux-Server namens `LinuxSQLInstance` wird das sekundäre Replikat gehostet.

## <a name="configure-the-ag"></a>Konfigurieren der Verfügbarkeitsgruppe 

Die Schritte zum Erstellen der Verfügbarkeitsgruppe sind identisch mit den Schritten zum Erstellen einer Verfügbarkeitsgruppe für Workloads mit Leseskalierung. Die Verfügbarkeitsgruppe weist den Clustertyp NONE auf, weil kein Cluster-Manager vorhanden ist. 

   >[!NOTE]
   >In den Skripts in diesem Artikel werden Werte, die Sie Ihrer Umgebung entsprechend ersetzen müssen, in spitzen Klammern (`<` und `>`) angegeben. Die spitzen Klammern selbst sind für die Skripts nicht erforderlich. 

1. Installieren Sie SQL Server 2017 unter Windows Server 2016, aktivieren Sie Always On-Verfügbarkeitsgruppen von SQL Server-Konfigurations-Manager, und legen Sie die Authentifizierung im gemischten Modus fest. 

   >[!TIP]
   >Wenn Sie diese Lösung in Azure überprüfen, fügen Sie beide Server in dieselbe Verfügbarkeitsgruppe ein, um sicherzustellen, dass sie im Rechenzentrum voneinander getrennt werden. 

   **Aktivieren von Verfügbarkeitsgruppen**

   Anweisungen hierzu finden Sie unter [Aktivieren und Deaktivieren von Always On-Verfügbarkeitsgruppen (SQL Server)](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

   ![Aktivieren von Verfügbarkeitsgruppen](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   SQL Server-Konfigurations-Manager erkennt, dass es sich bei dem Computer nicht um einen Knoten in einem Failovercluster handelt. 

   Nachdem Sie Verfügbarkeitsgruppen aktiviert haben, starten Sie SQL Server neu.

   **Festlegen der Authentifizierung im gemischten Modus**

   Anweisungen hierzu finden Sie unter [Ändern des Serverauthentifizierungsmodus](../database-engine/configure-windows/change-server-authentication-mode.md#change-authentication-mode-with-ssms).

1. Installieren von SQL Server 2017 unter Linux Anweisungen hierzu finden Sie unter [Installieren von SQL Server](sql-server-linux-setup.md). Aktivieren Sie `hadr` mit „mssql-conf“.

   Um `hadr` mit dem Befehl „mssql-conf“ über eine Shelleingabeaufforderung zu aktivieren, geben Sie den folgenden Befehl ein:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   Nachdem Sie `hadr` aktiviert haben, starten Sie die SQL Server-Instanz neu.  

   Die folgende Abbildung zeigt diesen ganzen Schritt.

   ![Screenshot: Git Bash-Fenster mit dem Befehl](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. Konfigurieren Sie die Hostdatei auf beiden Servern, oder registrieren Sie die Servernamen bei DNS.

1. Öffnen Sie Firewallports für TPC 1433 und 5022 unter Windows und Linux.

1. Erstellen Sie auf dem primären Replikat einen Anmeldenamen und ein Kennwort für die Datenbank.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. Erstellen Sie auf dem primären Replikat einen Hauptschlüssel und ein Zertifikat, und sichern Sie das Zertifikat mit einem privaten Schlüssel.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
   BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
       );
   GO
   ```

1. Kopieren Sie das Zertifikat und den privaten Schlüssel auf den Linux-Server (sekundäres Replikat) unter `/var/opt/mssql/data`. Sie können `pscp` verwenden, um die Dateien auf den Linux-Server zu kopieren. 

1. Legen Sie die Gruppe und den Besitz des privaten Schlüssels und des Zertifikats auf `mssql:mssql` fest.

   Mit dem folgenden Skript werden die Gruppe und der Besitz der Dateien festgelegt. 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   In der folgenden Abbildung sind Besitz und Gruppe für Zertifikat und Schlüssel ordnungsgemäß festgelegt.

   ![Screenshot: Git Bash-Fenster mit der CER- und der PVK-Datei im Ordner „/var/opt/mssql/data“](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. Erstellen Sie auf dem sekundären Replikat einen Anmeldenamen und ein Kennwort für die Datenbank, und erstellen Sie einen Hauptschlüssel.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. Stellen Sie auf dem sekundären Replikat das Zertifikat wieder her, das Sie in `/var/opt/mssql/data` kopiert haben. 

   ```sql
   CREATE CERTIFICATE dbm_certificate   
       AUTHORIZATION dbm_user
       FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
       WITH PRIVATE KEY (
       FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
       DECRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
   )
   GO
   ```

1. Erstellen Sie auf dem primären Replikat einen Endpunkt.

   ```sql
   CREATE ENDPOINT [Hadr_endpoint]
       AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = 5022)
       FOR DATA_MIRRORING (
           ROLE = ALL,
           AUTHENTICATION = CERTIFICATE dbm_certificate,
           ENCRYPTION = REQUIRED ALGORITHM AES
           );
   ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
   GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login]
   GO
   ```

   >[!IMPORTANT]
   >Die Firewall muss für den TCP-Listenerport geöffnet sein. Im vorherigen Skript wird Port 5022 verwendet. Verwenden Sie einen beliebigen verfügbaren TCP-Port. 

1. Erstellen Sie den Endpunkt auf dem sekundären Replikat. Wiederholen Sie das vorherige Skript auf dem sekundären Replikat, um den Endpunkt zu erstellen. 

1. Erstellen Sie auf dem primären Replikat die Verfügbarkeitsgruppe mit `CLUSTER_TYPE = NONE`. Im Beispielskript wird `SEEDING_MODE = AUTOMATIC` verwendet, um die Verfügbarkeitsgruppe zu erstellen. 

   >[!NOTE]
   >Wenn die Windows-Instanz von SQL Server unterschiedliche Pfade für Daten- und Protokolldateien verwendet, schlägt das automatische Seeding für die Linux-Instanz von SQL Server fehl, da diese Pfade auf dem sekundären Replikat nicht vorhanden sind. Damit das folgende Skript für eine plattformübergreifende Verfügbarkeitsgruppe verwendet werden kann, muss in der Datenbank für die Daten- und Protokolldateien auf dem Windows-Server derselbe Pfad angegeben werden. Alternativ können Sie das Skript so aktualisieren, dass `SEEDING_MODE = MANUAL` festgelegt wird, und anschließend die Datenbank mit `NORECOVERY` sichern und wiederherstellen, um für die Datenbank ein Seeding auszuführen. 
   >
   >Dieses Verhalten gilt für Azure Marketplace-Images. 
   >
   >Weitere Informationen zum automatischen Seeding finden Sie unter [Automatisches Seeding – Datenträgerlayout](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout). 

   Aktualisieren Sie vor dem Ausführen des Skripts die Werte für Ihre Verfügbarkeitsgruppen.

      * Ersetzen Sie `<WinSQLInstance>` durch den Servernamen der SQL Server-Instanz des primären Replikats.

      * Ersetzen Sie `<LinuxSQLInstance>` durch den Servernamen der SQL Server-Instanz des sekundären Replikats. 

   Aktualisieren Sie zum Erstellen der Verfügbarkeitsgruppe die Werte, und führen Sie das Skript auf dem primären Replikat aus.  

   ```sql
   CREATE AVAILABILITY GROUP [ag1]
       WITH (CLUSTER_TYPE = NONE)
       FOR REPLICA ON
           N'<WinSQLInstance>' 
        WITH (
           ENDPOINT_URL = N'tcp://<WinSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            SEEDING_MODE = AUTOMATIC,
            FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
           N'<LinuxSQLInstance>' 
       WITH (
            ENDPOINT_URL = N'tcp://<LinuxSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
           SEEDING_MODE = AUTOMATIC,
           FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
           )
   GO
   ```
   
   Weitere Informationen finden Sie unter [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md).

1. Verknüpfen Sie die Verfügbarkeitsgruppe auf dem sekundären Replikat.

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. Erstellen Sie eine Datenbank für das sekundäre Replikat. In den Beispielschritten wird eine Datenbank mit dem Namen `<TestDB>` verwendet. Wenn Sie das automatische Seeding verwenden, legen Sie für die Daten- und die Protokolldateien denselben Pfad fest. 

   Aktualisieren Sie vor dem Ausführen des Skripts die Werte für die Datenbank.

      * Ersetzen Sie `<TestDB>` durch den Namen Ihrer Datenbank.

      * Ersetzen Sie `<F:\Path>` durch den Pfad der Datenbank und der Protokolldateien. Verwenden Sie für die Datenbank- und Protokolldateien denselben Pfad. 

      Sie können auch die Standardpfade verwenden. 

    Führen Sie das Skript aus, um die Datenbank zu erstellen. 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. Erstellen Sie eine vollständige Sicherung der Datenbank. 

1. Wenn Sie kein automatisches Seeding verwenden, stellen Sie die Datenbank auf dem sekundären Replikatserver (Linux) wieder her. [Migrieren einer SQL Server-Datenbank von Windows zu Linux mithilfe der Funktion Sichern und Wiederherstellen](sql-server-linux-migrate-restore-database.md) Stellen Sie die Datenbank `WITH NORECOVERY` auf dem sekundären Replikat wieder her. 

1. Fügen Sie die Datenbank der Verfügbarkeitsgruppe hinzu. Aktualisieren Sie das Beispielskript. Ersetzen Sie `<TestDB>` durch den Namen Ihrer Datenbank. Führen Sie auf dem primären Replikat die SQL-Abfrage aus, um der Verfügbarkeitsgruppe die Datenbank hinzuzufügen.

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. Stellen Sie sicher, dass die Datenbank auf dem sekundären Replikat aufgefüllt wird. 

## <a name="fail-over-the-primary-replica"></a>Ausführen eines Failovers für das primäre Replikat

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

In diesem Artikel wurden die Schritte zum Erstellen einer plattformübergreifenden Verfügbarkeitsgruppe zur Unterstützung der Migration oder von Workloads mit Leseskalierung beschrieben. Dieser Artikel kann für die manuelle Notfallwiederherstellung verwendet werden. In diesem Artikel wurde zudem erläutert, wie für die Verfügbarkeitsgruppe ein Failover ausgeführt wird. Eine plattformübergreifende Verfügbarkeitsgruppe verwendet den Clustertyp `NONE` und bietet keine Unterstützung für Hochverfügbarkeit, da kein plattformübergreifendes Clustertool vorhanden ist. 

## <a name="next-steps"></a>Nächste Schritte

[Übersicht über Always On-Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[SQL Server availability basics for Linux deployments (Grundlagen zur SQL Server-Verfügbarkeit für Linux-Bereitstellungen)](sql-server-linux-ha-basics.md)
