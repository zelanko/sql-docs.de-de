---
title: 'Lektion 9: Wiederherstellen einer Datenbank aus Azure Storage | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 37d8344323add8b9b6f520d59862cdd978823e4f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049772"
---
# <a name="lesson-9-restore-a-database-from-azure-storage"></a>Lektion 9: Wiederherstellen einer Datenbank aus Azure Storage
  In dieser Lektion erfahren Sie, wie Sie eine Daten Bank Sicherungsdatei aus Azure Storage in einer Datenbank wiederherstellen, die sich entweder lokal oder auf einem virtuellen Computer in Azure befindet. Für diese Lektion müssen Sie Lektion 4, 5, 6, 7 und 8 nicht abschließen.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie haben eine Datenbank auf dem Quellcomputer erstellt.  
  
-   Sie haben mithilfe des Features [SQL Server Sicherung und Wiederherstellung mit Azure BLOB Storage Dienst](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) eine Sicherung der-Datenbank (BAK) in Azure Storage erstellt. Beachten Sie, dass Sie in diesem Schritt andere SQL Server-Anmeldeinformationen erstellen müssen. Diese Anmeldeinformationen verwenden Speicherkontoschlüssel.  
  
-   Sie verfügen über ein Azure Storage Konto.  
  
-   Sie haben unter Ihrem Azure Storage Konto einen Container erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben eine SQL Server Anmelde Informationen auf Ihrem Computer erstellt, um Azure Storage-Integrations Feature zu erstellen. Beachten Sie, dass diese Anmeldeinformationen einen Shared Access Signature (SAS)-Schlüssel erfordern.  
  
 Zum Wiederherstellen einer Datenbank aus Azure Storage können Sie die folgenden Schritte ausführen:  
  
1.  Starten Sie SQL Server Management Studio. Stellen Sie eine Verbindung mit der Standardinstanz her.  
  
2.  Klicken Sie auf der Standard Symbolleiste auf **neue Abfrage** .  
  
3.  Kopieren Sie das folgenden komplette Skript, und fügen Sie es in das Abfrage-Fenster ein. Ändern Sie das Skript nach Bedarf.  
  
     **Hinweis:** Sie führen die- `RESTORE` Anweisung aus, um die Datenbanksicherung (BAK) in Azure Storage in einer Daten Bank Instanz auf einem anderen Computer wiederherzustellen.  
  
    ```sql  
  
    USE master   
    GO   
    -- Create a new database to be backed up.   
    CREATE DATABASE TestDbRestoreFrom;   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    SELECT * from dbo.Table1;   
    GO   
    -- Create a credential to be used by SQL Server Backup and Restore with Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Azure Storage.   
    BACKUP DATABASE TestDBRestoreFrom    
    TO URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
          WITH CREDENTIAL = 'BackupCredential'    
         ,COMPRESSION   
         ,STATS = 5;   
    GO    
    -- Create a Shared Access Signature credential   
    CREATE CREDENTIAL [https://teststorageaccnt.blob.core.windows.net/testrestorefrom]   
    WITH IDENTITY='SHARED ACCESS SIGNATURE',   
    SECRET = 'sv=2012-02-12&sr=c&si=policy_resfrom&sig=EhVpzLUXjG4ThAMLmVhrnoiCt8IfmD3BsuYiMawGzxc%3D'   
    GO   
    USE master;   
    GO   
    RESTORE DATABASE TestDBRestoreFrom    
    FROM URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
    WITH    
    CREDENTIAL = 'BackupCredential',    
    REPLACE,   
    MOVE 'TestDBRestoreFrom' TO 'C:\Backup\TestDBRestoreFrom.mdf',     
    MOVE 'TestDBRestoreFrom_log' TO 'C:\Backup\TestDBRestoreFrom_log.ldf';   
    GO  
  
    ```  
  
 **Ende des Tutorials: SQL Server von Datendateien in Azure Storage Dienst**  
  
  
