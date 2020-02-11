---
title: 'Lektion 8: Wiederherstellen einer Datenbank in Azure Storage | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5b30a9f60f52b8b19875f5fb3c15242ce2c632fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70175424"
---
# <a name="lesson-8-restore-a-database-to-azure-storage"></a>Lektion 8: Wiederherstellen einer Datenbank in Azure Storage
  In dieser Lektion erfahren Sie, wie Sie eine Sicherungsdatei lokal erstellen und anschließend in Azure Storage wiederherstellen. Beachten Sie, dass Sie Ihre Datenbank entweder lokal oder auf einem virtuellen Computer in Azure haben können. Für diese Lektion müssen Sie Lektion 4, 5, 6 und 7 nicht abschließen.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie verfügen über ein Azure Storage Konto.  
  
-   Sie haben unter Ihrem Azure Storage Konto einen Container erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben SQL Server-Anmeldeinformationen auf dem Quellcomputer basierend auf der Shared Access Signature erstellt.  
  
-   Sie haben eine Datenbank auf dem Quellcomputer erstellt.  
  
 Führen Sie die folgenden Schritte aus, um die Azure Storage einer Datenbank wiederherzustellen:  
  
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
  
 Führen Sie zum Wiederherstellen einer Datenbank mit Daten-und Protokolldateien, die auf Azure Storage mithilfe SQL Server Management Studio Benutzeroberfläche verweisen, die folgenden Schritte aus:  
  
1.  Klicken Sie in **Objekt-Explorer**auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie Ihre Datenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Wiederherstellen**.  
  
4.  Klicken Sie auf der Seite **Allgemein** im Abschnitt **Wiederherstellungs** Quelle auf **Quell** Gerät.  
  
5.  Klicken Sie im Textfeld **Quell** Gerät auf die Schaltfläche Durchsuchen, um das Dialogfeld **Sicherungsmedien auswählen** zu öffnen.  
  
6.  Wählen Sie im Textfeld Sicherungsmedien die Option **Datei**aus, und klicken Sie auf die Schaltfläche **Hinzufügen** , um die Sicherungsdatei (. bak) zu suchen. Klicken Sie auf **OK**.  
  
7.  Klicken Sie auf der ersten Seite auf **Dateien** .  
  
8.  Geben Sie im Abschnitt **Datenbankdateien wiederherstellen** als im Feld **Wiederherstellen als** den folgenden Wert ein:  
  
     Geben Sie für Datendatei Folgendes `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`ein:. Geben Sie für Protokolldatei Folgendes `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`ein:.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")  
  
9. Klicken Sie auf **OK**.  
  
 Wenn die Wiederherstellung abgeschlossen ist, melden Sie sich beim Verwaltungsportal an. Sie sollten in der Lage sein, die .mdf- und .ldf-Dateien im Container wie folgt anzeigen zu können:  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")  
  
 **Nächste Lektion:**  
  
 [Lektion 9. Wiederherstellen einer Datenbank aus Azure Storage](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
