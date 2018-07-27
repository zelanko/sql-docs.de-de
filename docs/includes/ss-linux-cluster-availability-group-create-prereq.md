## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie die Verfügbarkeitsgruppe erstellen, müssen Sie:

- Ihre Umgebung so konfigurieren, dass alle Server kommunizieren können, die Verfügbarkeitsreplikate hosten sollen.
- Installieren Sie SQL Server.

>[!NOTE]
>Unter Linux müssen Sie eine verfügbarkeitsgruppe erstellen, bevor Sie ihn als Clusterressource für die Verwaltung mit dem Cluster hinzufügen. Dieses Dokument enthält ein Beispiel, in dem eine Verfügbarkeitsgruppe erstellt wird. Distribution-spezifische Anweisungen zum Erstellen des Clusters, und fügen die verfügbarkeitsgruppe als Clusterressource finden Sie unter den Links unter "Nächste Schritte".

1. Aktualisieren Sie den Computernamen für jeden Host ein.

   Ein SQL Server-Name muss folgende Anforderungen erfüllen:
   
   - 15 Zeichen oder weniger.
   - Eindeutig innerhalb des Netzwerks.
   
   Um den Computernamen festzulegen, bearbeiten Sie `/etc/hostname`. Das folgende Skript können Sie bearbeiten `/etc/hostname` mit `vi`:

   ```bash
   sudo vi /etc/hostname
   ```

2. Konfigurieren Sie die Datei "Hosts".

    >[!NOTE]
    >Wenn Hostnamen mit ihrer IP-Adresse in der DNS-Server registriert sind, müssen Sie die folgenden Schritte ausführen. Überprüfen Sie, dass alles, was die Knoten als Teil der Konfiguration der verfügbarkeitsgruppe miteinander kommunizieren können. (Ein Ping an den Hostnamen muss die entsprechende IP-Adresse zurückgegeben.) Stellen Sie außerdem sicher, dass die Datei/etc/Hosts einen Eintrag enthält, der die "localhost" IP-Adresse 127.0.0.1 mit dem Hostnamen des Knotens zugeordnet.
    >

   Die Hostdatei auf jedem Server enthält die IP-Adressen und Namen aller Server, die in die Verfügbarkeitsgruppe einbezogen werden. 

   Der folgende Befehl gibt die IP-Adresse des aktuellen Servers zurück:

   ```bash
   sudo ip addr show
   ```

   Aktualisieren Sie `/etc/hosts`. Das folgende Skript können Sie bearbeiten `/etc/hosts` mit `vi`:

   ```bash
   sudo vi /etc/hosts
   ```

   In folgendem Beispiel wird `/etc/hosts` auf **node1** mit Ergänzungen für **node1**, **node2** und **node3** veranschaulicht. In diesem Dokument **node1** bezieht sich auf dem Server, der das primäre Replikat hostet. Und **node2** und **node3** finden Sie in Server, die die sekundären Replikate hosten.

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>Installieren von SQL Server

Installieren Sie SQL Server. Die folgenden Links verweisen auf SQL Server-installationsanweisungen für verschiedene Verteilungen: 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Aktivieren von Always On-Verfügbarkeitsgruppen und Neustarten von mssql-server

Aktivieren Sie AlwaysOn-Verfügbarkeitsgruppen auf jedem Knoten, der eine SQL Server-Instanz hostet. Starten Sie neu `mssql-server`. Führen Sie folgendes Skript aus:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwaysonhealth-event-session"></a>Aktivieren einer AlwaysOn_health-Ereignissitzung 

Sie können optional AlwaysOn Availability Gruppen erweiterte Ereignisse mit Ursachendiagnose helfen, bei der Problembehebung für einer verfügbarkeitsgruppe aktivieren. Führen Sie auf jeder SQL Server-Instanz den folgenden Befehl aus: 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Weitere Informationen zu dieser XE-Sitzung, finden Sie unter [AlwaysOn erweiterte Ereignisse](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-a-certificate"></a>Erstellen eines Zertifikats

Der SQL Server-Dienst unter Linux verwendet Zertifikate zum Authentifizieren von Kommunikation zwischen den Spiegelungsendpunkten. 

Das folgende Transact-SQL-Skript erstellt einen Hauptschlüssel und ein Zertifikat. Anschließend werden das Zertifikat und die Datei mit einem privaten Schlüssel gesichert. Aktualisieren Sie das Skript durch sichere Kennwörter. Verbinden Sie mit primären SQL Server-Instanz. Führen Sie das folgende Transact-SQL-Skript, um das Zertifikat zu erstellen:

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

Zu diesem Zeitpunkt weist Ihr primäres SQL Server-Replikat ein Zertifikat unter `/var/opt/mssql/data/dbm_certificate.cer` und einen privaten Schlüssel unter `var/opt/mssql/data/dbm_certificate.pvk` auf. Kopieren Sie diese beiden Dateien auf allen Servern, die Verfügbarkeitsreplikate hosten werden, an den gleichen Speicherort. Verwenden Sie den Mssql-Benutzer, oder erteilen Sie Berechtigungen für die Mssql-Benutzer Zugriff auf diese Dateien. 

Beispielsweise kopiert der folgende Befehl auf dem Quellserver die Dateien auf den Zielcomputer. Ersetzen Sie die `**<node2>**` Werte mit den Namen der SQL Server-Instanzen, die die Replikate hosten. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

Erteilen Sie Berechtigungen für die Mssql-Benutzer Zugriff auf das Zertifikat, klicken Sie auf jedem Zielserver.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Erstellen des Zertifikats auf sekundären Servern

Das folgende Transact-SQL-Skript erstellt einen Hauptschlüssel und ein Zertifikat aus der Sicherung, die Sie auf dem primären SQL Server-Replikat erstellt haben. Aktualisieren Sie das Skript durch sichere Kennwörter. Das Entschlüsselungskennwort ist das gleiche Kennwort, mit dem Sie die PVK-Datei in einem vorherigen Schritt erstellt haben. Um das Zertifikat zu erstellen, führen Sie das folgende Skript auf allen sekundären Servern aus:

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Erstellen des Datenbankspiegelungs-Endpunkte auf allen Replikaten

Datenbank-Spiegelungsendpunkte senden und empfangen Meldungen zwischen den Serverinstanzen beim Teilnehmen an Datenbankspiegelungssitzungen über TCP (Transmission Control Protocol) oder beim Hosten verfügbarer Replikate. Der Datenbank-Spiegelungsendpunkt lauscht an einer eindeutigen TCP-Portnummer. 

Das folgende Transact-SQL-Skript erstellt für die Verfügbarkeitsgruppe einen Überwachungsendpunkt mit dem Namen `Hadr_endpoint`. Es startet den Endpunkt, und erhalten die CONNECT-Berechtigung für das Zertifikat, das Sie erstellt haben. Bevor Sie das Skript ausführen, ersetzen Sie die Werte zwischen `**< ... >**`. Sie können optional eine IP-Adresse einschließen `LISTENER_IP = (0.0.0.0)`. Bei der IP-Adresse des Listeners muss es sich um eine IPv4-Adresse handeln. Sie können auch `0.0.0.0` verwenden. 

Aktualisieren Sie auf sämtlichen SQL Server-Instanzen das folgende Transact-SQL-Skript für Ihre Umgebung: 

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATABASE_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
```

>[!NOTE]
>Wenn Sie SQL Server Express Edition auf einem Knoten verwenden, um ein reines konfigurationsreplikat Replikat, das einzige gültige Wert zum Hosten `ROLE` ist `WITNESS`. Führen Sie das folgende Skript in SQL Server Express Edition:

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATABASE_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
```

Der TCP-Port in der Firewall muss für den Listenerport geöffnet sein.



>[!IMPORTANT]
>Für die SQL Server 2017-Version ist die einzige Authentifizierungsmethode für den datenbankspiegelungs-Endpunkt unterstützt `CERTIFICATE`. Die `WINDOWS` Option wird in einer zukünftigen Version aktiviert.

Weitere Informationen finden Sie unter [Der Datenbankspiegelungs-Endpunkt (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).


