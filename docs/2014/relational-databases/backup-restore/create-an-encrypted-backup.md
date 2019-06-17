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
ms.openlocfilehash: 3959e998111d5fa45eee45b3d7de35501f86f794
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62876508"
---
# <a name="create-an-encrypted-backup"></a>Erstellen einer verschlüsselten Sicherung
  Dieses Thema beschreibt die Schritte, die notwendig sind, um eine verschlüsselte Sicherung mit Transact-SQL zu erstellen.  
  
## <a name="backup-to-disk-with-encryption"></a>Sicherung auf Datenträger mit Verschlüsselung  
 **Voraussetzungen:**  
  
-   Zugriff auf einen lokalen Datenträger oder Speicher mit ausreichendem Speicherplatz, um eine Sicherung der Datenbank zu erstellen.  
  
-   Ein Datenbank-Hauptschlüssel für die Masterdatenbank und ein Zertifikat oder ein asymmetrischer Schlüssel, das bzw. der für die SQL Server-Instanz verfügbar ist. Informationen zu Verschlüsselungsanforderungen und Berechtigungen finden Sie unter [Backup Encryption](backup-encryption.md).  
  
 Führen Sie die folgenden Schritte aus, um eine verschlüsselte Sicherung einer Datenbank auf einem lokalen Datenträger zu erstellen. In diesem Beispiel wird eine Benutzerdatenbank mit dem Namen MyTestDB verwendet.  
  
1.  **Erstellen Sie eine Datenbank-Hauptschlüssel der Masterdatenbank:** Wählen Sie ein Kennwort aus, mit dem die in der Datenbank gespeicherte Kopie des Datenbank-Hauptschlüssels verschlüsselt wird. Stellen Sie eine Verbindung mit der Datenbank-Engine her, öffnen Sie ein neues Abfragefenster, kopieren Sie das folgende Beispiel, fügen Sie es ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **Erstellen Sie ein Sicherungszertifikat:** Erstellen Sie ein sicherungszertifikat in der master-Datenbank ein. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **Sichern Sie die Datenbank:** Geben Sie den Verschlüsselungsalgorithmus und das zu verwendende Zertifikat. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
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
  
### <a name="backup-to-windows-azure-storage-with-encryption"></a>Sicherung im Windows Azure-Speicher mit Verschlüsselung  
 Wenn Sie eine Sicherung im Windows Azure-Speicher mithilfe der Option **SQL Server-Sicherung über URL** erstellen, sind die Verschlüsselungsschritte die gleichen, aber Sie müssen URL als Ziel und SQL-Anmeldeinformationen verwenden, um sich beim Windows Azure-Speicher zu authentifizieren. Wenn Sie konfigurieren möchten [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] mit Optionen, finden Sie unter [Einrichten von SQL Server Managed Backup für Windows Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) und [zum Einrichten von SQL Server Managed Backup für Windows Azure-Verfügbarkeitsgruppen](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 **Voraussetzungen:**  
  
-   Ein Windows-Speicherkonto und ein Container. Weitere Informationen finden Sie weiter oben unter [Lektion 1: Erstellen von Windows Azure-Speicherobjekten](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).  
  
-   Ein Datenbank-Hauptschlüssel für die Masterdatenbank und ein Zertifikat oder ein asymmetrischer Schlüssel in der SQL Server-Instanz. Informationen zu Verschlüsselungsanforderungen und Berechtigungen finden Sie unter [Backup Encryption](backup-encryption.md).  
  
1.  **SQL Server-Anmeldeinformationen zu erstellen:** Um SQL Server-Anmeldeinformationen zu erstellen, eine Verbindung mit der Datenbank-Engine herstellen, öffnen Sie ein neues Abfragefenster, und kopieren und fügen Sie das folgende Beispiel und klicken Sie auf **Execute**.  
  
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
  
3.  **Erstellen Sie ein Sicherungszertifikat:** Erstellen Sie ein Sicherungszertifikat in der master-Datenbank ein. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **Sichern Sie die Datenbank:** Geben Sie den Verschlüsselungsalgorithmus und das zu verwendende Zertifikat. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
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
  
  
