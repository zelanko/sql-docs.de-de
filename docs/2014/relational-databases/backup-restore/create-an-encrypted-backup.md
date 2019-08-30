---
title: Erstellen einer verschlüsselten Sicherung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b2f16425978b1e6ddc560aabd445b6cfe6737b57
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154756"
---
# <a name="create-an-encrypted-backup"></a>Erstellen einer verschlüsselten Sicherung
  Dieses Thema beschreibt die Schritte, die notwendig sind, um eine verschlüsselte Sicherung mit Transact-SQL zu erstellen.  
  
## <a name="backup-to-disk-with-encryption"></a>Sicherung auf Datenträger mit Verschlüsselung  
 **Voraussetzungen:**  
  
-   Zugriff auf einen lokalen Datenträger oder Speicher mit ausreichendem Speicherplatz, um eine Sicherung der Datenbank zu erstellen.  
  
-   Ein Datenbank-Hauptschlüssel für die Masterdatenbank und ein Zertifikat oder ein asymmetrischer Schlüssel, das bzw. der für die SQL Server-Instanz verfügbar ist. Informationen zu Verschlüsselungsanforderungen und Berechtigungen finden Sie unter [Backup Encryption](backup-encryption.md).  
  
 Führen Sie die folgenden Schritte aus, um eine verschlüsselte Sicherung einer Datenbank auf einem lokalen Datenträger zu erstellen. In diesem Beispiel wird eine Benutzerdatenbank mit dem Namen MyTestDB verwendet.  
  
1.  **Erstellen eines Datenbankhauptschlüssels der Masterdatenbank:** Wählen Sie ein Kennwort aus, mit dem die in der Datenbank gespeicherte Kopie des Datenbank-Hauptschlüssels verschlüsselt wird. Stellen Sie eine Verbindung mit der Datenbank-Engine her, öffnen Sie ein neues Abfragefenster, kopieren Sie das folgende Beispiel, fügen Sie es ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **Erstellen eines Sicherungszertifikats:** Erstellen Sie ein Sicherungszertifikat in der Masterdatenbank. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **Sichern der Datenbank:** Geben Sie den Verschlüsselungsalgorithmus und das Zertifikat an, das verwendet werden soll. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 Ein Beispiel zum Verschlüsseln einer durch EKM geschützten Sicherung finden Sie unter [Erweiterbare Schlüsselverwaltung mit Azure Key Vault &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
### <a name="backup-to-azure-storage-with-encryption"></a>Sicherung in Azure Storage mit Verschlüsselung  
 Wenn Sie eine Sicherung im Azure-Speicher mithilfe der Option **SQL Server Backup to URL** erstellen, sind die Verschlüsselungs Schritte identisch, aber Sie müssen URL als Ziel und SQL-Anmelde Informationen verwenden, um sich beim Azure-Speicher zu authentifizieren. Wenn Sie mit Verschlüsselungsoptionen [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfigurieren möchten, finden Sie weitere Informationen unter [Einrichten SQL Server verwalteten Sicherung in Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) und [Einrichten SQL Server verwalteten Sicherung in Azure für Verfügbarkeits Gruppen](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 **Voraussetzungen:**  
  
-   Ein Windows-Speicherkonto und ein Container. Weitere Informationen finden Sie weiter oben unter [Lektion 1: Erstellen Sie Azure Storage](../../tutorials/lesson-1-create-windows-azure-storage-objects.md)Objekte.  
  
-   Ein Datenbank-Hauptschlüssel für die Masterdatenbank und ein Zertifikat oder ein asymmetrischer Schlüssel in der SQL Server-Instanz. Informationen zu Verschlüsselungsanforderungen und Berechtigungen finden Sie unter [Backup Encryption](backup-encryption.md).  
  
1.  **Erstellen von SQL Server-Anmeldeinformationen:** Um SQL Server-Anmeldeinformationen zu erstellen, stellen Sie zunächst eine Verbindung mit der Datenbank-Engine her. Öffnen Sie dann ein neues Abfragefenster, kopieren Sie das folgende Beispiel, fügen Sie es ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **Erstellen Sie einen Datenbank-Hauptschlüssel:** Wählen Sie ein Kennwort aus, mit dem die in der Datenbank gespeicherte Kopie des Datenbank-Hauptschlüssels verschlüsselt wird. Stellen Sie eine Verbindung mit der Datenbank-Engine her, öffnen Sie ein neues Abfragefenster, kopieren Sie das folgende Beispiel, fügen Sie es ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **Erstellen eines Sicherungszertifikats:** Erstellen Sie ein Sicherungszertifikat in der Masterdatenbank. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **Sichern der Datenbank:** Geben Sie den Verschlüsselungsalgorithmus und das Zertifikat an, das verwendet werden soll. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
