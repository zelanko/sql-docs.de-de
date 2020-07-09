---
title: Erstellen einer vollständigen Datenbanksicherung | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine vollständige Datenbanksicherung in SQL Server mithilfe von SQL Server Management Studio, Transact-SQL oder PowerShell erstellen.
ms.custom: sqlfreshmay19
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: carlrab
ms.openlocfilehash: d2da7198c2eee8bbbd98ae0951a57fc877d0e367
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748459"
---
# <a name="create-a-full-database-backup"></a>Erstellen einer vollständigen Datenbanksicherung

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder PowerShell eine vollständige Datenbanksicherung erstellen.

Informationen zur SQL Server-Sicherung im Azure Blob Storage-Dienst finden Sie unter [SQL Server-Sicherung und -Wiederherstellung mit dem Microsoft Azure Blob Storage-Dienst](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) und [SQL Server-Sicherung über URLs](../../relational-databases/backup-restore/sql-server-backup-to-url.md).

## <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen

- Die `BACKUP`-Anweisung ist in einer expliziten oder impliziten Transaktion nicht zulässig.
- Sicherungen, die mit aktuelleren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt werden, können in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht wiederhergestellt werden.

Sehen Sie sich eine Übersicht und einen tieferen Einblick in Sicherungskonzepte und -tasks unter [Übersicht über Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md) an, bevor Sie fortfahren.

## <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen

- Wenn eine Datenbank größer wird, ist zum Abschließen von vollständigen Datenbanksicherungen mehr Zeit und mehr Speicherplatz erforderlich. Bei einer großen Datenbank bietet es sich an, eine vollständige Datenbanksicherung durch mehrere [differenzielle Datenbanksicherungen](../../relational-databases/backup-restore/differential-backups-sql-server.md) zu ergänzen.
- Ein Schätzwert der Größe einer vollständigen Datenbanksicherung kann mithilfe der gespeicherten Systemprozedur [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) ermittelt werden.
- Standardmäßig wird bei jedem erfolgreichen Sicherungsvorgang dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und dem Systemereignisprotokoll ein Eintrag hinzugefügt. Wenn Sie regelmäßig eine Sicherung durchführen, kumulieren diese Erfolgsmeldungen schnell und führen so zu großen Fehlerprotokollen! Dadurch kann sich die Suche nach anderen Meldungen erschweren. In solchen Fällen können Sie diese Sicherungsprotokolleinträge mithilfe des Ablaufverfolgungsflags 3226 unterdrücken, wenn keines der Skripts von diesen Einträgen abhängig ist. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).

## <a name="security"></a><a name="Security"></a> Sicherheit

Bei einer Datenbanksicherung ist **TRUSTWORTHY** auf „OFF“ festgelegt. Weitere Informationen zum Festlegen von **TRUSTWORTHY** auf „ON“ finden Sie unter [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).

Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden die **PASSWORD**- und **MEDIAPASSWORD**-Optionen nicht mehr für die Erstellung von Sicherungen verwendet. Sie können jedoch immer noch mit Kennwörtern erstellte Sicherungen wiederherstellen.

## <a name="permissions"></a><a name="Permissions"></a> Berechtigungen

Mitglieder der festen Serverrolle **sysadmin** und der festen Datenbankrollen **db_owner** und **db_backupoperator** verfügen standardmäßig über `BACKUP DATABASE`- und `BACKUP LOG`-Berechtigungen.

 Besitz- und Berechtigungsprobleme im Zusammenhang mit der physischen Datei des Sicherungsmediums können den Sicherungsvorgang beeinträchtigen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst muss über Lese- und Schreibberechtigungen für das Medium verfügen. Das Konto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst ausgeführt wird, muss daher Schreibberechtigungen für das Sicherungsmedium aufweisen. Allerdings prüft die gespeicherte Prozedur [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), die den Systemtabellen einen Eintrag für ein Sicherungsmedium hinzufügt, nicht die Dateizugriffsberechtigungen. Infolgedessen treten solche Probleme mit der physischen Datei des Sicherungsmediums möglicherweise erst auf, wenn auf die physische Ressource zugegriffen wird, um einen Sicherungs- oder Wiederherstellungsvorgang auszuführen.

## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio

> [!NOTE]
> Wenn Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] einen Sicherungstask angeben, können Sie das entsprechende [BACKUP](../../t-sql/statements/backup-transact-sql.md)-Skript von [!INCLUDE[tsql](../../includes/tsql-md.md)] generieren, indem Sie auf die Schaltfläche **Skript** klicken und ein Ziel für das Skript auswählen.

1. Erweitern Sie im **Objekt-Explorer** nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Serverstruktur.

1. Erweitern Sie **Datenbanken**, und wählen Sie eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.

1. Klicken Sie mit der rechten Maustaste auf die Datenbank, die Sie sichern möchten, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Sichern**.

1. Im Dialogfeld **Datenbank sichern** wird in der Dropdownliste die von Ihnen ausgewählte Datenbank (die Sie in jede andere Datenbank auf dem Server ändern können) angezeigt.

1. Wählen Sie in der Dropdownliste **Sicherungstyp** den gewünschten Sicherungstyp aus. Der Standardwert lautet **Vollständig**.

   > [!IMPORTANT]
   > Vor einer differenziellen Sicherung oder einer Transaktionsprotokollsicherung müssen Sie mindestens eine vollständige Datenbanksicherung ausführen.
   
1. Wählen Sie unter **Sicherungskomponente** die Option **Datenbank** aus.

1. Überprüfen Sie im Abschnitt **Ziel** den Standardspeicherort für die Sicherungsdatei (im Ordner ../mssql/data).

   Zur Sicherung auf einem anderen Gerät ändern Sie die Auswahl über die Dropdownliste **Sichern auf**. Wenn Sie die Sicherungsdaten über mehrere Dateien verteilen möchten, damit die Sicherung schneller ausgeführt wird, klicken Sie auf **Hinzufügen**, um zusätzliche Sicherungsobjekte und/oder -ziele hinzuzufügen.
 
   Um einen Sicherungsziel zu entfernen, wählen Sie ihn aus, und klicken Sie auf **Entfernen**. Zum Anzeigen des Inhalts eines vorhandenen Sicherungsziels wählen Sie es aus, und klicken Sie auf **Inhalt**.

1. (Optional) Überprüfen Sie die weiteren verfügbaren Einstellungen auf den Seiten **Medienoptionen** und **Sicherungsoptionen**.

   Weitere Informationen zu den verschiedenen Sicherungsoptionen finden Sie auf der [Seite „Allgemein“](back-up-database-general-page.md), der [Seite „Medienoptionen“](back-up-database-media-options-page.md) und der [Seite „Sicherungsoptionen“](back-up-database-backup-options-page.md).

1. Klicken Sie auf **OK**, um die Sicherung zu initiieren.

1. Wenn die Sicherung erfolgreich abgeschlossen wurde, klicken Sie auf **OK**, um das Dialogfeld „SQL Server Management Studio“ zu schließen.

### <a name="additional-information"></a>Zusätzliche Informationen

- Nach dem Erstellen einer vollständigen Datenbanksicherung können Sie eine [differenzielle Datenbanksicherung](create-a-differential-database-backup-sql-server.md) oder eine [Transaktionsprotokollsicherung](back-up-a-transaction-log-sql-server.md) ausführen.

- (Optional) Sie können das Kontrollkästchen **Kopiesicherung** aktivieren, um eine Kopiesicherung zu erstellen. Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung, die unabhängig von der Sequenz von herkömmlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen erstellt wird. Weitere Informationen finden Sie unter [Kopiesicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md). Für den Sicherungstyp **Differenziell** ist keine Kopiesicherung verfügbar.

- Die Option **Medium überschreiben** ist auf der Seite **Medienoptionen** deaktiviert, wenn Sie unter einer URL sichern.

### <a name="examples"></a>Beispiele

Erstellen Sie für die folgenden Beispiele mit dem folgenden Transact-SQL-Code eine Testdatenbank:

```sql
USE [master]
GO

CREATE DATABASE [SQLTestDB]
GO

USE [SQLTestDB]
GO
CREATE TABLE SQLTest
   (
      ID INT NOT NULL PRIMARY KEY,
      c1 VARCHAR(100) NOT NULL,
      dt1 DATETIME NOT NULL DEFAULT getdate()
   );
GO

USE [SQLTestDB]
GO

INSERT INTO SQLTest (ID, c1) VALUES (1, 'test1')
INSERT INTO SQLTest (ID, c1) VALUES (2, 'test2')
INSERT INTO SQLTest (ID, c1) VALUES (3, 'test3')
INSERT INTO SQLTest (ID, c1) VALUES (4, 'test4')
INSERT INTO SQLTest (ID, c1) VALUES (5, 'test5')
GO

SELECT * FROM SQLTest
GO
```

#### <a name="a-full-back-up-to-disk-to-default-location"></a>A. Vollständige Sicherung auf Datenträger am Standardspeicherort

In diesem Beispiel wird die `SQLTestDB`-Datenbank auf dem Datenträger am standardmäßigen Sicherungsspeicherort gesichert.

1. Erweitern Sie im **Objekt-Explorer** nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Serverstruktur.

1. Erweitern Sie die **Datenbank**, klicken Sie mit der rechten Maustaste auf `SQLTestDB`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .

1. Klicken Sie auf **OK**.

1. Wenn die Sicherung erfolgreich abgeschlossen wurde, klicken Sie auf **OK**, um das Dialogfeld „SQL Server Management Studio“ zu schließen.

![Erstellen einer SQL-Sicherung](media/quickstart-backup-restore-database/backup-db-ssms.png)

#### <a name="b-full-back-up-to-disk-to-non-default-location"></a>B. Vollständige Sicherung auf Datenträger an einem anderen als dem Standardspeicherort

In diesem Beispiel wird die `SQLTestDB`-Datenbank auf dem Datenträger am Speicherort Ihrer Wahl gesichert.

1. Erweitern Sie im **Objekt-Explorer** nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Serverstruktur.

1. Erweitern Sie die **Datenbank**, klicken Sie mit der rechten Maustaste auf `SQLTestDB`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .

1. Wählen Sie auf der Seite **Allgemein** im Abschnitt **Ziel** in der Dropdownliste **Sichern auf:** **Datenträger** aus.

1. Wählen Sie **Entfernen** aus, bis alle vorhandenen Sicherungsdateien entfernt wurden.

1. Wählen Sie **Hinzufügen** aus. Das Dialogfeld **Sicherungsziel auswählen** wird geöffnet.

1. Geben Sie einen gültigen Pfad und Dateinamen in das Textfeld **Dateiname** ein, und verwenden Sie als Erweiterung **.bak**, um die Klassifizierung dieser Datei zu vereinfachen.

1. Klicken Sie auf **OK**, und klicken Sie dann noch mal auf **OK**, um die Sicherung zu initiieren.

1. Wenn die Sicherung erfolgreich abgeschlossen wurde, klicken Sie auf **OK**, um das Dialogfeld „SQL Server Management Studio“ zu schließen.

![Ändern des Datenbankspeicherorts](media/create-a-full-database-backup-sql-server/change-db-location.png)

#### <a name="c-create-an-encrypted-backup"></a>C. Erstellen einer verschlüsselten Sicherung

In diesem Beispiel wird die `SQLTestDB`-Datenbank mit Verschlüsselung am standardmäßigen Sicherungsspeicherort gesichert.

1. Erweitern Sie im **Objekt-Explorer** nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Serverstruktur.

1. Erweitern Sie **Datenbanken** und dann **Systemdatenbanken**, klicken Sie mit der rechten Maustaste auf `master`, und klicken Sie dann auf **Neue Abfrage**, um ein Abfragefenster mit einer Verbindung zu Ihrer `SQLTestDB`-Datenbank zu öffnen.

1. Führen Sie die folgenden Befehle aus, um einen [**Datenbankmasterschlüssel**](../../relational-databases/security/encryption/create-a-database-master-key.md) und ein [**Zertifikat**](../../t-sql/statements/create-certificate-transact-sql.md) in Ihrer `master`-Datenbank zu erstellen.  

   ```sql
   -- Create the master key
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  

   -- If the master key already exists, open it in the same session that you create the certificate (see next step)
   OPEN MASTER KEY DECRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe'

   -- Create the certificate encrypted by the master key
   CREATE CERTIFICATE MyCertificate
   WITH SUBJECT = 'Backup Cert', EXPIRY_DATE = '20201031';  
   ```

1. Klicken Sie im **Objekt-Explorer** im Knoten **Datenbanken** mit der rechten Maustaste auf `SQLTestDB`, zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .

1. Wählen Sie auf der Seite **Medienoptionen** im Abschnitt **Medien überschreiben** die Option **Auf neuen Mediensatz sichern und alle vorhandenen Sicherungssätze löschen** aus.

1. Aktivieren Sie auf der Seite **Sicherungsoptionen** im Abschnitt **Verschlüsselung** das Kontrollkästchen **Sicherung verschlüsseln** .

1. Wählen Sie in der Dropdownliste „Algorithmus“ den Eintrag **AES 256** aus.

1. Wählen Sie in der Dropdownliste **Zertifikat oder asymmetrischer Schlüssel**`MyCertificate`aus.

1. Klicken Sie auf **OK**.

![Verschlüsselte Sicherung](media/create-a-full-database-backup-sql-server/encrypted-backup.png)

#### <a name="d-back-up-to-the-azure-blob-storage-service"></a>D: Sichern im Azure Blob Storage-Dienst

Im nachstehenden Beispiel wird eine vollständige Sicherung der `SQLTestDB`-Datenbank in den Azure Blob Storage-Dienst ausgeführt. Dabei wird in diesem Beispiel davon ausgegangen, dass Sie bereits über ein Speicherkonto mit einem Blobcontainer verfügen. In diesem Beispiel wird eine Shared Access Signature für Sie erstellt. Dies ist nicht möglich, wenn der Container bereits über eine vorhandene Shared Access Signatur verfügt.

Wenn Sie noch keinen Azure-Blobcontainer in einem Speicherkonto haben, erstellen Sie zunächst einen, bevor Sie fortfahren. Weitere Informationen finden Sie unter [Erstellen eines universellen Speicherkontos](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=azure-portal) und [Erstellen eines Containers](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

1. Erweitern Sie im **Objekt-Explorer** nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Serverstruktur.

1. Erweitern Sie die **Datenbank**, klicken Sie mit der rechten Maustaste auf `SQLTestDB`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .

1. Wählen Sie Option **URL** aus der Dropdownliste **Back up to:** (Sichern auf:) auf der Seite **Allgemein** im Abschnitt **Ziel** .

1. Klicken Sie auf **Hinzufügen** , um das Dialogfeld **Sicherungsziel auswählen** zu öffnen.

1. Wenn Sie den Azure-Speichercontainer, den Sie mit SQL Server Management Studio verwenden möchten, zuvor registriert haben, wählen Sie diesen nun aus. Andernfalls klicken Sie auf **Neuer Container**, um einen neuen Container zu registrieren.

1. Melden Sie sich über das Dialogfeld **Verbindung mit einem Microsoft-Abonnement herstellen** bei Ihrem Konto an.

1. Wählen Sie im Dropdown-Textfeld **Speicherkonto auswählen** Ihr Speicherkonto aus.

1. Wählen Sie im Dropdown-Textfeld **Blobcontainer auswählen** Ihren Blobcontainer aus.

1. Wählen Sie im Dropdown-Kalenderfeld **Ablauf der Richtlinie für den gemeinsamen Zugriff** ein Ablaufdatum für die SAS-Richtlinie aus, die Sie in diesem Beispiel erstellen.

1. Klicken Sie auf **Anmeldeinformationen erstellen**, um eine SAS (Shared Access Signature) und Anmeldeinformationen in SQL Server Management Studio zu generieren.

1. Klicken Sie auf **OK**, um das Dialogfeld **Verbindung mit einem Microsoft-Abonnement herstellen** zu schließen.

1. Ändern Sie im Textfeld **Sicherungsdatei** den Namen der Sicherungsdatei (optional).

1. Klicken Sie auf **OK**, um das Dialogfeld **Sicherungsziel auswählen** zu schließen.

1. Klicken Sie auf **OK**, um die Sicherung zu initiieren.

1. Wenn die Sicherung erfolgreich abgeschlossen wurde, klicken Sie auf **OK**, um das Dialogfeld „SQL Server Management Studio“ zu schließen.

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL

Erstellen Sie eine vollständige Datenbanksicherung, indem Sie die `BACKUP DATABASE`-Anweisung ausführen, und geben Sie dabei Folgendes an:

- Den Namen der zu sichernden Datenbank.
- Das Sicherungsmedium, auf das die vollständige Datenbanksicherung geschrieben wird.

Die grundlegende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax zum Erstellen einer vollständigen Datenbanksicherung lautet:

 BACKUP DATABASE *database* TO *backup_device* [ **,** ...*n* ] [ WITH *with_options* [ **,** ...*o* ] ] ;

|Option|BESCHREIBUNG|
|------------|-----------------|
|*database*|Die Datenbank, für die eine Sicherungskopie erstellt werden soll.|
|*Sicherungsmedium* [ **,** ...*n* ]|Gibt eine Liste an, die zwischen 1 und 64 Sicherungsmedien für den Sicherungsvorgang enthalten kann. Sie können ein physisches Sicherungsmedium angeben oder ein entsprechendes logisches Sicherungsmedium, sofern es bereits definiert wurde. Geben Sie das physische Sicherungsmedium mithilfe der Option DISK oder TAPE an:<br /><br /> { DISK &#124; TAPE } **=** _physical\_backup\_device\_name_<br /><br /> Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)aufgezeichnet wurde.|
|WITH *with_options* [ **,** ...*o* ]|Optional geben Sie eine oder mehrere zusätzliche Optionen an, *o*. Weitere Informationen zu einigen der grundlegenden Optionen finden Sie unter Schritt 2.|
|||

Geben Sie optional eine oder mehrere **WITH**-Optionen an. Einige der grundlegenden **WITH**-Optionen werden hier beschrieben. Weitere Informationen zu allen **WITH**-Optionen finden Sie unter [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).

Grundlegender Sicherungssatz von **WITH**-Optionen:

- **{ COMPRESSION | NO_COMPRESSION }** : Nur in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] und höher verfügbar. Gibt an, ob für diese Sicherung eine [Sicherungskomprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md) verwendet wird, wodurch die Standardeinstellung auf Serverebene überschrieben wird.
- **ENCRYPTION (ALGORITHM, SERVER CERTIFICATE | ASYMMETRIC KEY)** : Nur in SQL Server 2014 und höheren Versionen geben Sie den zu verwendenden Verschlüsselungsalgorithmus und das Zertifikat oder den asymmetrischen Schlüssel an, die die Sicherheit bei der Verschlüsselung erhöhen.
- **DESCRIPTION** **=** { **'** _text_ **'**  |  **@** _text\_variable_ }: Gibt den Text an, mit dem der Sicherungssatz beschrieben wird. Die Zeichenfolge kann maximal 255 Zeichen haben.
- **NAME = { *backup_set_name* |  **@** _backup\_set\_name\_var_ }** : Gibt den Namen des Sicherungssatzes an. Namen können maximal 128 Zeichen haben. Wird NAME nicht angegeben, erhält der Sicherungssatz einen leeren Namen.

Standardmäßig fügt `BACKUP` die Sicherung einem vorhandenen Mediensatz an, wobei vorhandene Sicherungssätze beibehalten werden. Verwenden Sie die `NOINIT`-Option, um dies explizit anzugeben. Informationen über das Anfügen an vorhandene Sicherungssätze finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md):

Verwenden Sie alternativ die **FORMAT**-Option, um die Sicherungsmedien zu formatieren:

 FORMAT [ **,** MEDIANAME **=** { *media_name* |  **@** _media\_name\_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* |  **@** _text\_variable_ } ]

 Verwenden Sie die **FORMAT**-Klausel, wenn Sie das Medium das erste Mal einsetzen oder alle vorhandenen Daten überschreiben möchten. Weisen Sie den neuen Medien optional einen Mediennamen und eine Beschreibung zu.

 > [!IMPORTANT]
 > Gehen Sie mit der **FORMAT**-Klausel der `BACKUP`-Anweisung äußerst vorsichtig um, denn sie zerstört alle zuvor auf dem Sicherungsmedium gespeicherten Sicherungen.

### <a name="examples"></a><a name="TsqlExample"></a> Beispiele

Erstellen Sie für die folgenden Beispiele mit dem folgenden Transact-SQL-Code eine Testdatenbank:

```sql
USE [master]
GO

CREATE DATABASE [SQLTestDB]
GO

USE [SQLTestDB]
GO
CREATE TABLE SQLTest (
   ID INT NOT NULL PRIMARY KEY,
   c1 VARCHAR(100) NOT NULL,
   dt1 DATETIME NOT NULL DEFAULT GETDATE()
)
GO

USE [SQLTestDB]
GO

INSERT INTO SQLTest (ID, c1) VALUES (1, 'test1')
INSERT INTO SQLTest (ID, c1) VALUES (2, 'test2')
INSERT INTO SQLTest (ID, c1) VALUES (3, 'test3')
INSERT INTO SQLTest (ID, c1) VALUES (4, 'test4')
INSERT INTO SQLTest (ID, c1) VALUES (5, 'test5')
GO

SELECT * FROM SQLTest
GO
```

#### <a name="a-back-up-to-a-disk-device"></a>A. Sichern auf ein Datenträgermedium

In diesem Beispiel wird die gesamte `SQLTestDB` -Datenbank auf dem Datenträger gesichert, wobei mithilfe von `FORMAT` ein neuer Mediensatz erstellt wird.

```sql
USE SQLTestDB;
GO
BACKUP DATABASE SQLTestDB
TO DISK = 'c:\tmp\SQLTestDB.bak'
   WITH FORMAT,
      MEDIANAME = 'SQLServerBackups',
      NAME = 'Full Backup of SQLTestDB';
GO
```

#### <a name="b-back-up-to-a-tape-device"></a>B. Sichern auf ein Bandmedium

 Im folgenden Beispiel wird die gesamte `SQLTestDB` -Datenbank auf Band gesichert, wobei die Sicherung an vorherige Sicherungen angefügt wird.

```sql
USE SQLTestDB;
GO
BACKUP DATABASE SQLTestDB
   TO TAPE = '\\.\Tape0'
   WITH NOINIT,
      NAME = 'Full Backup of SQLTestDB';
GO
```

#### <a name="c-back-up-to-a-logical-tape-device"></a>C. Sichern auf ein logisches Bandmedium

Im folgenden Beispiel wird ein logisches Sicherungsmedium für ein Bandlaufwerk erstellt. Im Beispiel wird dann die SQLTestDB-Datenbank vollständig auf diesem Gerät gesichert.

```sql
-- Create a logical backup device,
-- SQLTestDB_Bak_Tape, for tape device \\.\tape0.
USE master;
GO
EXEC sp_addumpdevice 'tape', 'SQLTestDB_Bak_Tape', '\\.\tape0'; USE SQLTestDB;
GO
BACKUP DATABASE SQLTestDB
   TO SQLTestDB_Bak_Tape
   WITH FORMAT,
      MEDIANAME = 'SQLTestDB_Bak_Tape',
      MEDIADESCRIPTION = '\\.\tape0',
      NAME = 'Full Backup of SQLTestDB';
GO
```

## <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell

Verwenden Sie das **Backup-SqlDatabase** -Cmdlet. Um ausdrücklich anzugeben, dass dies eine vollständige Datenbanksicherung ist, geben Sie den **-BackupAction**-Parameter mit dessen Standardwert **Database** an. Dieser Parameter ist bei vollständigen Datenbanksicherungen optional.

> [!NOTE]
> Für diese Beispiele wird das SqlServer-Modul benötigt. Führen Sie `Get-Module -Name SqlServer` aus, um festzustellen, ob es installiert ist. Zur Installation dieses Modul führen Sie `Install-Module -Name SqlServer` in einer Administratorsitzung von PowerShell aus.
>
> Weitere Informationen finden Sie unter [SQL Server PowerShell Provider](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).

> [!IMPORTANT]
> Wenn Sie ein PowerShell-Fenster aus SQL Server Management Studio öffnen, um eine Verbindung zu einer Installation von SQL Server herzustellen, können Sie den Teil mit den Anmeldeinformationen in diesem Beispiel weglassen, da Ihre Anmeldeinformationen in SSMS automatisch zum Herstellen der Verbindung zwischen PowerShell und Ihrer SQL Server-Instanz verwendet werden.

### <a name="examples"></a>Beispiele

#### <a name="a-full-backup-local"></a>A. Vollständige Sicherung (lokal)

Im folgenden Beispiel wird eine vollständige Datenbanksicherung der `<myDatabase>` -Datenbank am standardmäßigen Sicherungsspeicherort der Serverinstanz `Computer\Instance`erstellt. Optional wird im Beispiel **-BackupAction Database**angegeben.

Die vollständige Syntax und weitere Beispiele finden Sie unter [Backup-SqlDatabase](https://docs.microsoft.com/powershell/module/sqlserver/backup-sqldatabase).

```powershell
$credential = Get-Credential

Backup-SqlDatabase -ServerInstance Computer[\Instance] -Database <myDatabase> -BackupAction Database -Credential $credential
```

#### <a name="b-full-backup-to-azure"></a>B. Vollständige Sicherung in Azure

Das folgende Beispiel erstellt eine vollständige Sicherung der Datenbank `<myDatabase>` in der `<myServer>`-Instanz im Azure Blob Storage-Dienst. Eine gespeicherte Zugriffsrichtlinie wurde mit Lese-, Schreib-, und Auflistungsrechten erstellt. Die SQL Server Anmeldeinformation `https://<myStorageAccount>.blob.core.windows.net/<myContainer>`wurde mit einer Shared Access Signature (SAS) erstellt, die der gespeicherten Zugriffsrichtlinie zugeordnet ist. Der PowerShell-Befehl verwendet den **BackupFile** -Parameter, um den Speicherort (URL) sowie den Namen der Sicherungsdaten anzugeben.

```powershell
$credential = Get-Credential
$container = 'https://<myStorageAccount>blob.core.windows.net/<myContainer>'
$fileName = '<myDatabase>.bak'
$server = '<myServer>'
$database = '<myDatabase>
$backupFile = $container + '/' + $fileName

Backup-SqlDatabase -ServerInstance $server -Database $database -BackupFile $backupFile -Credential $credential
```

## <a name="related-tasks"></a><a name="RelatedTasks"></a> Related tasks

- [Erstellen einer vollständigen Datenbanksicherung (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
- [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)
- [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)
- [Wiederherstellen einer Datenbanksicherung unter dem einfachen Wiederherstellungsmodell &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)
- [Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)
- [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)
- [Verwenden des Wartungsplanungs-Assistenten](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)

## <a name="see-also"></a>Weitere Informationen

- [Problembehandlung bei der Sicherung von SQL Server und Wiederherstellungsvorgänge](https://support.microsoft.com/kb/224071)
- [Übersicht über Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)
- [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)
- [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)
- [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)
- [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)
- [Datenbank sichern &#40;Seite Allgemein&#41;](../../relational-databases/backup-restore/back-up-database-general-page.md)
- [Datenbank sichern &#40;Seite 'Sicherungsoptionen'&#41;](../../relational-databases/backup-restore/back-up-database-backup-options-page.md)
- [Differenzielle Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)
- [Vollständige Datenbanksicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-database-backups-sql-server.md)
