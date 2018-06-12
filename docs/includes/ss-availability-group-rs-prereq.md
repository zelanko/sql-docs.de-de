## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie die Verfügbarkeitsgruppe erstellen, müssen Sie:

- Ihre Umgebung so konfigurieren, dass alle Server kommunizieren können, die Verfügbarkeitsreplikate hosten sollen.
- Installieren Sie SQL Server. Weitere Einzelheiten finden Sie unter [Installieren von SQL Server](../database-engine/install-windows/install-sql-server.md).

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Aktivieren von Always On-Verfügbarkeitsgruppen und Neustarten von mssql-server

>[!NOTE]
>In dem unten aufgeführten Befehl werden Cmdlets aus dem sqlserver-Modul verwendet, das im PowerShell-Katalog veröffentlicht wurde. Sie können dieses Modul mit dem Befehl „Install-Module“ installieren.

Aktivieren Sie Always On-Verfügbarkeitsgruppen auf jedem Replikat, das eine SQL Server-Instanz hostet. Starten Sie anschließend den SQL Server-Dienst neu. Führen Sie für die Aktivierung und das Neustarten der SQL Server-Dienste den folgenden Befehl aus:

```powershell
Enable-SqlAlwaysOn -ServerInstance <server\instance> -Force
```

## <a name="enable-an-alwaysonhealth-event-session"></a>Aktivieren einer AlwaysOn_health-Ereignissitzung

Sie können optional die Sitzung für erweiterte Ereignisse (XE) von Always On-Verfügbarkeitsgruppen aktivieren, die Ihnen bei der Ursachendiagnose hilft, wenn Sie in einer Verfügbarkeitsgruppe Probleme beheben. Führen Sie auf jeder SQL Server-Instanz den folgenden Befehl aus:

```sql
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Weitere Informationen zu dieser XE-Sitzung finden Sie unter [Erweiterte Ereignisse von Always On-Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/always-on-extended-events.md).

## <a name="database-mirroring-endpoint-authentication"></a>Authentifizierung über Datenbank-Spiegelungsendpunkt

Die in der Verfügbarkeitsgruppe zur Leseskalierung involvierten Replikate müssen über den Endpunkt authentifiziert werden, damit die Synchronisierung ordnungsgemäß funktioniert. Für eine Authentifizierung dieser Art sind zwei Hauptszenarios möglich.

### <a name="service-account"></a>Dienstkonto

In einer Active Directory-Umgebung, in der sämtliche sekundäre Replikate mit derselben Domäne verknüpft sind, kann SQL Server eine Authentifizierung über das Dienstkonto durchführen. Sie müssen auf allen SQL Server-Instanzen explizit einen Anmeldenamen für das Dienstkonto erstellen:

```sql
CREATE LOGIN [<domain>\service account] FROM WINDOWS;
```

### <a name="sql-login-authentication"></a>SQL-Anmeldeauthentifizierung

In Umgebungen, in denen die sekundären Replikate nicht mit einer Active Directory-Domäne verknüpft sind, müssen Sie die SQL-Authentifizierung verwenden. Das folgende Transact-SQL-Skript erstellt eine Anmeldung mit dem Namen `dbm_login` und einen Benutzer mit dem Namen `dbm_user`. Aktualisieren Sie das Skript durch ein sicheres Kennwort. Führen Sie für sämtliche SQL Server-Instanzen den folgenden Befehl aus, um den Endpunktbenutzer für die Datenbankspiegelung zu erstellen:

```sql
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

#### <a name="certificate-authentication"></a>Zertifikatauthentifizierung

Wenn Sie ein sekundäres Replikat verwenden, für das eine Authentifizierung über die SQL-Authentifizierung erforderlich ist, verwenden Sie ein Zertifikat für die Authentifizierung zwischen den Spiegelungsendpunkten.

Das folgende Transact-SQL-Skript erstellt einen Hauptschlüssel und ein Zertifikat. Anschließend werden das Zertifikat und die Datei mit einem privaten Schlüssel gesichert. Aktualisieren Sie das Skript durch sichere Kennwörter. Führen Sie auf der primären SQL Server-Instanz das folgende Skript aus, um das Zertifikat auszuführen:

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

Zu diesem Zeitpunkt weist Ihr primäres SQL Server-Replikat ein Zertifikat unter `c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer` und einen privaten Schlüssel unter `c:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk` auf. Kopieren Sie diese beiden Dateien auf allen Servern, die Verfügbarkeitsreplikate hosten werden, an den gleichen Speicherort.

Stellen Sie bei jedem sekundären Replikat sicher, dass das Dienstkonto für SQL Server über Berechtigungen für den Zugriff auf das Zertifikat verfügt.

#### <a name="create-the-certificate-on-secondary-servers"></a>Erstellen des Zertifikats auf sekundären Servern

Das folgende Transact-SQL-Skript erstellt einen Hauptschlüssel und ein Zertifikat aus der Sicherung, die Sie auf dem primären SQL Server-Replikat erstellt haben. Der Befehl autorisiert auch den Benutzer, damit er Zugriff auf das Zertifikat hat. Aktualisieren Sie das Skript durch sichere Kennwörter. Das Entschlüsselungskennwort ist mit dem Kennwort identisch, das Sie für die Erstellung der `.pvk`-Datei in einem vorherigen Schritt verwendet haben. Führen Sie das folgende Skript auf allen sekundären Replikaten aus, um das Zertifikat zu erstellen:

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Erstellen des Datenbankspiegelungs-Endpunkte auf allen Replikaten

Datenbank-Spiegelungsendpunkte senden und empfangen Meldungen zwischen den Serverinstanzen beim Teilnehmen an Datenbankspiegelungssitzungen über TCP (Transmission Control Protocol) oder beim Hosten verfügbarer Replikate. Der Datenbank-Spiegelungsendpunkt lauscht an einer eindeutigen TCP-Portnummer.

Das folgende Transact-SQL-Skript erstellt für die Verfügbarkeitsgruppe einen Überwachungsendpunkt mit dem Namen `Hadr_endpoint`. Es startet den Endpunkt und erteilt eine Verbindungsberechtigung für das Dienstkonto oder die SQL-Anmeldung, die Sie in einem vorherigen Schritt erstellt haben. Bevor Sie das Skript ausführen, ersetzen Sie die Werte zwischen `**< ... >**`. Sie können optional eine IP-Adresse einschließen `LISTENER_IP = (0.0.0.0)`. Bei der IP-Adresse des Listeners muss es sich um eine IPv4-Adresse handeln. Sie können auch `0.0.0.0` verwenden.

Aktualisieren Sie auf sämtlichen SQL Server-Instanzen das folgende Transact-SQL-Skript für Ihre Umgebung:

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [<service account or user>];
```

Der TCP-Port in der Firewall muss für den Listenerport geöffnet sein.

Weitere Informationen finden Sie unter [Der Datenbankspiegelungs-Endpunkt (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
