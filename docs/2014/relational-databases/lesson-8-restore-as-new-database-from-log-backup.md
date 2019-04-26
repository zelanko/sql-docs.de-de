---
title: 'Lektion 9: Wiederherstellen einer Datenbank aus Windows Azure-Speicher | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38d807fae60099022e847e4799196305ccfbadf8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743286"
---
# <a name="lesson-9-restore-a-database-from-windows-azure-storage"></a>Lektion 9: Wiederherstellen einer Datenbank aus dem Windows Azure-Speicher
  In dieser Lektion erfahren Sie, wie Sie eine Datenbanksicherungsdatei vom Windows Azure-Speicher in einer Datenbank wiederherstellen, die sich entweder in einer lokalen Umgebung oder auf einem virtuellen Computer in Windows Azure befindet. Für diese Lektion müssen Sie Lektion 4, 5, 6, 7 und 8 nicht abschließen.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie haben eine Datenbank auf dem Quellcomputer erstellt.  
  
-   Sie haben eine Sicherung der Datenbank (bak) im Windows Azure-Speicher erstellt, mit der [SQL Server-Sicherung und-Wiederherstellung mit dem Windows Azure-Blob-Speicherdienst](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) Feature. Beachten Sie, dass Sie in diesem Schritt andere SQL Server-Anmeldeinformationen erstellen müssen. Diese Anmeldeinformationen verwenden Speicherkontoschlüssel.  
  
-   Sie verfügen über ein Windows Azure-Speicherkonto.  
  
-   Sie haben einen Container über Ihr Windows Azure-Speicherkonto erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben auf dem Computer SQL Server-Anmeldeinformationen für die Windows Azure-Speicherintegration erstellt. Beachten Sie, dass diese Anmeldeinformationen einen Shared Access Signature (SAS)-Schlüssel erfordern.  
  
 Um eine Datenbank aus dem Windows Azure-Speicher wiederherzustellen, können Sie folgende Schritte ausführen:  
  
1.  Starten von SQL Server Management Studio Stellen Sie eine Verbindung mit der Standardinstanz her.  
  
2.  Klicken Sie auf **neue Abfrage** auf der Standardsymbolleiste.  
  
3.  Kopieren Sie das folgenden komplette Skript, und fügen Sie es in das Abfrage-Fenster ein. Ändern Sie das Skript aus, je nach Bedarf.  
  
     **Hinweis**: Sie führen die `RESTORE` Anweisung, um die datenbanksicherung (bak) im Windows Azure-Speicher auf einer Datenbankinstanz auf einem anderen Computer wiederherstellen.  
  
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
    -- Create a credential to be used by SQL Server Backup and Restore with Windows Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Windows Azure Storage.   
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
  
 **Ende des Lernprogramms: SQL Server-Datendateien im Windows Azure Storage-Dienst**  
  
  
