---
title: 'Tutorial: SQL Server-Sicherung und -Wiederherstellung mit dem Azure-BLOB-Speicherdienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a33c2bd47bae8bede7fa71e1654627c123e7cdbc
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874318"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Tutorial: SQL Server-Sicherung und -Wiederherstellung mit dem Azure-BLOB-Speicherdienst
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In diesem Tutorial erfahren Sie, wie Sie Sicherungen in den Azure Blob Storage-Dienst schreiben und daraus wiederherstellen.  In diesem Tutorial erfahren Sie, wie Sie einen Azure Blob-Container und Anmeldeinformationen für den Zugriff auf das Speicherkonto erstellen, eine Sicherung in den Blob-Dienst schreiben und anschließend eine einfache Wiederherstellung ausführen.
  
### <a name="prerequisites"></a>Voraussetzungen  
Um dieses Tutorial abzuschließen, müssen Sie mit den Sicherungs- und Wiederherstellungskonzepten in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und der T-SQL-Syntax vertraut sein. Zur Verwendung dieses Tutorials benötigen Sie ein Azure-Speicherkonto, SQL Server Management Studio (SSMS), Zugriff auf einen Server, auf dem SQL Server ausgeführt wird, und eine AdventureWorks-Datenbank. Darüber hinaus sollte das zum Ausgeben von BACKUP- oder RESTORE-Befehlen verwendete Benutzerkonto Mitglied der Datenbankrolle **db_backupoperator** sein und über Berechtigungen zum **Ändern beliebiger Anmeldeinformationen** verfügen. 

- Erstellen Sie ein kostenloses [Azure-Konto](https://azure.microsoft.com/offers/ms-azr-0044p/).
- Erstellen Sie ein [Azure-Speicherkonto](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=portal).
- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installieren Sie die [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Laden Sie die [AdventureWorks 2016-Beispieldatenbank](https://docs.microsoft.com/sql/samples/adventureworks-install-configure) herunter.
- Weisen Sie das Benutzerkonto der Rolle des [db_backupoperator](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles) zu und gewähren Sie die Berechtigung zum [Ändern beliebiger Anmeldeinformationen](https://docs.microsoft.com/sql/t-sql/statements/alter-credential-transact-sql). 


## <a name="create-azure-blob-container"></a>Erstellen des Azure-Blobcontainers
Ein Container stellt eine Gruppierung eines Blob-Satzes bereit. Alle BLOBs müssen sich in einem Container befinden. Die Anzahl der Container für ein Konto ist unbegrenzt, muss jedoch mindestens 1 betragen. In einem Container kann eine unbegrenzte Anzahl von BLOBs gespeichert werden. 

Führen Sie die folgenden Schritte aus, um einen Container zu erstellen:

1. Öffnen Sie das Azure-Portal. 
1. Navigieren Sie zu Ihrem Speicherkonto. 
   1. Wählen Sie das Speicherkonto aus, und scrollen Sie zu **Blobdienste**.
   1. Wählen Sie **Blobs** und dann +**Container**, um einen neuen Container hinzuzufügen. 
   1. Geben Sie den Namen für den Container ein, und notieren Sie sich diesen. Diese Informationen werden in der URL (Pfad der Sicherungsdatei) der T-SQL-Anweisungen im späteren Verlauf dieses Tutorials verwendet. 
   1. Wählen Sie **OK**. 
    
    ![Neuer Container](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/new-container.png)


  >[!NOTE]
  >Sowohl Sicherungs- als auch Wiederherstellungsvorgänge in SQL Server erfordern eine Authentifizierung beim Speicherkonto. Dies gilt auch, wenn Sie einen öffentlichen Container erstellen. Container können mithilfe der REST-APIs auch programmgesteuert erstellt werden. Weitere Informationen finden Sie unter [Erstellen von Containern](https://docs.microsoft.com/rest/api/storageservices/Create-Container).


## <a name="create-a-sql-server-credential"></a>Erstellen von SQL Server-Anmeldeinformationen
SQL Server-Anmeldeinformationen sind ein Objekt zum Speichern von Authentifizierungsinformationen, die für die Verbindung mit einer Ressource außerhalb von SQL Server erforderlich sind. Hier werden Anmeldeinformationen von SQL Server-Sicherungs- und Wiederherstellungsvorgängen verwendet, um sich beim Windows Azure Blob Storage-Dienst zu authentifizieren. In den Anmeldeinformationen werden der Name des Speicherkontos und der **Zugriffsschlüssel** des Speicherkontos gespeichert. Sobald die Anmeldeinformationen erstellt wurden, müssen sie beim Ausgeben der BACKUP-/RESTORE-Anweisungen in der WITH CREDENTIAL-Option angegeben werden. Weitere Informationen über Anmeldeinformationen finden Sie unter [Anmeldeinformationen](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/credentials-database-engine). 

  >[!IMPORTANT]
  >Die unten beschriebenen Anforderungen für das Erstellen von SQL Server-Anmeldeinformationen sind spezifisch für SQL Server Sicherungsprozesse ([SQL Server Backup to URL](backup-restore/sql-server-backup-to-url.md)und [SQL Server Managed Backup to Microsoft Azure](backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server verwendet beim Zugriff auf Azure-Speicher zum Schreiben oder Lesen von Sicherungen den Namen des Speicherkontos und Informationen zu den Zugriffsschlüsseln.

### <a name="access-keys"></a>Zugriffsschlüssel
Da das Azure-Portal noch geöffnet ist, speichern Sie die Zugriffsschlüssel für das Erstellen der Anmeldeinformationen. 

1. Navigieren Sie zu **Speicherkonto** im Azure-Portal. 
1. Scrollen Sie zu **Einstellungen**, und wählen Sie **Zugriffsschlüssel**. 
1. Speichern Sie sowohl den Schlüssel als auch die Verbindungszeichenfolge, um diese im weiteren Verlauf des Tutorials zu verwenden. 

   ![Zugriffsschlüssel](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/access-keys.png)

### <a name="create-a-sql-server-credential"></a>Erstellen von SQL Server-Anmeldeinformationen
Erstellen Sie mit dem von Ihnen gespeicherten Zugriffsschlüssel die SQL Server-Anmeldeinformationen, indem Sie die folgenden Schritte ausführen. 

1. Stellen Sie über SQL Server Management Studio eine Verbindung zu Ihrem SQL Server her. 
1. Wählen Sie die **AdventureWorks2016**-Datenbank, und öffnen Sie das Fenster **Neue Abfrage**. 
1. Kopieren Sie das folgende Beispiel in das Abfragefenster, und führen Sie es aus. Sie können es nach Bedarf ändern. 

  ```sql
  CREATE CREDENTIAL mycredential   
  WITH IDENTITY= 'msftutorialstorage', -- this is the name of the storage account you specified when creating a storage account   
  SECRET = '<storage account access key>' -- this should be either the Primary or Secondary Access Key for the storage account 
  ```
1. Führen Sie die Anweisung aus, um die Anmeldeinformationen zu erstellen. 

## <a name="backup-database-to-the-windows-azure-blob-storage-service"></a>Speichern der Datenbank im Windows Azure Blob Storage-Dienst
In diesem Abschnitt werden Sie anhand der T-SQL-Anweisung eine vollständige Datenbanksicherung im Windows Azure Blob Storage ausführen. 

1. Stellen Sie über SQL Server Management Studio eine Verbindung zu Ihrem SQL Server her. 
1. Wählen Sie die **AdventureWorks2016**-Datenbank, und öffnen Sie das Fenster **Neue Abfrage**. 
1. Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf: 

 ```sql
 BACKUP DATABASE [AdventureWorks2016] 
 TO URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/ 
 WITH CREDENTIAL = 'mycredential';
 /* name of the credential you created in the previous step */ 
 GO
 ```
1. Führen Sie die Anweisung aus, um Ihre AdventureWorks2016-Datenbank in URL zu sichern. 

 
## <a name="restore-database-from-windows-azure-blob-storage-service"></a>Wiederherstellen der Datenbank aus dem Windows Azure Blob Storage-Dienst
In diesem Abschnitt verwenden Sie eine T-SQL-Anweisung, um die vollständige Datenbanksicherung wiederherzustellen. 

1. Stellen Sie über SQL Server Management Studio eine Verbindung zu Ihrem SQL Server her. 
1. Öffnen Sie das Fenster **Neue Abfrage**. 
1. Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf: 

 ```sql
 RESTORE DATABASE AdventureWorks2016 
 FROM URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 WITH CREDENTIAL = 'mycredential',
 STATS = 5 -- use this to see monitor the progress
 GO
 ``` 

## <a name="see-also"></a>Siehe auch 
Die folgenden Themen werden empfohlen, um das Verständnis der Konzepte und bewährten Verfahren zu verbessern, die Sie bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sicherungen im Azure Blob Storage-Dienst verwenden.  
  
-   [SQL Server-Sicherung und -Wiederherstellung mit dem Microsoft Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
-   [SQL Server-URL-Sicherung – bewährte Methoden und Problembehandlung](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
