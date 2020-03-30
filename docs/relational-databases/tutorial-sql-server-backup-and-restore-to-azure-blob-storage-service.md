---
title: 'Schnellstart: Sichern und Wiederherstellen im Azure Blob Storage-Dienst'
ms.custom: seo-dt-2019
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: quickstart
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
ms.openlocfilehash: 24847d7b14341e9a1d5a4d874eb0046f53261fea
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "74165523"
---
# <a name="quickstart-sql-backup-and-restore-to-azure-blob-storage-service"></a>Schnellstart: Sicherung und Wiederherstellung von SQL Server mit dem Azure Blob Storage-Dienst
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md](../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]
In diesem Schnellstart erfahren Sie, wie Sie Sicherungen in den Azure Blob Storage-Dienst schreiben und daraus wiederherstellen.  In diesem Artikel wird erläutert, wie Sie einen Azure-Blobcontainer erstellen, eine Sicherung in den Blobdienst schreiben und dann eine Wiederherstellung durchführen.
  
## <a name="prerequisites"></a>Voraussetzungen  
Um diesen Schnellstart abzuschließen, müssen Sie mit den Sicherungs- und Wiederherstellungskonzepten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und der T-SQL-Syntax vertraut sein.  Sie benötigen ein Azure-Speicherkonto, SQL Server Management Studio (SSMS) und Zugriff auf entweder einen Server, auf dem SQL Server ausgeführt wird, oder eine verwaltete Instanz von Azure SQL-Datenbank. Darüber hinaus sollte das zum Ausgeben von BACKUP- oder RESTORE-Befehlen verwendete Benutzerkonto Mitglied der Datenbankrolle **db_backupoperator** sein und über Berechtigungen zum **Ändern beliebiger Anmeldeinformationen** verfügen. 

- Erstellen Sie ein kostenloses [Azure-Konto](https://azure.microsoft.com/offers/ms-azr-0044p/).
- Erstellen Sie ein [Azure-Speicherkonto](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=portal).
- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installieren Sie [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads), oder stellen Sie eine [verwaltete Instanz](/azure/sql-database/sql-database-managed-instance-get-started) mit einer Verbindung bereit, die über eine [Azure SQL-VM](/azure/sql-database/sql-database-managed-instance-configure-vm) oder [ Point-to-Site](/azure/sql-database/sql-database-managed-instance-configure-p2s) hergestellt wurde.
- Weisen Sie das Benutzerkonto der Rolle des [db_backupoperator](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles) zu und gewähren Sie die Berechtigung zum [Ändern beliebiger Anmeldeinformationen](https://docs.microsoft.com/sql/t-sql/statements/alter-credential-transact-sql). 

## <a name="create-azure-blob-container"></a>Erstellen eines Azure-Blobcontainers
Ein Container stellt eine Gruppierung eines Blob-Satzes bereit. Alle BLOBs müssen sich in einem Container befinden. Die Anzahl der Container für ein Speicherkonto ist unbegrenzt, muss jedoch mindestens 1 betragen. In einem Container kann eine unbegrenzte Anzahl von BLOBs gespeichert werden. 

Führen Sie die folgenden Schritte aus, um einen Container zu erstellen:

1. Öffnen Sie das Azure-Portal. 
1. Navigieren Sie zu Ihrem Speicherkonto. 
1. Wählen Sie das Speicherkonto aus, und scrollen Sie zu **Blobdienste**.
1. Wählen Sie **Blobs** und dann **+ Container** aus, um einen neuen Container hinzuzufügen. 
1. Geben Sie den Namen für den Container ein, und notieren Sie sich diesen. Diese Informationen werden in der URL (Pfad der Sicherungsdatei) der T-SQL-Anweisungen im späteren Verlauf dieses Schnellstarts verwendet. 
1. Klicken Sie auf **OK**. 
    
    ![Neuer Container](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/new-container.png)

  > [!NOTE]
  > Sowohl Sicherungs- als auch Wiederherstellungsvorgänge in SQL Server erfordern eine Authentifizierung beim Speicherkonto. Dies gilt auch, wenn Sie einen öffentlichen Container erstellen. Container können mithilfe der REST-APIs auch programmgesteuert erstellt werden. Weitere Informationen finden Sie unter [Erstellen von Containern](https://docs.microsoft.com/rest/api/storageservices/Create-Container).

## <a name="create-a-test-database"></a>Erstellen einer Testdatenbank 
In diesem Schritt erstellen Sie mithilfe von SQL Server Management Studio (SSMS) eine Testdatenbank. 

1. Starten Sie [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md), und stellen Sie eine Verbindung mit Ihrer SQL Server-Instanz her.
1. Öffnen Sie das Fenster **Neue Abfrage**. 
1. Führen Sie den folgenden Transact-SQL-Code (T-SQL-Code) aus, um die Testdatenbank zu erstellen. Aktualisieren Sie den Knoten **Datenbanken** im **Objekt-Explorer**, um Ihre neue Datenbank anzuzeigen. Bei neu erstellten Datenbanken in einer verwalteten Instanz von Azure SQL-Datenbank ist Transparent Data Encryption (TDE) automatisch aktiviert, was deaktiviert werden muss, um fortzufahren. 

```sql
USE [master]
GO

-- Create database
CREATE DATABASE [SQLTestDB]
GO

-- Create table in database
USE [SQLTestDB]
GO
CREATE TABLE SQLTest (
    ID INT NOT NULL PRIMARY KEY,
    c1 VARCHAR(100) NOT NULL,
    dt1 DATETIME NOT NULL DEFAULT getdate()
)
GO

-- Populate table 
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

-- Disable TDE for newly-created databases on a managed instance 
USE [SQLTestDB];
GO
ALTER DATABASE [SQLTestDB] SET ENCRYPTION OFF;
GO
```

## <a name="create-credential"></a>Erstellen von Anmeldeinformationen

Erstellen Sie auf der grafischen Benutzeroberfläche von SQL Server Management Studio die Anmeldeinformationen, indem Sie die folgenden Schritte ausführen. Alternativ können Sie die Anmeldeinformationen auch [programmgesteuert](tutorial-use-azure-blob-storage-service-with-sql-server-2016.md#2---create-a-sql-server-credential-using-a-shared-access-signature) erstellen. 

1. Erweitern Sie im **Objekt-Explorer** von [SQL Server Management Studio(SSMS)](../ssms/download-sql-server-management-studio-ssms.md) den Knoten **Datenbanken**.
1. Klicken Sie mit der rechten Maustaste auf Ihre neue `SQLTestDB`-Datenbank, bewegen Sie den Mauszeiger über **Tasks**, und wählen Sie dann **Sichern...** aus, um den Assistenten **Datenbank sichern** zu starten. 
1. Wählen Sie **URL** in der Dropdownliste **Sichern auf** aus, und klicken Sie dann auf **Hinzufügen**, um das Dialogfeld **Sicherungsziel auswählen** zu öffnen. 

   ![Auf URL sichern](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/back-up-to-url.png)

1. Wählen Sie **Neuer Container** im Dialogfeld **Sicherungsziel auswählen** aus, um das Fenster **Mit einem Microsoft-Abonnement verbinden** zu öffnen. 

   ![Sicherungsziel](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/select-backup-destination.png)

1. Melden Sie sich beim Azure-Portal an, indem Sie auf **Anmelden** klicken und dann den Anmeldevorgang fortsetzen. 
1. Wählen Sie in der Dropdownliste Ihr **Abonnement** aus. 
1. Wählen Sie in der Dropdownliste Ihr **Speicherkonto** aus. 
1. Wählen Sie in der Dropdownliste den zuvor erstellten Container aus. 
1. Wählen Sie **Anmeldeinformationen erstellen** aus, um Ihre *Shared Access Signature (SAS)* zu generieren.  **Speichern Sie diesen Wert, da Sie ihn für die Wiederherstellung benötigen.**

   ![Erstellen von Anmeldeinformationen](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/create-credential.png)

1. Klicken Sie auf **OK**, um das Dialogfeld **Mit einem Microsoft-Abonnement verbinden** zu schließen. Dadurch wird der Wert *Azure-Speichercontainer* im Dialogfeld **Sicherungsziel auswählen** ausgefüllt. Klicken Sie auf **OK**, um den ausgewählten Speichercontainer zu wählen, und schließen Sie das Dialogfeld. 
1. An dieser Stelle können Sie entweder zu Schritt 4 im nächsten Abschnitt übergehen, um die Sicherung der Datenbank durchzuführen, oder den Assistenten **Datenbank sichern** schließen, wenn Sie stattdessen die Sicherung der Datenbank mit Transact-SQL fortsetzen möchten. 


## <a name="back-up-database"></a>Datenbank sichern
In diesem Schritt sichern Sie die Datenbank `SQLTestDB` in Ihrem Azure Blob Storage-Konto, indem Sie entweder die grafische Benutzeroberfläche von SQL Server Management Studio oder Transact-SQL (T-SQL) verwenden. 

# <a name="ssms"></a>[SSMS](#tab/SSMS)

1. Wenn der Assistent **Datenbank sichern** nicht bereits geöffnet ist, erweitern Sie im **Objekt-Explorer** von [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) den Knoten **Datenbanken**.
1. Klicken Sie mit der rechten Maustaste auf Ihre neue `SQLTestDB`-Datenbank, bewegen Sie den Mauszeiger über **Tasks**, und wählen Sie dann **Sichern...** aus, um den Assistenten **Datenbank sichern** zu starten. 
1. Wählen Sie **URL** in der Dropdownliste **Sichern auf** aus, und klicken Sie dann auf **Hinzufügen**, um das Dialogfeld **Sicherungsziel auswählen** zu öffnen. 

   ![Auf URL sichern](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/back-up-to-url.png)

1. Wählen Sie in der Dropdownliste **Azure-Speichercontainer** den Container aus, den Sie im vorherigen Schritt erstellt haben. 

   ![Azure-Speichercontainer](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/azure-storage-container.png)

1. Klicken Sie im Assistenten **Datenbank sichern** auf **OK**, um Ihre Datenbank zu sichern. 
1. Klicken Sie auf **OK**, nachdem Ihre Datenbank erfolgreich gesichert wurde, um alle mit der Sicherung verbundenen Fenster zu schließen. 

   > [!TIP]
   > Sie können die Transact-SQL hinter diesem Befehl als Skript ausgeben, indem Sie **Skript** oben im Assistenten **Datenbank sichern** auswählen: ![Befehl „Skript“](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/script-backup-command.png)


# <a name="transact-sql"></a>[Transact-SQL](#tab/tsql)

Sichern Sie Ihre Datenbank mithilfe von Transact-SQL, indem Sie den folgenden Befehl ausführen: 


```sql
USE [master]

BACKUP DATABASE [SQLTestDB] 
TO  URL = N'https://msftutorialstorage.blob.core.windows.net/sql-backup/sqltestdb_backup_2020_01_01_000001.bak' 
WITH  COPY_ONLY, CHECKSUM
GO
```

---

## <a name="delete-database"></a>Datenbank löschen
In diesem Schritt löschen Sie die Datenbank, bevor Sie die Wiederherstellung durchführen. Dieser Schritt ist nur für die Zwecke dieses Tutorials erforderlich, bei normalen Datenbank-Verwaltungsverfahren aber eher unwahrscheinlich. Sie können diesen Schritt überspringen. Dann müssen Sie jedoch entweder den Namen der Datenbank während der Wiederherstellung in eine verwaltete Instanz ändern oder den Wiederherstellungsbefehl `WITH REPLACE` ausführen, um die Datenbank erfolgreich lokal wiederherzustellen. 

# <a name="ssms"></a>[SSMS](#tab/SSMS)

1. Erweitern Sie im **Objekt-Explorer** den Knoten **Datenbanken**, klicken Sie mit der rechten Maustaste auf die `SQLTestDB`-Datenbank, und wählen Sie „Löschen“ aus, um den Assistenten **Objekt löschen** zu starten. 
1. Klicken Sie bei einer verwalteten Instanz auf **OK**, um die Datenbank zu löschen. Aktivieren Sie lokal das Kontrollkästchen neben **Bestehende Verbindungen schließen**, und klicken Sie dann auf **OK**, um die Datenbank zu löschen. 

# <a name="transact-sql"></a>[Transact-SQL](#tab/tsql)

Löschen Sie die Datenbank, indem Sie den folgenden Transact-SQL-Befehl ausführen:

```sql
USE [master]
GO
DROP DATABASE [SQLTestDB]
GO

-- If connections currently exist on-premises, you'll need to set the database into single user mode first
USE [master]
GO
ALTER DATABASE [SQLTestDB] SET  SINGLE_USER WITH ROLLBACK IMMEDIATE
GO
USE [master]
GO
DROP DATABASE [SQLTestDB]
GO
```

---


## <a name="restore-database"></a>Datenbank wiederherstellen 
In diesem Schritt stellen Sie die Datenbank entweder über die grafische Benutzeroberfläche von SQL Server Management Studio oder mit Transact-SQL wieder her. 

# <a name="ssms"></a>[SSMS](#tab/SSMS)

1. Klicken Sie in SQL Server Management Studio im **Objekt-Explorer** mit der rechten Maustaste auf den Knoten **Datenbanken**, und wählen Sie dann **Datenbank wiederherstellen** aus. 
1. Klicken Sie auf **Gerät** und dann auf die Auslassungspunkte (...), um das Gerät zu wählen. 

   ![Wiederherstellungsgerät auswählen](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/select-restore-device.png)

1. Wählen Sie **URL** in der Dropdownliste **Sicherungsmedientyp** aus, und klicken Sie auf **Hinzufügen**, um Ihr Gerät hinzuzufügen. 

   ![Sicherungsgerät hinzufügen](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/add-backup-device.png)

1. Wählen Sie den Container in der Dropdownliste aus, und fügen Sie dann die Shared Access Signature (SAS) ein, die Sie beim Erstellen der Anmeldeinformationen gespeichert haben. 

   ![Sicherungsziel](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/restore-from-container.png)

1. Klicken Sie auf **OK**, um den Speicherort der Sicherungsdatei auszuwählen. 
1. Erweitern Sie **Container**, und wählen Sie den Container aus, in dem sich Ihre Sicherungsdatei befindet. 
1. Wählen Sie die Sicherungsdatei aus, die Sie wiederherstellen möchten, und klicken Sie dann auf **OK**. Wenn keine Dateien sichtbar sind, verwenden Sie möglicherweise den falschen SAS-Schlüssel. Sie können den SAS-Schlüssel erneut generieren, indem Sie die gleichen Schritte wie zuvor ausführen, um den Container hinzuzufügen. 

   ![Wiederherstellungsdatei auswählen](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/select-restore-file.png)

1. Klicken Sie auf **OK**, um das Dialogfeld **Sicherungsmedien auswählen** zu schließen. 
1. Klicken Sie auf **OK**, um die Datenbank wiederherzustellen. 

# <a name="transact-sql"></a>[Transact-SQL](#tab/tsql)

Um Ihre lokale Datenbank aus Azure Blob Storage wiederherzustellen, ändern Sie den folgenden Transact-SQL-Befehl so, dass Sie Ihr eigenes Speicherkonto verwenden, und führen Sie ihn dann in einem neuen Abfragefenster aus. 

```sql
USE [master]
RESTORE DATABASE [SQLTestDB] FROM 
URL = N'https://msftutorialstorage.blob.core.windows.net/sql-backup/sqltestdb_backup_2020_01_01_000001.bak'
```

---


## <a name="see-also"></a>Weitere Informationen 
Die folgenden Themen werden empfohlen, um das Verständnis der Konzepte und bewährten Verfahren zu verbessern, die Sie bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sicherungen im Azure Blob Storage-Dienst verwenden.  
  
-   [SQL Server-Sicherung und -Wiederherstellung mit Microsoft Azure Blob Storage](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
-   [SQL Server-Sicherung über URLs – bewährte Methoden und Problembehandlung](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
