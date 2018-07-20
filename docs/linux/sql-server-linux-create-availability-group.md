---
title: Erstellen und konfigurieren Sie eine verfügbarkeitsgruppe für SQL Server unter Linux | Microsoft-Dokumentation
description: Dieses Tutorial veranschaulicht das Erstellen und Konfigurieren von Verfügbarkeitsgruppen für SQL Server unter Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 06/28/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 21ca1eea093121107b2e04cff40b6f749a6c6bda
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083492"
---
# <a name="create-and-configure-an-availability-group-for-sql-server-on-linux"></a>Erstellen Sie und konfigurieren Sie eine verfügbarkeitsgruppe für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Tutorial wird beschrieben, wie zum Erstellen und Konfigurieren einer verfügbarkeitsgruppe (AG) für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux. Im Gegensatz zu [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] und zuvor auf Windows, können Verfügbarkeitsgruppen mit oder ohne zuerst den zugrunde liegenden Pacemaker-Cluster zu erstellen. Integration mit dem Cluster bei Bedarf einem späteren Zeitpunkt erfolgt nicht.

Das Tutorial umfasst die folgenden Aufgaben:
 
> [!div class="checklist"]
> * Aktivieren Sie Verfügbarkeitsgruppen.
> * Erstellen Sie die Availability Group-Endpunkten und Zertifikaten.
> * Verwendung [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) oder Transact-SQL zum Erstellen einer verfügbarkeitsgruppe.
> * Erstellen der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Anmeldung und Berechtigungen für Pacemaker.
> * Erstellen Sie Verfügbarkeit Gruppieren von Ressourcen in einem Pacemaker-Cluster (nur für externen Typ).

## <a name="prerequisite"></a>Voraussetzung
- Pacemaker Cluster mit hochverfügbarkeit bereitstellen, wie in beschrieben [ein Pacemaker-Clusters für SQL Server unter Linux bereitstellen](sql-server-linux-deploy-pacemaker-cluster.md).


## <a name="enable-the-availability-groups-feature"></a>Aktivieren Sie die Funktion "Verfügbarkeitsgruppen"

Im Gegensatz zu auf Windows, Sie können nicht mithilfe von PowerShell oder [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Konfigurations-Manager die Verfügbarkeit zu Gruppen (AG)-Funktion. Sie müssen unter Linux verwenden `mssql-conf` zum Aktivieren des Features. Es gibt zwei Möglichkeiten, um die Funktion "Verfügbarkeitsgruppen" zu aktivieren: Verwenden der `mssql-conf` -Hilfsprogramm, oder Sie bearbeiten die `mssql.conf` Datei manuell.

> [!IMPORTANT]
> Die AG-Funktion muss für reines konfigurationsreplikat Replikate aktiviert sein, auch auf [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)].

### <a name="use-the-mssql-conf-utility"></a>Verwenden Sie das Dienstprogramm für die Mssql-conf

Geben Sie an einer Eingabeaufforderung Folgendes ein:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
```

### <a name="edit-the-mssqlconf-file"></a>Bearbeiten Sie die Datei mssql.conf

Sie können auch ändern, die `mssql.conf` -Datei befindet sich unter der `/var/opt/mssql` Ordner die folgenden Zeilen hinzufügen:

```
[hadr]

hadr.hadrenabled = 1
```

### <a name="restart-includessnoversion-mdincludesssnoversion-mdmd"></a>Neu starten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Nach der Aktivierung von Verfügbarkeitsgruppen, wie auf Windows, Sie neu starten müssen [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Kann durch Folgendes geschehen:

```bash
sudo systemctl restart mssql-server
```

## <a name="create-the-availability-group-endpoints-and-certificates"></a>Erstellen Sie die verfügbarkeitsgruppenendpunkte Verfügbarkeit und Zertifikate

Eine verfügbarkeitsgruppe verwendet TCP-Endpunkte für die Kommunikation. Unter Linux werden die Endpunkte für eine Verfügbarkeitsgruppe nur unterstützt, wenn Zertifikate für die Authentifizierung verwendet werden. Dies bedeutet, dass das Zertifikat von einer Instanz muss auf allen anderen Instanzen wiederhergestellt werden, die Replikate, die in derselben Verfügbarkeitsgruppe beteiligt werden. Der Prozess ist auch für eine reine konfigurationsreplikat erforderlich. 

Erstellen von Endpunkten und Wiederherstellen von Zertifikaten können nur über Transact-SQL erfolgen. Sie können nicht[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-generierte Zertifikate auch. Sie benötigen auch einen Prozess zum Verwalten, und Ersetzen Sie alle Zertifikate, die ablaufen.

> [!IMPORTANT]
> Wenn Sie planen, verwenden Sie die [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] Assistenten zum Erstellen der Verfügbarkeitsgruppe, Sie trotzdem müssen zum Erstellen und Wiederherstellen der Zertifikate mithilfe von Transact-SQL unter Linux.

Wenden Sie für die vollständige Syntax für die verfügbaren Optionen für die verschiedenen Befehle (z. B. die Erhöhung der Sicherheit) ist sich an:

-   [BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)
-   [ZERTIFIKAT ERSTELLEN](../t-sql/statements/create-certificate-transact-sql.md)
-   [CREATE ENDPOINT](../t-sql/statements/create-endpoint-transact-sql.md)

> [!NOTE]
> Auch wenn Sie eine verfügbarkeitsgruppe erstellen, die der Typ des Endpunkts verwendet *FOR DATABASE_MIRRORING*, da einige Aspekte der zugrunde liegenden für diese jetzt veralteten Funktion einmal freigegeben wurden.

In diesem Beispiel wird die Zertifikate für eine Konfiguration mit drei Knoten erstellt. Die Instanznamen sind LinAGN1 LinAGN2 und LinAGN3.

1.  Führen Sie den folgenden LinAGN1, um den Hauptschlüssel, Zertifikat und Endpunkt zu erstellen sowie sichern Sie das Zertifikat. In diesem Beispiel wird die typische TCP-Port 5022 für den Endpunkt verwendet.
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN1_Cert
    WITH SUBJECT = 'LinAGN1 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN1_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN1_Cert,
        ROLE = ALL);
    
    GO
    ```
    
2.  Führen Sie auf LinAGN2 identisch:
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    WITH SUBJECT = 'LinAGN2 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN2_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN2_Cert,
        ROLE = ALL);
    
    GO
    ```
    
3.  Führen Sie abschließend die gleiche Sequenz auf LinAGN3 ein:
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    WITH SUBJECT = 'LinAGN3 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN3_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN3_Cert,
        ROLE = ALL);
    
    GO
    ```
    
4.  Mithilfe von `scp` oder einem anderen Hilfsprogramm, die Sicherungen des Zertifikats in jedem Knoten zu kopieren, die Teil der Verfügbarkeitsgruppe sein wird.
    
    Für dieses Beispiel:
    
    - Kopieren Sie LinAGN1_Cert.cer LinAGN2 und LinAGN3
    - Kopieren Sie LinAGN2_Cert.cer LinAGN1 und LinAGN3.
    - Kopieren Sie LinAGN3_Cert.cer LinAGN1 und LinAGN2.
    
5.  Ändern Sie den Besitz und die Gruppe, die die kopierten Dateien auf zugeordneten `mssql`.
    
    ```bash
    sudo chown mssql:mssql <CertFileName>
    ```
    
6.  Erstellen Sie auf Instanzebene Anmeldungen und Benutzer mit LinAGN2 und LinAGN3 auf LinAGN1 verknüpft sind.
    
    ```SQL
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
7.  Wiederherstellen Sie LinAGN2_Cert und LinAGN3_Cert auf LinAGN1. Die anderen Replikate Zertifikate ist ein wichtiger Aspekt der AG-Kommunikation und Sicherheit.
    
    ```SQL
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
8.  Grant the logins associated with LinAG2 and LinAGN3 permission to connect to the endpoint on LinAGN1.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
9.  Erstellen Sie auf Instanzebene Anmeldungen und Benutzer mit LinAGN1 und LinAGN3 auf LinAGN2 verknüpft sind.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
10.  Wiederherstellen Sie LinAGN1_Cert und LinAGN3_Cert auf LinAGN2. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
11.  Grant the logins associated with LinAG1 and LinAGN3 permission to connect to the endpoint on LinAGN2.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
12.  Erstellen Sie auf Instanzebene Anmeldungen und Benutzer mit LinAGN1 und LinAGN2 auf LinAGN3 verknüpft sind.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    ```
    
13.  Wiederherstellen Sie LinAGN1_Cert und LinAGN2_Cert auf LinAGN3. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
14.  Grant the logins associated with LinAG1 and LinAGN2 permission to connect to the endpoint on LinAGN3.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    ```

## <a name="create-the-availability-group"></a>Erstellen der verfügbarkeitsgruppe

In diesem Abschnitt wird beschrieben, wie mit [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) oder Transact-SQL zum Erstellen der verfügbarkeitsgruppe für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

### <a name="use-includessmanstudiofull-mdincludesssmanstudiofull-mdmd"></a>Verwendung von [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]

In diesem Abschnitt zeigt, wie zum Erstellen einer Verfügbarkeitsgruppe mit dem Clustertyp External mithilfe von SSMS mit dem Assistenten für neue Verfügbarkeitsgruppen.

1.  Erweitern Sie in SSMS **hohe Verfügbarkeit mit AlwaysOn**, klicken Sie mit der rechten Maustaste auf **Verfügbarkeitsgruppen**, und wählen Sie **Assistenten für neue Verfügbarkeitsgruppen**.

2.  Klicken Sie auf das Einführungsdialogfeld **Weiter**.

3.  Klicken Sie im Dialogfeld "Optionen der Verfügbarkeitsgruppe angeben" Geben Sie einen Namen für die verfügbarkeitsgruppe, und wählen Sie einen Clustertyp EXTERNAL oder NONE, in der Dropdownliste aus. Externe sollte verwendet werden, wenn Pacemaker bereitgestellt wird. None ist für spezielle Szenarien, z. B. read Scale out. Auswählen der Option für die integritätserkennung auf Datenbankebene ist optional. Weitere Informationen zu dieser Option finden Sie unter [Datenbank auf Datenbankebene Detection Failover verfügbarkeitsgruppenoption](../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md). Klicken Sie auf **Weiter**.

    ![](./media/sql-server-linux-create-availability-group/image3.png)

4.  Klicken Sie im Dialogfeld "Datenbanken auswählen" Wählen Sie die Datenbanken, die in der Verfügbarkeitsgruppe einbezogen werden. Jede Datenbank muss eine vollständige Sicherung haben, bevor es zu einer Verfügbarkeitsgruppe hinzugefügt werden kann. Klicken Sie auf **Weiter**.

5.  Klicken Sie in das Dialogfeld "Replikate angeben" auf **Hinzufügen von Replikaten**.

6.  Verbindung mit dem Dialogfeld "Server" herstellen, geben Sie den Namen der Instanz von Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] , werden die Anmeldeinformationen für die Verbindung und das sekundäre Replikat. Klicken Sie auf **Verbinden**.

7.  Wiederholen Sie die vorherigen beiden Schritte aus, für die Instanz, die ein reines konfigurationsreplikat Replikat oder ein weiteres sekundäres Replikat enthält.

8.  Alle drei Instanzen sollte jetzt auf das Dialogfeld "Replikate angeben" aufgeführt werden. Wenn Sie einen Cluster "extern" für das sekundäre Replikat zu verwenden, die "true" einer sekundären Datenbank werden, stellen Sie sicher, dass der Verfügbarkeitsmodus übereinstimmt, der das primäre Replikat und Failovermodus auf External festgelegt ist. Wählen Sie für das reine konfigurationsreplikat nur ein Verfügbarkeitsmodus der Konfiguration ein.

    Das folgende Beispiel zeigt eine Verfügbarkeitsgruppe mit zwei Replikate mit dem Clustertyp External und ein reines konfigurationsreplikat Replikat.

    ![](./media/sql-server-linux-create-availability-group/image4.png)

    Das folgende Beispiel zeigt eine Verfügbarkeitsgruppe mit zwei Replikaten, die dem Clustertyp None und ein reines konfigurationsreplikat Replikat.

    ![](./media/sql-server-linux-create-availability-group/image5.png)

9.  Wenn Sie die sicherungseinstellungen ändern möchten, klicken Sie auf der Registerkarte "Sicherungseinstellungen". Weitere Informationen zu sicherungseinstellungen mit Verfügbarkeitsgruppen, finden Sie unter [Konfigurieren der Sicherung auf verfügbarkeitsreplikaten](../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).

10. Wenn lesbare sekundäre Datenbanken verwenden, oder erstellen eine Verfügbarkeitsgruppe mit einem Cluster keine leseskalierung eingeben möchten, können Sie einen Listener erstellen, durch Auswählen der Registerkarte "Listener". Ein Listener kann auch später hinzugefügt werden. Um einen Listener zu erstellen, wählen Sie die Option **erstellen ein verfügbarkeitsgruppenlisteners** , und geben Sie einen Namen, einen TCP/IP-Port und angibt, ob eine statische oder automatisch zugewiesene DHCP IP-Adresse verwendet. Denken Sie daran, dass für eine Verfügbarkeitsgruppe mit dem Clustertyp None, die IP-Adresse statisch und festgelegt werden soll in der primären IP-Adresse.

    ![](./media/sql-server-linux-create-availability-group/image6.png)

11. Wenn ein Listener für lesbare Szenarien erstellt wird, kann SSMS 17.3 oder höher die Erstellung des schreibgeschützten Routings im Assistenten aus. Sie können auch später über SSMS oder Transact-SQL-hinzugefügt werden. So fügen Sie schreibgeschütztes routing jetzt hinzu

    A.  Wählen Sie die Registerkarte des schreibgeschützten Routing.

    B.  Geben Sie die URLs für den schreibgeschützten Replikaten ein. Diese URLs sind Endpunkte zu ähnlich, außer sie den Port der Instanz nicht auf den Endpunkt zu verwenden.

    c.  Wählen Sie jede URL, und wählen Sie im unteren Bereich die lesbaren Replikate. Halten Sie um mehrere Metriken auszuwählen UMSCHALT oder klicken und ziehen.

12. Klicken Sie auf **Weiter**.

13. Wählen Sie, wie sekundären Replikat initialisiert werden. Der Standardwert ist die Verwendung [Automatisches seeding](../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md), erfordert den gleichen Pfad auf allen Servern, die in der Verfügbarkeitsgruppe teilnehmen. Sie können auch veranlassen, den Assistenten werden ein sicherungs-, Kopier- und Wiederherstellen (die zweite Option erstellt). Lassen Sie sie verknüpfen, wenn Sie manuell gesichert, kopiert und die Datenbank auf den Replikaten wiederhergestellt haben (dritte option); oder fügen Sie die Datenbank später (letzte Option). Wie bei der Zertifikate, wenn Sie manuell Sicherungen sind, und kopieren, muss Berechtigungen für die Sicherungsdateien für den anderen Replikaten festgelegt werden soll. Klicken Sie auf **Weiter**.

14. Klicken Sie im Dialogfeld "Überprüfung" Wenn alles, was nicht als Erfolg zurückgegeben, zu untersuchen. Einige Warnungen sind zulässig und werden nicht schwerwiegend, z. B. Wenn Sie keinen Listener erstellen. Klicken Sie auf **Weiter**.

15. Klicken Sie auf das Dialogfeld "Zusammenfassung" auf **Fertig stellen**. Der Prozess zum Erstellen der Verfügbarkeitsgruppe wird jetzt gestartet werden.

16. Wenn die Erstellung der Verfügbarkeitsgruppe abgeschlossen ist, klicken Sie auf **schließen** auf den Ergebnissen. Sie sehen nun die Verfügbarkeitsgruppe auf den Replikaten in der dynamischen Verwaltungssichten sowie die hohe Verfügbarkeit mit AlwaysOn-Ordner, in SSMS.

### <a name="use-transact-sql"></a>Verwenden von Transact-SQL

Dieser Abschnitt zeigt Beispiele für die Erstellung einer Verfügbarkeitsgruppe mit Transact-SQL. Der Listener und schreibgeschütztes routing können konfiguriert werden, nachdem die Verfügbarkeitsgruppe erstellt wurde. Die Verfügbarkeitsgruppe selbst geändert werden kann, mit `ALTER AVAILABILITY GROUP`, aber ändern den Cluster-Typ kann nicht durchgeführt werden, [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Wenn Sie nicht zum Erstellen einer Verfügbarkeitsgruppe mit dem Clustertyp External beabsichtigt, müssen Sie löschen und neu erstellen, mit dem Clustertyp None. Weitere Informationen und anderen Optionen die folgenden Links finden Sie unter:

-   [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)
-   [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md)
-   [Konfigurieren des schreibgeschützten Routings für eine Verfügbarkeitsgruppe (SQLServer)](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners (SQLServer)](../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)

#### <a name="example-one--two-replicas-with-a-configuration-only-replica-external-cluster-type"></a>Beispiel 1: zwei Replikate mit einem Replikat für reines konfigurationsreplikat (externen Cluster-Typ)

Dieses Beispiel zeigt, wie Sie eine Verfügbarkeitsgruppe zwei Replikaten erstellen, die ein reines konfigurationsreplikat Replikat verwendet wird.

1.  Führen Sie auf den Knoten, der das primäre Replikat mit der vollständig Lese-/Schreibkopie der Datenbank(en) werden. Dieses Beispiel verwendet das automatische seeding.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1' WITH (
       ENDPOINT_URL = N' TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       SEEDING_MODE = AUTOMATIC),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       AVAILABILITY_MODE = CONFIGURATION_ONLY);
       
    GO
    ```
    
2.  Führen Sie in einem Abfrage-Fenster, das das andere Replikat verbunden ist Folgendes ein, um verknüpfen Sie das Replikat zur Verfügbarkeitsgruppe, und der Seedingvorgang müssen vom primären zum sekundären Replikat zu initiieren.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Fügen sie in einem Abfrage-Fenster, das mit dem reinen konfigurationsreplikat verbunden ist der Verfügbarkeitsgruppe.
    
   ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
   ```

#### <a name="example-two--three-replicas-with-read-only-routing-external-cluster-type"></a>Beispiel 2 – 3 Replikate mit schreibgeschütztes routing (externen Cluster-Typ)

Dieses Beispiel zeigt drei vollständige, dass die Replikate und wie schreibgeschütztes routing im Rahmen der anfänglichen Erstellung der Verfügbarkeitsgruppe konfiguriert werden können.

1.  Führen Sie auf den Knoten, der das primäre Replikat mit der vollständig Lese-/Schreibkopie der Datenbank(en) werden. Dieses Beispiel verwendet das automatische seeding.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN2.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:1433')),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN2.FullyQualified.Name:1433')),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN3.FullyQualified.Name:1433'))
    LISTENER '<ListenerName>' (WITH IP = ('<IPAddress>', '<SubnetMask>'), Port = 1433);
    
    GO
    ```
    
    Einige Dinge zu dieser Konfiguration zu beachten:
    
    - *AGName* ist der Name der verfügbarkeitsgruppe.
    - *DBName* ist der Name der Datenbank, die mit der verfügbarkeitsgruppe verwendet wird. Es kann auch eine Liste von Namen durch Kommas getrennt sein.
    - *ListenerName* ist ein Name, der den zugrunde liegenden-Server/Knoten unterscheidet. Wird registriert, im DNS zusammen mit *IP-Adresse*.
    - *IP-Adresse* eine IP-Adresse, die mit zugeordnetem *ListenerName*. Es ist auch eindeutig und nicht identisch mit den Servern/Knoten. Anwendungen und Endbenutzern verwendet entweder *ListenerName* oder *IP-Adresse* zur Verbindung mit der Verfügbarkeitsgruppe.
    - *Subnetzmaske* ist die Subnetzmaske des *IP-Adresse*; z. B. 255.255.255.0.

2.  Führen Sie in einem Abfrage-Fenster, das das andere Replikat verbunden ist Folgendes ein, um verknüpfen Sie das Replikat zur Verfügbarkeitsgruppe, und der Seedingvorgang müssen vom primären zum sekundären Replikat zu initiieren.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Wiederholen Sie Schritt2 für das dritte Replikat aus.

#### <a name="example-three--two-replicas-with-read-only-routing-none-cluster-type"></a>Beispiel 3 – zwei Replikate mit schreibgeschütztes routing (kein cluster-Typ)

Dieses Beispiel zeigt die Erstellung einer Konfiguration mit zwei Replikaten mithilfe eines clustertyps ' None '. Es wird für das Szenario leseskalierung verwendet wird, auf dem kein Failover erwartet. Dadurch wird den Listener, der tatsächlich auf dem primären Replikat als auch das schreibgeschützte routing ist die Verwendung der Roundrobin-Funktionalität erstellt.

1.  Führen Sie auf den Knoten, der das primäre Replikat mit der vollständig Lese-/Schreibkopie der Datenbank(en) werden. Dieses Beispiel verwendet das automatische seeding.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = NONE)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name: <PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name'.'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:<PortOfInstance>'));
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:<PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL =N'TCP://LinAGN2.FullyQualified.Name:<PortOfInstance>'));
    LISTENER '<ListenerName>' (WITH IP = ('<PrimaryReplicaIPAddress>', '<SubnetMask>'), Port = <PortOfListener>);
    
    GO
    ```
    
    Erläuterungen
    - *AGName* ist der Name der verfügbarkeitsgruppe.
    - *DBName* ist der Name der Datenbank, die mit der verfügbarkeitsgruppe verwendet wird. Es kann auch eine Liste von Namen durch Kommas getrennt sein.
    - *PortOfEndpoint* ist die Portnummer ein, die den Endpunkt erstellt.
    - *PortOfInstance* ist die Portnummer, die von der Instanz verwendeten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].
    - *ListenerName* ist ein Name, die unterscheidet sich von der zugrunde liegenden Replikate, jedoch wird nicht tatsächlich verwendet werden.
    - *PrimaryReplicaIPAddress* ist die IP-Adresse des primären Replikats.
    - *Subnetzmaske* ist die Subnetzmaske des *IP-Adresse*. Z. B. 255.255.255.0.
    
2.  Fügen Sie das sekundäre Replikat der Verfügbarkeitsgruppe, und initiieren Sie das automatische seeding.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = NONE);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```

## <a name="create-the-includessnoversion-mdincludesssnoversion-mdmd-login-and-permissions-for-pacemaker"></a>Erstellen der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Anmeldung und Berechtigungen für Pacemaker

Eine Pacemaker hochverfügbarkeit-Cluster zugrunde liegenden [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux benötigt Zugriff auf die [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Instanz sowie Berechtigungen für die verfügbarkeitsgruppe selbst. Diesen Schritten erstellen Sie die Anmeldung und den zugeordneten Berechtigungen zusammen mit einer Datei, der angibt, wie Sie die Anmeldung beim Pacemaker [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

1.  Führen Sie in einem Abfrage-Fenster, das mit dem ersten Replikat verbunden ist die folgenden Schritte aus:

    ```SQL
    CREATE LOGIN PMLogin WITH PASSWORD '<StrongPassword>';
    
    GO
    
    GRANT VIEW SERVER STATE TO PMLogin;
    
    GO
    
    GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::<AGThatWasCreated> TO PMLogin;
    
    GO
    ```
    
2.  Geben Sie den Befehl, auf Knoten 1 
    ```bash
    sudo emacs /var/opt/mssql/secrets/passwd
    ```
    
    Emacs-Editor wird geöffnet.
    
3.  Geben Sie die folgenden zwei Zeilen in den Editor ein:

    ```
    PMLogin
    <StrongPassword>
    ```
    
4.  Halten Sie die STRG-Taste gedrückt, und drücken Sie dann die X, dann C, um zu beenden, und speichern Sie die Datei.

5.  Execute 
    ```bash
    sudo chmod 400 /var/opt/mssql/secrets/passwd
    ```
    
    die Datei zu sperren.

6.  Wiederholen Sie die Schritte 1 bis 5 für die anderen Server, die als Replikate dient.

## <a name="create-the-availability-group-resources-in-the-pacemaker-cluster-external-only"></a>Erstellen Sie die Ressourcen in der Pacemaker-Clusters (nur extern)

Gruppe wird nach einer verfügbarkeitsgruppe erstellt [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], die entsprechenden Ressourcen müssen in Pacemaker erstellt, wenn ein Clustertyp externer angegeben wird. Es gibt zwei Ressourcen, die mit einer Verfügbarkeitsgruppe verknüpft ist: die Verfügbarkeitsgruppe selbst und eine IP-Adresse. Konfigurieren die IP-Adressressource ist optional, wenn Sie die Listener-Funktionen nicht verwenden, werden jedoch empfohlen.

Die AG-Ressource, die erstellt wird, ist eine besondere Art von Ressource mit dem Namen eines Klons. Die AG-Ressource ist im Wesentlichen Kopien auf jedem Knoten, und es gibt eine steuernde Ressource mit dem Namen des Masters. Der Master ist verknüpft mit dem Server, die das primäre Replikat hostet. Die sekundären Replikate (reguläre oder reines konfigurationsreplikat) werden als untergeordnete Server und höher gestuft werden können, um master in einem Failovercluster.

1.  Erstellen Sie die AG-Ressource mit der folgenden Syntax aus:

    **Red Hat Enterprise Linux (RHEL) und Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failure-timeout=30s --master meta notify=true
    ```

    >[!NOTE]
    >Für RHEL 7.4 können Sie eine Warnung mit der Verwendung von – Master auftreten. Um dies zu vermeiden, verwenden `sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failover-timeout=30s master notify=true`
   
    **SUSE Linux Enterprise Server (SLES)**
    
    ```bash
    primitive <NameForAGResource> \
    ocf:mssql:ag \
    params ag_name="<AGName>" \
    meta failure-timeout=60s \
    op start timeout=60s \
    op stop timeout=60s \
    op promote timeout=60s \
    op demote timeout=10s \
    op monitor timeout=60s interval=10s \
    op monitor timeout=60s interval=11s role="Master" \
    op monitor timeout=60s interval=12s role="Slave" \
    op notify timeout=60s
    ms ms-ag_cluster <NameForAGResource> \
    meta master-max="1" master-node-max="1" clone-max="3" \
    clone-node-max="1" notify="true" \
    commit
    ```
    
    in denen *NameForAGResource* ist von den eindeutigen Namen für die Verfügbarkeitsgruppe, zu der dieser Clusterressource und *AGName* ist der Name der Verfügbarkeitsgruppe, die erstellt wurde.
 
2.  Erstellen Sie die IP-Adressressource, für die Verfügbarkeitsgruppe, der die Listener-Funktionen zugeordnet werden soll.

    **RHEL und Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForIPResource> ocf:heartbeat:IPaddr2 ip=<IPAddress> cidr_netmask=<Netmask>
    ```

    **SLES**
    
    ```bash
    crm configure \
    primitive <NameForIPResource> \
       ocf:heartbeat:IPaddr2 \
       params ip=<IPAddress> \
          cidr_netmask=<Netmask>
    ```
    
    in denen *NameForIPResource* ist der eindeutige Name für die IP-Adressressource und *IP-Adresse* die statische IP-Adresse der Ressource zugeordnet ist. Unter SLES müssen Sie auch die Netzmaske angeben. Beispielsweise müsste 255.255.255.0 einen Wert von 24 für *Netzmaske an.*
    
3.  Eine Zusammenstellung-Einschränkung muss konfiguriert werden, um sicherzustellen dass die IP-Adresse und die AG-Ressource auf dem gleichen Knoten ausgeführt werden.

    **RHEL und Ubuntu**
    
    ```bash
    sudo pcs constraint colocation add <NameForIPResource> <NameForAGResource>-master INFINITY with-rsc-role=Master
    ```

    **SLES**
    
    ```bash
    crm configure <NameForConstraint> inf: \
    <NameForIPResource> <NameForAGResource>:Master 
    commit
    ```
    
    in denen *NameForIPResource* ist der Name für die IP-Adressressource *NameForAGResource* ist der Name für die AG-Ressource, und klicken Sie auf SLES, *NameForConstraint* ist der Name für die Einschränkung.

4.  Erstellen Sie eine Sortierung der Einschränkung, um sicherzustellen, dass die AG-Ressource aktiv ist und ausgeführt wird, bevor Sie die IP-Adresse ein. Während die Einschränkung für die Zusammenstellung eine Bestellung-Einschränkung impliziert, werden diese erzwungen.

    **RHEL und Ubuntu**
    
    ```bash
    sudo pcs constraint order promote <NameForAGResource>-master then start <NameForIPResource>
    ```
    
    **SLES**
    
    ```bash
    crm configure \
    order <NameForConstraint> inf: <NameForAGResource>:promote <NameForIPResource>:start
    commit
    ```
    
    in denen *NameForIPResource* ist der Name für die IP-Adressressource *NameForAGResource* ist der Name für die AG-Ressource, und klicken Sie auf SLES, *NameForConstraint* ist der Name für die Einschränkung.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie zum Erstellen und Konfigurieren einer verfügbarkeitsgruppe für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux. Sie haben gelernt, wie auf:
> [!div class="checklist"]
> * Aktivieren Sie Verfügbarkeitsgruppen.
> * Erstellen von AG-Endpunkten und Zertifikaten.
> * Verwendung [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) oder Transact-SQL, um eine Verfügbarkeitsgruppe zu erstellen.
> * Erstellen der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Anmeldung und Berechtigungen für Pacemaker.
> * Erstellen Sie AG-Ressourcen in einen Pacemaker-Cluster.

Die meisten AG Verwaltungsaufgaben, einschließlich Upgrades und Ausführen eines Failovers finden Sie unter:

> [!div class="nextstepaction"]
> [Arbeiten Sie HA-verfügbarkeitsgruppe für SQL Server unter Linux](sql-server-linux-availability-group-failover-ha.md)

