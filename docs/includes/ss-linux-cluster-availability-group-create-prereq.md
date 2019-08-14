---
ms.openlocfilehash: 7d392ee6791c120243b304ab24b2f8268499617d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215583"
---
## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie die Verfügbarkeitsgruppe erstellen, müssen Sie:

- Ihre Umgebung so konfigurieren, dass alle Server kommunizieren können, die Verfügbarkeitsreplikate hosten sollen.
- Installieren Sie SQL Server.

>[!NOTE]
>Unter Linux müssen Sie eine Verfügbarkeitsgruppe erstellen, bevor Sie sie als vom Cluster verwaltete Clusterressource hinzufügen. Dieses Dokument enthält ein Beispiel, in dem eine Verfügbarkeitsgruppe erstellt wird. Verteilungsspezifische Anweisungen zum Erstellen des Clusters und Hinzufügen der Verfügbarkeitsgruppe als Clusterressource finden Sie in den Links unter „Nächste Schritte“.

1. Aktualisieren Sie den Computernamen für jeden Host.

   Ein SQL Server-Name muss folgende Anforderungen erfüllen:
   
   - Maximal 15 Zeichen
   - Eindeutig innerhalb des Netzwerks
   
   Um den Computernamen festzulegen, bearbeiten Sie `/etc/hostname`. Mithilfe des folgenden Skripts können Sie `/etc/hostname` mit `vi` bearbeiten:

   ```bash
   sudo vi /etc/hostname
   ```

2. Konfigurieren Sie die Hostdatei.

    >[!NOTE]
    >Wenn Hostnamen mit ihren IP-Adressen im DNS-Server registriert sind, müssen Sie die folgenden Schritte nicht ausführten. Überprüfen Sie, ob alle Knoten, die zur Konfiguration der Verfügbarkeitsgruppe gehören sollen, miteinander kommunizieren können. (Ein ping-Befehl an den Hostnamen sollte mit der entsprechenden IP-Adresse antworten.) Stellen Sie außerdem sicher, dass die Datei „/etc/hosts“ keinen Eintrag enthält, in dem die localhost-IP-Adresse 127.0.0.1 dem Hostnamen des Knotens zugeordnet wird.
    >

   Die Hostdatei auf jedem Server enthält die IP-Adressen und Namen aller Server, die in die Verfügbarkeitsgruppe einbezogen werden. 

   Der folgende Befehl gibt die IP-Adresse des aktuellen Servers zurück:

   ```bash
   sudo ip addr show
   ```

   Aktualisieren Sie `/etc/hosts`. Mithilfe des folgenden Skripts können Sie `/etc/hosts` mit `vi` bearbeiten:

   ```bash
   sudo vi /etc/hosts
   ```

   In folgendem Beispiel wird `/etc/hosts` auf **node1** mit Ergänzungen für **node1**, **node2** und **node3** veranschaulicht. In diesem Dokument bezieht sich **node1** auf den Server, der das primäre Replikat hostet. **node2** und **node3** beziehen sich auf den Server, der die sekundären Replikate hostet.

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>Installieren von SQL Server

Installieren Sie SQL Server. Die folgenden Links verweisen auf SQL Server-Installationsanweisungen für verschiedene Verteilungen: 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Aktivieren von Always On-Verfügbarkeitsgruppen und Neustarten von mssql-server

Aktivieren Sie Always On-Verfügbarkeitsgruppen auf jedem Knoten, der eine SQL Server-Instanz hostet. Starten Sie `mssql-server` dann neu. Führen Sie folgendes Skript aus:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwayson_health-event-session"></a>Aktivieren einer AlwaysOn_health-Ereignissitzung 

Sie können optional erweiterte Ereignisse der AlwaysOn-Verfügbarkeitsgruppen aktivieren, die Ihnen bei der Ursachendiagnose helfen, wenn Sie Probleme in einer Verfügbarkeitsgruppe behandeln. Führen Sie auf jeder SQL Server-Instanz den folgenden Befehl aus: 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Weitere Informationen zu dieser XE-Sitzung finden Sie unter [AlwaysOn Extended Events](https://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-a-certificate"></a>Erstellen eines Zertifikats

Der SQL Server-Dienst unter Linux verwendet Zertifikate zum Authentifizieren von Kommunikation zwischen den Spiegelungsendpunkten. 

Das folgende Transact-SQL-Skript erstellt einen Hauptschlüssel und ein Zertifikat. Anschließend werden das Zertifikat und die Datei mit einem privaten Schlüssel gesichert. Aktualisieren Sie das Skript durch sichere Kennwörter. Stellen Sie eine Verbindung mit der primären SQL Server-Instanz her. Führen Sie das folgende Transact-SQL-Skript aus, um das Zertifikat zu erstellen:

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

Zu diesem Zeitpunkt weist Ihr primäres SQL Server-Replikat ein Zertifikat unter `/var/opt/mssql/data/dbm_certificate.cer` und einen privaten Schlüssel unter `var/opt/mssql/data/dbm_certificate.pvk` auf. Kopieren Sie diese beiden Dateien auf allen Servern, die Verfügbarkeitsreplikate hosten werden, an den gleichen Speicherort. Verwenden Sie den mssql-Benutzer, oder erteilen Sie dem mssql-Benutzer Berechtigungen, um auf diese Dateien zuzugreifen. 

Der folgende Befehl kopiert z.B. auf dem Quellserver die Dateien auf den Zielcomputer. Ersetzen Sie die `**<node2>**`-Werte durch die Namen der SQL Server-Instanzen, die die Replikate hosten werden. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

Erteilen Sie auf jedem Zielserver dem mssql-Benutzer die Berechtigung, damit er auf das Zertifikat zugreifen kann.

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

Das folgende Transact-SQL-Skript erstellt für die Verfügbarkeitsgruppe einen Überwachungsendpunkt mit dem Namen `Hadr_endpoint`. Es startet den Endpunkt, und erteilt Verbindungsberechtigung an das Zertifikat, das Sie erstellt haben. Bevor Sie das Skript ausführen, ersetzen Sie die Werte zwischen `**< ... >**`. Sie können optional eine IP-Adresse einschließen `LISTENER_IP = (0.0.0.0)`. Bei der IP-Adresse des Listeners muss es sich um eine IPv4-Adresse handeln. Sie können auch `0.0.0.0` verwenden. 

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
>Wenn Sie SQL Server Express Edition auf einem Knoten verwenden, um ein Konfigurationsreplikat zu hosten, ist für `ROLE` nur der Wert `WITNESS` zulässig. Führen Sie das folgende Skript in SQL Server Express Edition aus:

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
>Für SQL Server 2017 ist `CERTIFICATE` die einzige Authentifizierungsmethode, die für den Datenbankspiegelungs-Endpunkt unterstützt wird. Die Option `WINDOWS` wird in einer zukünftigen Version aktiviert.

Weitere Informationen finden Sie unter [Der Datenbankspiegelungs-Endpunkt (SQL Server)](https://msdn.microsoft.com/library/ms179511.aspx).


