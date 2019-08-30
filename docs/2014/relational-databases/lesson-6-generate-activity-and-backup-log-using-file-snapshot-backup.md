---
title: 'Lektion 7: Verschieben der Datendateien in Azure Storage | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85b3395420963e3052caa8eda7e760b9db60bd89
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154990"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a>Lektion 7: Verschieben Sie die Datendateien in Azure Storage
  In dieser Lektion erfahren Sie, wie Sie Ihre Datendateien in Azure Storage (aber nicht in Ihre SQL Server Instanz) verschieben. Für diese Lektion müssen Sie Lektion 4, 5 und 6 nicht abschließen.  
  
 Wenn Sie die Datendateien in Azure Storage verschieben möchten, können Sie `ALTER DATABASE` die-Anweisung verwenden, um den Speicherort der Datendateien zu ändern.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie verfügen über ein Azure Storage Konto.  
  
-   Sie haben unter Ihrem Azure Storage Konto einen Container erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben die SQL Server-Anmeldeinformationen auf dem Quellcomputer erstellt.  
  
 Führen Sie als nächstes die folgenden Schritte aus, um die Datendateien in Azure Storage zu verschieben:  
  
1.  Erstellen Sie zunächst eine Testdatenbank auf dem Quellcomputer, und fügen Sie einige Daten hinzu.  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  Führen Sie den folgenden Code aus:  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  Wenn Sie dies ausführen, wird folgende Meldung angezeigt: "Die Datei" TestDB1Alter "wurde im System Katalog geändert. Der neue Pfad wird beim nächsten Start der Datenbank verwendet. "  
  
4.  Schalten Sie dann die Datenbank offline.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  Nun müssen Sie die Datendateien mit einer der folgenden Methoden in Azure Storage kopieren: [Azcopy-Tool](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx)oder ein Drittanbieter-Speicher-Explorer-Tool.  
  
     **Wichtig:** Wenn Sie diese neue Erweiterung verwenden, stellen Sie immer sicher, dass Sie ein seitenblob und kein blockblob erstellen.  
  
6.  Schalten Sie dann die Datenbank online.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **Nächste Lektion:**  
  
 [Lektion 8: Wiederherstellen einer Datenbank auf Azure Storage](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
