---
title: 'Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 10/04/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 90a9b797862db65187d991bb6961cdfd0bda8959
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523553"
---
# <a name="tutorial-getting-started-with-always-encrypted-with-secure-enclaves-using-ssms"></a>Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial werden Ihnen die erste Schritte mit [Always Encrypted mit Secure Enclaves](encryption/always-encrypted-enclaves.md) vermittelt. Es wird Folgendes gezeigt:
- Erstellen einer einfachen Umgebung zum Testen und Auswerten von Always Encrypted mit Secure Enclaves
- Direktes Verschlüsseln von Daten und Ausgeben umfangreicher Abfragen für verschlüsselte Spalten mithilfe von SQL Server Management Studio (SSMS)

## <a name="prerequisites"></a>Voraussetzungen

Für die ersten Schritte mit Always Encrypted mit Secure Enclaves benötigen Sie mindestens zwei Computer (dies können virtuelle Computer sein):

- SQL Server-Computer als Host für SQL Server und SSMS
- HGS-Computer zum Ausführen des Host-Überwachungsdiensts, der für den Enclave-Nachweis erforderlich ist

### <a name="sql-server-computer-requirements"></a>SQL Server-Computeranforderungen

- [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] oder höher
- Windows 10 Enterprise Version 1809 oder Windows Server 2019 Datacenter
- [SQL Server Management Studio (SSMS) 18.0 oder höher](../../ssms/download-sql-server-management-studio-ssms.md)

Alternativ können Sie SSMS auf einem anderen Computer installieren.

>[!WARNING] 
>In Produktionsumgebungen sollten Sie niemals SSMS oder andere Tools zum Verwalten von Always Encrypted-Schlüsseln oder Ausführen von Abfragen für verschlüsselte Daten auf dem SQL Server-Computer verwenden, da dies den Zweck der Verwendung von Always Encrypted mindern oder vollständig zunichte machen kann.

### <a name="hgs-computer-requirements"></a>HGS-Computeranforderungen

- Windows Server 2019 Standard oder Datacenter Edition
- 2 CPUs
- 8 GB RAM
- 100 GB Speicher

>[!NOTE]
>Der HGS-Computer sollte nicht mit einer Domäne verknüpft werden, bevor Sie beginnen.

## <a name="step-1-configure-the-hgs-computer"></a>Schritt 1: Konfigurieren des HGS-Computers

In diesem Schritt konfigurieren Sie den HGS-Computer zum Ausführen des Host-Überwachungsdiensts, der den Hostschlüsselnachweis unterstützt.

1. Melden Sie sich beim HGS-Computer als Administrator (lokaler Administrator) an, öffnen Sie eine Windows PowerShell-Konsole mit erhöhten Rechten, und fügen Sie die Rolle für den Host-Überwachungsdienst hinzu, indem Sie den folgenden Befehl ausführen:

   ```powershell
   Install-WindowsFeature -Name HostGuardianServiceRole -IncludeManagementTools -Restart
   ```

2. Nach dem Neustart des HGS-Computers melden Sie sich erneut mit Ihrem Administratorkonto an, öffnen Sie eine Windows PowerShell-Konsole mit erhöhten Rechten, und führen Sie die folgenden Befehle aus, um den Host-Überwachungsdienst zu installieren und dessen Domäne zu konfigurieren. Das hier von Ihnen angegebene Kennwort gilt nur für das Kennwort des Reparaturmodus für Verzeichnisdienste für Active Directory. Das Anmeldekennwort Ihres Administratorkontos wird dadurch nicht geändert. Sie können einen Domänennamen Ihrer Wahl für „-HgsDomainName“ angeben.

   ```powershell
   $adminPassword = ConvertTo-SecureString -AsPlainText '<password>' -Force
   Install-HgsServer -HgsDomainName 'bastion.local' -SafeModeAdministratorPassword $adminPassword -Restart
   ```

3. Nach dem wiederholten Neustart des Computers melden Sie sich mit Ihrem Administratorkonto an (das nun auch ein Domänenadministrator ist), öffnen Sie eine Windows PowerShell-Konsole mit erhöhten Rechten, und konfigurieren Sie den Hostschlüsselnachweis für Ihre HGS-Instanz. 

   ```powershell
   Initialize-HgsAttestation -HgsServiceName 'hgs' -TrustHostKey  
   ```

4. Führen Sie den folgenden Befehl aus, um die IP-Adresse des HGS-Computers zu suchen. Speichern Sie diese IP-Adresse für spätere Schritte.

   ```powershell
   Get-NetIPAddress  
   ```

>[!NOTE]
>Wenn Sie auf Ihren HGS-Computer mit einem DNS-Namen verweisen möchten, können Sie eine Weiterleitung von den DNS-Servern Ihres Unternehmens an den neuen HGS-Domänencontroller einrichten.  

## <a name="step-2-configure-the-sql-server-computer-as-a-guarded-host"></a>Schritt 2: Konfigurieren des SQL Server-Computers als überwachter Host
In diesem Schritt konfigurieren Sie den SQL Server-Computer als überwachten Host, der beim Host-Überwachungsdienst mit Hostschlüsselnachweis registriert ist.
>[!NOTE]
>Der Hostschlüsselnachweis wird nur zur Verwendung in Testumgebungen empfohlen. Für Produktionsumgebungen sollten Sie den TPM-Nachweis verwenden.

1. Melden Sie sich beim SQL Server-Computer als Administrator an, öffnen Sie eine Windows PowerShell-Konsole mit erhöhten Rechten, und installieren Sie die Funktion für überwachten Host, mit der auch Hyper-V installiert wird (sofern nicht bereits installiert).

   ```powershell
   Enable-WindowsOptionalFeature -Online -FeatureName HostGuardian -All
   ```

2. Starten Sie den SQL Server-Computer bei Aufforderung erneut, um die Installation von Hyper-V abzuschließen.
3. Rufen Sie den Wert der folgenden Variablen ab, um den Namen Ihres SQL Server-Computers zu bestimmen.

   ```powershell
   $env:computername 
   ```

4. Melden Sie sich erneut beim SQL Server-Computer als Administrator an, öffnen Sie eine Windows PowerShell-Konsole mit erhöhten Rechten, generieren Sie einen eindeutigen Hostschlüssel, und exportieren Sie den resultierenden öffentlichen Schlüssel in eine Datei.

   ```powershell
   Set-HgsClientHostKey 
   Get-HgsClientHostKey -Path $HOME\Desktop\hostkey.cer
   ```

5. Kopieren Sie die Hostschlüsseldatei, die im vorherigen Schritt generiert wurde, auf den HGS-Computer. Bei den folgenden Anweisungen wird davon ausgegangen, dass der Dateiname „hostkey.cer“ lautet und Sie diese Datei auf Ihren Desktop auf dem HGS-Computer kopieren.
6. Öffnen Sie auf dem HGS-Computer eine Windows PowerShell-Konsole mit erhöhten Rechten, und registrieren Sie den Hostschlüssel Ihres SQL Server-Computers beim Host-Überwachungsdienst:

   ```powershell
   Add-HgsAttestationHostKey -Name <your SQL Server computer name> -Path $HOME\Desktop\hostkey.cer
   ```

7. Führen Sie auf dem SQL Server-Computer den folgenden Befehl in einer Windows PowerShell-Konsole mit erhöhten Rechten aus, um dem SQL Server-Computer den Ort für den Nachweis anzugeben. Vergewissern Sie sich, dass Sie die IP-Adresse oder den DNS-Namen des HSG-Computers angeben. 

   ```powershell
   Set-HgsClientConfiguration -AttestationServerUrl https://<IP address or DNS name>/Attestation -KeyProtectionServerUrl https://<IP address or DNS name>/KeyProtection/  
   ```

Das Ergebnis des oben gezeigten Befehls sollte „AttestationStatus = Passed“ lauten.

Wenn Sie eine Fehlermeldung vom Typ „HostUnreachable“ erhalten, bedeutet dies, dass Ihr SQL Server-Computer nicht mit dem Host-Überwachungsdienst kommunizieren kann. Stellen Sie sicher, dass Sie den HGS Computer pingen können.

Ein Fehler vom Typ „UnauthorizedHost“ weist darauf hin, dass der öffentliche Schlüssel nicht beim HGS-Server registriert wurde. Wiederholen Sie die Schritte 5 und 6, um den Fehler zu beheben.

Wenn andere Fehler auftreten, führen Sie „Clear-HgsClientHostKey“ aus, und wiederholen Sie die Schritte 4 bis 7.

## <a name="step-3-enable-always-encrypted-with-secure-enclaves-in-sql-server"></a>Schritt 3: Aktivieren von Always Encrypted mit Secure Enclaves in SQL Server

In diesem Schritt aktivieren Sie die Funktionen von Always Encrypted mithilfe von Enclaves in Ihrer SQL Server-Instanz.

1. Öffnen Sie SSMS, stellen Sie als „sysadmin“ eine Verbindung mit Ihrer SQL Server-Instanz her, und öffnen Sie ein neues Abfragefenster.
2. Konfigurieren Sie den Secure Enclave-Typ als VBS.

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1
   RECONFIGURE
   ```

3. Starten Sie Ihre SQL Server-Instanz neu, damit die vorherige Änderung übernommen wird. Sie können die Instanz in SSMS neu starten, indem Sie im Objekt-Explorer mit der rechten Maustaste darauf klicken und „Neustart“ auswählen. Stellen Sie nach dem Neustart der Instanz eine neue Verbindung her.

4. Vergewissern Sie sich, dass die Secure Enclave geladen ist, indem Sie die folgende Abfrage ausführen:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```

    Die Abfrage sollte eine Zeile zurückgeben, die wie folgt aussieht:  

    | NAME                           | Wert | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type | 1     | 1              |

5. Um umfangreiche Berechnungen mit verschlüsselten Spalten zu aktivieren, führen Sie die folgende Abfrage aus:

   ```sql
   DBCC traceon(127,-1)
   ```

    > [!NOTE]
    > Umfangreiche Berechnungen sind in [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] standardmäßig deaktiviert. Sie müssen über die oben genannte Anweisung nach jedem Neustart der SQL Server-Instanz aktiviert werden.

## <a name="step-4-create-a-sample-database"></a>Schritt 4: Erstellen einer Beispieldatenbank
In diesem Schritt erstellen Sie eine Datenbank mit einigen Beispieldaten, die Sie später verschlüsseln.

1. Stellen Sie eine Verbindung mit Ihrer SQL Server-Instanz über SSMS her.
2. Erstellen Sie eine neue Datenbank mit dem Namen „ContosoHR“.

    ```sql
    CREATE DATABASE [ContosoHR] COLLATE Latin1_General_BIN2
    ```

3. Vergewissern Sie sich, dass Sie mit der neu erstellten Datenbank verbunden sind. Erstellen Sie eine neue Tabelle mit dem Namen „Employees“.

    ```sql
    CREATE TABLE [dbo].[Employees]
    (
        [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
        [SSN] [char](11) NOT NULL,
        [FirstName] [nvarchar](50) NOT NULL,
        [LastName] [nvarchar](50) NOT NULL,
        [Salary] [money] NOT NULL
    ) ON [PRIMARY]
    GO
    ```

4. Fügen Sie der Tabelle „Employees“ einige Mitarbeiterdatensätze hinzu.

    ```sql
    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('795-73-9838'
            , N'Catherine'
            , N'Abel'
            , $31692)
    GO

    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('990-00-6818'
            , N'Kim'
            , N'Abercrombie'
            , $55415)
    GO
    ```

## <a name="step-5-provision-enclave-enabled-keys"></a>Schritt 5: Bereitstellen Enclave-fähiger Schlüssel

In diesem Schritt erstellen Sie einen Spaltenhauptschlüssel und einen Spaltenverschlüsselungsschlüssel, die Enclave-Berechnungen zulassen.

1. Stellen Sie mit SSMS eine Datenbankverbindung her.
2. Erweitern Sie Ihre Datenbank im **Objekt-Explorer**, und navigieren Sie zu **Sicherheit** > **Always Encrypted-Schlüssel**.
3. Stellen Sie einen neuen Enclave-fähigen Spaltenhauptschlüssel bereit:
    1. Klicken Sie mit der rechten Maustaste auf **Always Encrypted-Schlüssel**, und wählen Sie **Neuer Spaltenhauptschlüssel** aus.
    2. Wählen Sie den Namen des Spaltenhauptschlüssels aus: CMK1.
    3. Stellen Sie sicher, dass Sie entweder **Windows-Zertifikatspeicher (Aktueller Benutzer oder lokaler Computer)** oder **Azure Key Vault** auswählen.
    4. Wählen Sie **Enclave-Berechnungen zulassen**.
    5. Wenn Sie Azure Key Vault ausgewählt haben, melden Sie sich bei Azure an, und wählen Sie Ihren Schlüsseltresor. Weitere Informationen zum Erstellen eines Schlüsseltresors für Always Encrypted finden Sie unter [Verwalten Ihrer Schlüsseltresore im Azure-Portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).
    6. Wählen Sie Ihren Schlüssel aus, wenn er bereits vorhanden ist, oder folgen Sie den Anweisungen auf dem Formular, um einen neuen Schlüssel zu erstellen.
    7. Wählen Sie **OK**.

        ![Enclave-Berechnungen zulassen](encryption/media/always-encrypted-enclaves/allow-enclave-computations.png)

4. Erstellen Sie einen neuen Enclave-fähigen Spaltenverschlüsselungsschlüssel:

    1. Klicken Sie mit der rechten Maustaste auf **Always Encrypted-Schlüssel**, und wählen Sie **Neuer Spaltenverschlüsselungsschlüssel**.
    2. Geben Sie einen Namen für den neuen Spaltenverschlüsselungsschlüssel ein: CEK1.
    3. Wählen Sie in der Dropdownliste **Spaltenhauptschlüssel** den in den vorherigen Schritten erstellten Spaltenhauptschlüssel.
    4. Wählen Sie **OK**.

## <a name="step-6-encrypt-some-columns-in-place"></a>Schritt 6: Direktes Verschlüsseln einiger Spalten

In diesem Schritt verschlüsseln Sie die in den Spalten „SSN“ und „Salary“ gespeicherten Daten in der serverseitigen Enclave und testen dann eine SELECT-Abfrage der Daten.

1. Konfigurieren Sie in SSMS ein neues Abfragefenster mit aktiviertem Always Encrypted für die Datenbankverbindung.
    1. Öffnen Sie in SSMS ein neues Abfragefenster.
    2. Klicken Sie im neuen Abfragefenster mit der rechten Maustaste auf eine beliebige Stelle.
    3. Wählen Sie „Verbindung“ \> „Verbindung ändern“ aus.
    4. Wählen Sie **Optionen** aus. Navigieren Sie zur Registerkarte **Always Encrypted**, wählen Sie **Always Encrypted aktivieren**, und geben Sie die Enclave-Nachweis-URL an.
    5. Wählen Sie **Verbinden**.
2. Konfigurieren Sie in SSMS ein weiteres Abfragefenster mit deaktiviertem Always Encrypted für die Datenbankverbindung.
    1. Öffnen Sie in SSMS ein neues Abfragefenster.
    2. Klicken Sie im neuen Abfragefenster mit der rechten Maustaste auf eine beliebige Stelle.
    3. Wählen Sie „Verbindung“ \> „Verbindung ändern“ aus.
    4. Wählen Sie **Optionen** aus. Navigieren Sie zur Registerkarte **Always Encrypted**, und vergewissern Sie sich, dass **Always Encrypted aktivieren** nicht ausgewählt ist.
    5. Wählen Sie **Verbinden**.
3. Verschlüsseln Sie die Spalten „SSN“ und „Salary“. Fügen Sie im Abfragefenster mit aktiviertem Always Encrypted die folgenden Anweisungen ein, und führen Sie diese aus:

    ```sql
    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [SSN] [char] (11)
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON)
    GO
    DBCC FREEPROCCACHE
    GO

    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [Salary] [money]
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON)
    GO
    DBCC FREEPROCCACHE
    GO
    ```

4. Um zu überprüfen, ob die Spalten „SSN“ und „Salary“ jetzt verschlüsselt sind, fügen Sie die folgende Anweisung im Abfragefenster mit deaktiviertem Always Encrypted ein, und führen Sie die Anweisung aus. Das Abfragefenster sollte verschlüsselte Werte in den Spalten „SSN“ und „Salary“ zurückgeben. Testen Sie im Abfragefenster mit aktiviertem Always Encrypted die gleiche Abfrage, um die Daten entschlüsselt anzuzeigen.

    ```sql
    SELECT * FROM [dbo].[Employees]
    ```

## <a name="step-7-run-rich-queries-against-encrypted-columns"></a>Schritt 7: Ausführen umfangreicher Abfragen für verschlüsselte Spalten

Sie können nun umfangreiche Abfragen für verschlüsselte Spalten ausführen. Ein Teil der Abfrageverarbeitung wird in der serverseitigen Enclave ausgeführt. 

1. Aktivieren Sie die Parametrisierung für Always Encrypted.
    1. Wählen Sie im Hauptmenü von SSMS die Option **Abfrage** aus.
    2. Klicken Sie auf **Abfrageoptionen**.
    3. Navigieren Sie zu **Ausführung** > **Erweitert**.
    4. Aktivieren oder deaktivieren Sie „Parametrisierung für Always Encrypted aktivieren“.
    5. Wählen Sie „OK“ aus.
2. Fügen Sie im Abfragefenster mit aktiviertem Always Encrypted die folgende Abfrage ein, und führen Sie sie aus. Die Abfrage sollte Klartextwerte und Zeilen zurückgeben, die den angegebenen Suchkriterien entsprechen.

    ```sql
    DECLARE @SSNPattern [char](11) = '%6818'
    DECLARE @MinSalary [money] = $1000
    SELECT * FROM [dbo].[Employees]
    WHERE SSN LIKE @SSNPattern AND [Salary] >= @MinSalary;
    ```

## <a name="next-steps"></a>Next Steps
Informationen zu weiteren Anwendungsfällen finden Sie unter [Konfigurieren von Always Encrypted mit Secure Enclaves](encryption/configure-always-encrypted-enclaves.md). Sie können auch Folgendes ausprobieren:

- [Konfigurieren des TPM-Nachweises](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode)
- [Konfigurieren von HTTPS für die HGS-Instanz](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https)
- Entwickeln von Anwendungen, die umfangreiche Abfragen für verschlüsselte Spalten ausgeben
