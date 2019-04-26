---
title: Lektion 5. (Optional) Verschlüsseln Sie Ihre Datenbank mithilfe von TDE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0850fb7b6be85f8052781ca70f97477d5cb3e403
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743306"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>Lektion 5. (Optional) Verschlüsseln Ihrer Datenbank anhand von TDE
  Optional können Sie die neu erstellte Datenbank verschlüsseln. Die transparente Datenverschlüsselung (TDE) führt die E/A-Verschlüsselung und -Entschlüsselung der Daten und der Protokolldateien in Echtzeit durch. Diese Art der Verschlüsselung verwendet einen Verschlüsselungsschlüssel für die Datenbank (Database Encryption Key, DEK), der in der Datenbankstartseite gespeichert wird, damit er während der Wiederherstellung verfügbar ist. Weitere Informationen finden Sie unter [Transparent Data Encryption &#40;TDE&#41; ](security/encryption/transparent-data-encryption.md) und [Verschieben einer TDE-geschützten Datenbank auf einen anderen SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie verfügen über ein Windows Azure-Speicherkonto.  
  
-   Sie haben einen Container über Ihr Windows Azure-Speicherkonto erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben die SQL Server-Anmeldeinformationen auf dem Quellcomputer erstellt.  
  
-   Sie haben eine Datenbank erstellt, indem Sie die Schritte ausgeführt haben, die in Lektion 4 beschrieben werden.  
  
 Wenn Sie eine Datenbank verschlüsseln möchten, führen Sie folgende Schritte aus:  
  
1.  Ändern Sie folgende Anweisungen, und führen Sie sie auf dem Quellcomputer in einem Abfragefenster aus:  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  Verschlüsseln Sie anschließend die neue Datenbank auf dem Quellcomputer, indem Sie folgende Schritte ausführen:  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 Wenn Sie Informationen zum Verschlüsselungsstatus einer Datenbank und zu den ihr zugeordneten Verschlüsselungsschlüsseln erhalten möchten, führen Sie die folgende Anweisung aus:  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 Ausführliche Informationen, die Transact-SQL-Anweisungen, die in dieser Lektion verwendet wurden, finden Sie unter [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), und [sys.dm_database_ Encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).  
  
 **Nächste Lektion:**  
  
 [Lektion 6: Migrieren einer Datenbank aus einer Quelle lokalen zu einem Zielcomputer in Windows Azure](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
