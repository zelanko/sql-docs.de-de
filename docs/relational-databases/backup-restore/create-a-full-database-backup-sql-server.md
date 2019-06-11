---
title: Erstellen einer vollständigen Datenbanksicherung (SQL Server) | Microsoft-Dokumentation
ms.custom: sqlfreshmay19
ms.date: 05/29/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
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
manager: craigg
ms.openlocfilehash: c90a3cf1f74eb588bd6faa657a3f47d7e57df453
ms.sourcegitcommit: fc0eb955b41c9c508a1fe550eb5421c05fbf11b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66403056"
---
# <a name="create-a-full-database-backup-sql-server"></a>Erstellen einer vollständigen Datenbanksicherung (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder PowerShell eine vollständige Datenbanksicherung erstellen.  
  

Informationen zur SQL Server-Sicherung im Azure-BLOB-Speicherdienst finden Sie unter [SQL Server-Sicherung und -Wiederherstellung mit dem Microsoft Azure Blob Storage Service](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) und [SQL Server-Sicherung über URLs](../../relational-databases/backup-restore/sql-server-backup-to-url.md):  
  
##  <a name="Restrictions"></a> Einschränkungen  
  
-   Die BACKUP-Anweisung ist nicht in einer expliziten oder implizierten Transaktion zulässig.    
-   Sicherungen, die mit aktuelleren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt werden, können in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht wiederhergestellt werden.   
-   Sehen Sie sich eine Übersicht und einen tieferen Einblick in Sicherungskonzepte und -tasks unter [Übersicht über Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md) an, bevor Sie fortfahren.  
  
## <a name="Recommendations"></a> Empfehlungen  
  
-   Wenn eine Datenbank größer wird, ist zum Abschließen von vollständigen Datenbanksicherungen jedoch mehr Zeit und mehr Speicherplatz erforderlich. Bei einer großen Datenbank bietet es sich an, eine vollständige Datenbanksicherung durch mehrere [differenzielle Datenbanksicherungen](../../relational-databases/backup-restore/differential-backups-sql-server.md) zu ergänzen. Weitere Informationen finden Sie unter [SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md).    
-   Ein Schätzwert der Größe einer vollständigen Datenbanksicherung kann mithilfe der gespeicherten Systemprozedur [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) ermittelt werden.    
-   Standardmäßig wird bei jedem erfolgreichen Sicherungsvorgang dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und dem Systemereignisprotokoll ein Eintrag hinzugefügt. Wenn Sie regelmäßig eine Sicherung durchführen, kumulieren diese Erfolgsmeldungen schnell und führen so zu großen Fehlerprotokollen! Dadurch kann sich die Suche nach anderen Meldungen erschweren. In solchen Fällen können Sie diese Sicherungsprotokolleinträge mithilfe des Ablaufverfolgungsflags 3226 unterdrücken, wenn keines der Skripts von diesen Einträgen abhängig ist. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).  
  
##  <a name="Security"></a> Sicherheit  
 Bei einer Datenbanksicherung ist TRUSTWORTHY auf OFF festgelegt. Weitere Informationen zum Festlegen von TRUSTWORTHY auf ON finden Sie unter [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden die **PASSWORD** - und **MEDIAPASSWORD** -Optionen nicht mehr für die Erstellung von Sicherungen verwendet. Sie können jedoch immer noch mit Kennwörtern erstellte Sicherungen wiederherstellen.  
  
##  <a name="Permissions"></a> Berechtigungen  
 Mitglieder der festen Serverrolle **sysadmin** und der festen Datenbankrollen **db_owner** und **db_backupoperator** verfügen standardmäßig über BACKUP DATABASE- und BACKUP LOG-Berechtigungen.  
  
 Besitz- und Berechtigungsprobleme im Zusammenhang mit der physischen Datei des Sicherungsmediums können den Sicherungsvorgang beeinträchtigen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss **über Lese- und Schreibberechtigungen für das Medium verfügen. Das Konto, unter dem der** -Dienst ausgeführt wird, muss Schreibberechtigungen haben. Allerdings prüft die gespeicherte Prozedur [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), die den Systemtabellen einen Eintrag für ein Sicherungsmedium hinzufügt, nicht die Dateizugriffsberechtigungen. Solche Probleme mit der physischen Datei des Sicherungsmediums treten möglicherweise erst auf, wenn auf die physische Ressource zugegriffen wird, um einen Sicherungs- oder Wiederherstellungsvorgang auszuführen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
>  Wenn Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Sicherungstask angeben, können Sie das entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](../../t-sql/statements/backup-transact-sql.md) -Skript generieren, indem Sie auf die Schaltfläche **Skript** klicken und ein Ziel für das Skript auswählen.  
  
### <a name="back-up-a-database"></a>So sichern Sie eine Datenbank  
  
1.  Klicken Sie nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]im **Objekt-Explorer**auf den Servernamen, um die Serverstruktur zu erweitern.    
1.  Erweitern Sie **Datenbanken**, und wählen Sie eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.    
1.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern**. Das Dialogfeld **Datenbank sichern** wird angezeigt.  
1. Wählen Sie die **Datenbank** aus der Dropdownliste aus. 
1. Wählen Sie in der Dropdownliste **Sicherungstyp** den Wert **Vollständig**aus. 
1. Wählen Sie unter **Sicherungskomponente** die Option **Datenbank** aus. 
1. Verwenden Sie im Abschnitt **Ziel** die Dropdownliste **Sichern auf** aus, um das Sicherungsziel auszuwählen. Klicken Sie auf **Hinzufügen**, um weitere Sicherungsobjekte und/oder -ziele hinzuzufügen. Um einen Sicherungsziel zu entfernen, wählen Sie ihn aus, und klicken Sie auf **Entfernen**. Zum Anzeigen des Inhalts eines vorhandenen Sicherungsziels wählen Sie es aus, und klicken Sie auf **Inhalt**.
1. (Optional) Überprüfen Sie die weiteren verfügbaren Einstellungen auf den Seiten **Medienoptionen** und **Sicherungsoptionen**. Weitere Informationen zu den verschiedenen Sicherungsoptionen finden Sie auf der [Seite „Allgemein“](back-up-database-general-page.md), der [Seite „Medienoptionen“](back-up-database-media-options-page.md) und der [Seite „Sicherungsoptionen“](back-up-database-backup-options-page.md). 



### <a name="additional-information"></a>Zusätzliche Informationen
- Nach dem Erstellen einer vollständigen Datenbanksicherung können Sie eine differenzielle Datenbanksicherung ausführen. Weitere Informationen finden Sie unter [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).  
- Optional können Sie das Kontrollkästchen **Kopiesicherung** aktivieren, um eine Kopiesicherung zu erstellen. Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung, die unabhängig von der Sequenz von herkömmlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen erstellt wird. Weitere Informationen finden Sie unter [Kopiesicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).  Für den Sicherungstyp **Differenziell** ist keine Kopiesicherung verfügbar.  
- Die Option **Medium überschreiben** ist auf der Seite **Medienoptionen** möglicherweise deaktiviert, wenn Sie unter der URL sichern. 


## <a name="ssms-examples"></a>SSMS-Beispiele  

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
    dt1 DATETIME NOT NULL DEFAULT getdate()
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

### <a name="a-full-back-up-to-disk-to-default-location"></a>A. Vollständige Sicherung auf Datenträger am Standardspeicherort
In diesem Beispiel wird die `SQLTestDB`-Datenbank auf dem Datenträger am standardmäßigen Sicherungsspeicherort gesichert.  Es wurde nie eine Sicherung von `SQLTestDB` erstellt.
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie anschließend diese Instanz.
2.  Erweitern Sie die **Datenbank**, klicken Sie mit der rechten Maustaste auf `SQLTestDB`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .
3.  Wählen Sie **OK**.

![Erstellen einer SQL-Sicherung](media/quickstart-backup-restore-database/backup-db-ssms.png) 
 

### <a name="b--full-back-up-to-disk-to-non-default-location"></a>**B.  Vollständige Sicherung auf Datenträger an einem anderen als dem Standardspeicherort**
In diesem Beispiel wird die `SQLTestDB`-Datenbank auf Datenträger unter `F:\MSSQL\BAK` gesichert.  Frühere Sicherungen von `SQLTestDB` wurden erstellt.
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie anschließend diese Instanz.
2.  Erweitern Sie die **Datenbank**, klicken Sie mit der rechten Maustaste auf `Sales`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .
3.  Wählen Sie auf der Seite **Allgemein** im Abschnitt **Ziel** in der Dropdownliste **Sichern auf:** **Datenträger** aus.
4.  Wählen Sie **Entfernen** aus, bis alle vorhandenen Sicherungsdateien entfernt wurden.
5.  Wählen Sie **Hinzufügen** aus. Das Dialogfeld **Sicherungsziel auswählen** wird geöffnet.
6.  Geben Sie `F:\MSSQL\BAK\Sales_20160801.bak` im Textfeld **Dateiname** ein.
7.  Wählen Sie **OK**.
8.  Wählen Sie **OK**.

![Ändern des Datenbankspeicherorts](media/create-a-full-database-backup-sql-server/change-db-location.png)

### <a name="c--create-an-encrypted-backup"></a>**C.  Erstellen einer verschlüsselten Sicherung**
In diesem Beispiel wird die `SQLTestDB`-Datenbank mit Verschlüsselung am standardmäßigen Sicherungsspeicherort gesichert.  

1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie anschließend diese Instanz.
1. Öffnen Sie ein Fenster **Neue Abfrage**, und führen Sie die folgenden Befehle aus, um einen [**Datenbankmasterschlüssel**](../../relational-databases/security/encryption/create-a-database-master-key.md) und ein [**Zertifikat**](../../t-sql/statements/create-certificate-transact-sql.md) in Ihrer `SQLTestDB`-Datenbank zu erstellen. 

    ```sql
    USE [SQLTestDB]
        
    -- Create the database master key
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
    
    
    -- Create the certificate
    CREATE CERTIFICATE MyCertificate   
    ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
    EXPIRY_DATE = '20201031';  
    GO  
    ```

1.  Erweitern Sie **Datenbanken** im **Objekt-Explorer**, klicken Sie mit der rechten Maustaste auf `SQLTestDB`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .
1.  Wählen Sie auf der Seite **Medienoptionen** im Abschnitt **Medien überschreiben** die Option **Auf neuen Mediensatz sichern und alle vorhandenen Sicherungssätze löschen** aus.
1.  Aktivieren Sie auf der Seite **Sicherungsoptionen** im Abschnitt **Verschlüsselung** das Kontrollkästchen **Sicherung verschlüsseln** .
1.  Wählen Sie in der Dropdownliste „Algorithmus“ den Eintrag **AES 256** aus.
1.  Wählen Sie in der Dropdownliste **Zertifikat oder asymmetrischer Schlüssel** `MyCertificate`aus.
1.  Wählen Sie **OK**.

![Verschlüsselte Sicherung](media/create-a-full-database-backup-sql-server/encrypted-backup.png)

### <a name="d--back-up-to-the-azure-blob-storage-service"></a>**D.  Sichern auf den Azure-BLOB-Speicherdienst**


In den drei folgenden Beispielen wird eine vollständige Sicherung der `Sales` -Datenbank in den Microsoft Azure BLOB-Speicherdienst ausgeführt.  Der Speicherkontoname lautet `mystorageaccount`.  Der Container heißt `myfirstcontainer`.  Aus Gründen der Übersichtlichkeit sind die ersten vier Schritte hier einmal aufgelistet und alle Beispiele beginnen mit **Schritt 5**.

1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie anschließend diese Instanz.
2.  Erweitern Sie die **Datenbank**, klicken Sie mit der rechten Maustaste auf `Sales`,zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern...** .
3.  Wählen Sie Option **URL** aus der Dropdownliste **Back up to:** (Sichern auf:) auf der Seite **Allgemein** im Abschnitt **Ziel** .
4.  Klicken Sie auf **Hinzufügen** , um das Dialogfeld **Sicherungsziel auswählen** zu öffnen.

#### <a name="striped-backup-to-url-and-a-sql-server-credential-already-exists"></a>Es sind bereits eine Sicherung im Stripesetformat über URLs und SQL Server-Anmeldeinformationen vorhanden

Eine gespeicherte Zugriffsrichtlinie wurde mit Lese-, Schreib-, und Auflistungsrechten erstellt.  Die SQL Server Anmeldeinformation `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`wurde mit einer Shared Access Signature (SAS) erstellt, die der gespeicherten Zugriffsrichtlinie zugeordnet ist.  

   5.   Wählen Sie `https://mystorageaccount.blob.core.windows.net/myfirstcontainer` aus dem Textfeld **Azure-Speichercontainer:** .
   6.  Geben Sie im Textfeld **Sicherungsdatei:** `Sales_stripe1of2_20160601.bak`ein.
   7.  Klicken Sie auf **OK**.
   8.  Wiederholen Sie die Schritte **4** und **5**.
   9.  Geben Sie im Textfeld **Sicherungsdatei:** `Sales_stripe2of2_20160601.bak`ein.
   10.  Klicken Sie auf **OK**.
   11.   Klicken Sie auf **OK**.

#### <a name="a-shared-access-signature-exists-and-a-sql-server-credential-does-not-exist"></a>Eine Shared Access Signature ist vorhanden und eine SQL Server-Anmeldeinformation ist nicht vorhanden

  5.    Geben Sie `https://mystorageaccount.blob.core.windows.net/myfirstcontainer` in das Textfeld **Azure-Speichercontainer:** ein.  
  6.    Geben Sie die SAS in das Textfeld **Shared Access Signature:** ein.  
  7.    Klicken Sie auf **OK**.  
  8.    Klicken Sie auf **OK**.


#### <a name="a-shared-access-signature-does-not-exist"></a>Es ist keine Shared Access Signature (SAS) vorhanden

  5.    Klicken Sie auf **Neuer Container**. Das Dialogfeld **Verbindung mit einen Microsoft Abonnement herstellen** wird geöffnet.   
  6.    Füllen Sie das Dialogfeld **Verbindung mit einen Microsoft Abonnement herstellen** aus, und klicken Sie anschließend auf **OK** um zum Dialogfeld **Sicherungsziel auswählen** zurückzukehren.  Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einen Microsoft Abonnement](../../relational-databases/backup-restore/connect-to-a-microsoft-azure-subscription.md) .  
  7.    Klicken Sie im Dialogfeld **Sicherungsziel auswählen** auf **OK** .  
  8.    Klicken Sie auf **OK**.

  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
### <a name="create-a-full-database-backup"></a>Erstellen einer vollständigen Datenbanksicherung  
  
1.  Führen Sie die BACKUP DATABASE-Anweisung aus, um die vollständige Datenbanksicherung zu erstellen, und geben Sie dabei Folgendes an:  
  
    -   Den Namen der zu sichernden Datenbank.   
    -   Das Sicherungsmedium, auf das die vollständige Datenbanksicherung geschrieben wird.    
     Die grundlegende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax zum Erstellen einer vollständigen Datenbanksicherung lautet:  
  
     BACKUP DATABASE *database*  
       TO *backup_device* [ **,** ...*n* ]    
     [ WITH *mit_Optionen* [ **,** ...*o* ] ] ;  
  
    |Option|und Beschreibung|  
    |------------|-----------------|  
    |*database*|Die Datenbank, für die eine Sicherungskopie erstellt werden soll.|  
    |*Sicherungsmedium* [ **,** ...*n* ]|Gibt eine Liste an, die zwischen 1 und 64 Sicherungsmedien für den Sicherungsvorgang enthalten kann. Sie können ein physisches Sicherungsmedium angeben oder ein entsprechendes logisches Sicherungsmedium, sofern es bereits definiert wurde. Geben Sie das physische Sicherungsmedium mithilfe der Option DISK oder TAPE an:<br /><br /> { DISK &#124; TAPE } **=** _physical\_backup\_device\_name_<br /><br /> Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)aufgezeichnet wurde.|  
    |WITH *with_options* [ **,** ...*o* ]|Optional geben Sie eine oder mehrere zusätzliche Optionen an, *o*. Weitere Informationen zu einigen der grundlegenden Optionen finden Sie unter Schritt 2.|  
  
2.  Geben Sie optional eine oder mehrere WITH-Optionen an. Einige der grundlegenden WITH-Optionen werden hier beschrieben. Weitere Informationen zu allen WITH-Optionen finden Sie unter [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md):  

Grundlegender Sicherungssatz von WITH-Optionen:

- **{ COMPRESSION | NO_COMPRESSION }** : Nur in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] und höher verfügbar. Gibt an, ob für diese Sicherung eine [Sicherungskomprimierung](../../relational-databases/backup-restore/backup-compression-sql-server.md) verwendet wird, wodurch die Standardeinstellung auf Serverebene überschrieben wird. 
- **ENCRYPTION (ALGORITHM, SERVER CERTIFICATE |ASYMMETRIC KEY)** : Nur in SQL Server 2014 und höheren Versionen geben Sie den zu verwendenden Verschlüsselungsalgorithmus und das Zertifikat oder den asymmetrischen Schlüssel an, die die Sicherheit bei der Verschlüsselung erhöhen.
- **DESCRIPTION** **=** { **'** _text_ **'**  |  **@** _text\_variable_ }: Gibt den Text an, mit dem der Sicherungssatz beschrieben wird. Die Zeichenfolge kann maximal 255 Zeichen haben.  
- **NAME = { *backup_set_name* |  **@** _backup\_set\_name\_var_ }** : Gibt den Namen des Sicherungssatzes an. Namen können maximal 128 Zeichen haben. Wird NAME nicht angegeben, erhält der Sicherungssatz einen leeren Namen. 
  
 
Standardmäßig fügt BACKUP die Sicherung einem vorhandenen Mediensatz an, wobei vorhandene Sicherungssätze beibehalten werden. Verwenden Sie die NOINIT-Option, um dies explizit anzugeben. Informationen über das Anfügen an vorhandene Sicherungssätze finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md):  

Verwenden Sie alternativ die FORMAT-Option, um die Sicherungsmedien zu formatieren:  

FORMAT [ **,** MEDIANAME **=** { *media_name* |  **@** _media\_name\_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* |  **@** _text\_variable_ } ]  
Verwenden Sie die FORMAT-Klausel, wenn Sie das Medium das erste Mal einsetzen oder alle vorhandenen Daten überschreiben möchten. Weisen Sie den neuen Medien optional einen Mediennamen und eine Beschreibung zu.  

> [!IMPORTANT]  
>  Gehen Sie mit den FORMAT- und INIT-Klauseln der BACKUP-Anweisung äußerst vorsichtig um, denn sie zerstören alle zuvor auf dem Sicherungsmedium gespeicherten Sicherungen.  
  
##  <a name="TsqlExample"></a> Transact-SQL-Beispiele  
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
    dt1 DATETIME NOT NULL DEFAULT getdate()
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
  
#### <a name="a-back-up-to-a-disk-device"></a>**A. Sichern auf ein Datenträgermedium**  
 In diesem Beispiel wird die gesamte `SQLTestDB` -Datenbank auf dem Datenträger gesichert, wobei mithilfe von `FORMAT` ein neuer Mediensatz erstellt wird.  
  
```sql  
USE SQLTestDB;  
GO  
BACKUP DATABASE SQLTestDB  
TO DISK = 'Z:\SQLServerBackups\SQLTestDB.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of SQLTestDB';  
GO  
```  
  
#### <a name="b-back-up-to-a-tape-device"></a>**B. Sichern auf ein Bandmedium**  
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
  
#### <a name="c-back-up-to-a-logical-tape-device"></a>**C. Sichern auf ein logisches Bandmedium**  
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
  
##  <a name="PowerShellProcedure"></a> PowerShell  
Verwenden Sie das **Backup-SqlDatabase** -Cmdlet. Um ausdrücklich anzugeben, dass dies eine vollständige Datenbanksicherung ist, geben Sie den **-BackupAction**  -Parameter mit dessen Standardwert **Database**an. Dieser Parameter ist bei vollständigen Datenbanksicherungen optional.  

## <a name="powershell-examples"></a>PowerShell-Beispiele

### <a name="a--full-local-backup"></a>A.  Vollständige lokale Sicherung 
Im folgenden Beispiel wird eine vollständige Datenbanksicherung der `MyDB` -Datenbank am standardmäßigen Sicherungsspeicherort der Serverinstanz `Computer\Instance`erstellt. Optional wird im Beispiel **-BackupAction Database** angegeben.  
```powershell 
Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
```
 
### <a name="b--full-backup-to-microsoft-azure"></a>B.  Vollständige Sicherung für Microsoft Azure 
Das folgende Beispiel erstellt eine vollständige Sicherung der Datenbank `Sales` in der `MyServer`-Instanz an den Microsoft Azure BLOB-Speicherdienst.  Eine gespeicherte Zugriffsrichtlinie wurde mit Lese-, Schreib-, und Auflistungsrechten erstellt.  Die SQL Server Anmeldeinformation `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`wurde mit einer Shared Access Signature (SAS) erstellt, die der gespeicherten Zugriffsrichtlinie zugeordnet ist.  Der PowerShell-Befehl verwendet den **BackupFile** -Parameter, um den Speicherort (URL) sowie den Namen der Sicherungsdaten anzugeben.

```powershell  
import-module sqlps;
$container = 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer';
$FileName = 'Sales.bak';
$database = 'Sales';
$BackupFile = $container + '/' + $FileName ;
  
Backup-SqlDatabase -ServerInstance "MyServer" -Database $database -BackupFile $BackupFile;
```
 
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer vollständigen Datenbanksicherung (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
-   [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)
-   [Wiederherstellen einer Datenbanksicherung unter dem einfachen Wiederherstellungsmodell &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)
-   [Wiederherstellen einer Datenbank bis zum Fehlerzeitpunkt im vollständigen Wiederherstellungsmodell &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)
-   [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)
-   [Verwenden des Wartungsplanungs-Assistenten](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a>Siehe auch  
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
  
  
