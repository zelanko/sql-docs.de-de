---
title: 'Lektion 8: Wiederherstellen einer Datenbank in Windows Azure-Speicher | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9e0841c3473baf73033f298cfd3c8402ffc3aa19
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532562"
---
# <a name="lesson-8-restore-a-database-to-windows-azure-storage"></a>Lektion 8: Wiederherstellen einer Datenbank im Windows Azure-Speicher
  In dieser Lektion erfahren Sie, wie Sie eine Sicherungsdatei lokal erstellen und dann im Windows Azure-Speicher wiederherstellen. Ihre Datenbank kann sich entweder in einer lokalen Umgebung oder auf einem virtuellen Computer in Windows Azure befinden. Für diese Lektion müssen Sie Lektion 4, 5, 6 und 7 nicht abschließen.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie verfügen über ein Windows Azure-Speicherkonto.  
  
-   Sie haben einen Container über Ihr Windows Azure-Speicherkonto erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben SQL Server-Anmeldeinformationen auf dem Quellcomputer basierend auf der Shared Access Signature erstellt.  
  
-   Sie haben eine Datenbank auf dem Quellcomputer erstellt.  
  
 Um eine Datenbank im Windows Azure-Speicher wiederherzustellen, können Sie folgende Schritte ausführen:  
  
1.  Starten Sie SQL Server Management Studio auf dem Quellcomputer.  
  
2.  Wenn Sie mit der neu erstellten Datenbank verbunden sind, öffnen Sie das Abfragefenster. Führen Sie die folgende Anweisung aus:  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  Kopieren Sie als Nächstes folgende Anweisungen in das Abfragefenster, und führen Sie sie aus.  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     Am Ende dieses Schritts sollte der Container Daten (.mdf) und Dateien (.ldf) im Verwaltungsportal auflisten.  
  
 Um eine Datenbank mit Daten und Protokolldateien, die auf Windows Azure-Speicher verweisen, mithilfe der SQL Server Management Studio-Benutzeroberfläche wiederherzustellen, führen Sie die folgenden Schritte aus:  
  
1.  In **Objekt-Explorer**, klicken Sie auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie Ihre Datenbank.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Wiederherstellen**.  
  
4.  Auf der **allgemeine** auf der Seite die **wiederherstellen** im quellabschnitt, klicken Sie auf **Quelle** Gerät.  
  
5.  Klicken Sie auf die Schaltfläche zum Durchsuchen für das **Quelle** Textfeld des Geräts, das öffnet die **Sicherungsmedien auswählen** im Dialogfeld.  
  
6.  Wählen Sie in das Textfeld Backup Media **Datei**, und klicken Sie auf die **hinzufügen** um die Sicherungsdatei (bak) zu suchen. Klicken Sie auf **OK**.  
  
7.  Klicken Sie auf **Dateien** auf der ersten Seite.  
  
8.  In der **Datenbankdateien wiederherstellen** Abschnitt unter **wiederherstellen als** Feld, und geben Sie die folgenden Schritte:  
  
     Geben Sie bei einer Datendatei ist: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`. Geben Sie für die Protokolldatei: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")  
  
9. Klicken Sie auf **OK**.  
  
 Wenn die Wiederherstellung abgeschlossen ist, melden Sie sich beim Verwaltungsportal an. Sie sollten in der Lage sein, die .mdf- und .ldf-Dateien im Container wie folgt anzeigen zu können:  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")  
  
 **Nächste Lektion:**  
  
 [Lektion 9: Wiederherstellen einer Datenbank aus Azure Storage](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
