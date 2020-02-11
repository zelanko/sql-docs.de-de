---
title: 'Lektion 4: Erstellen einer Datenbank in Azure Storage | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ee331966984a12d309e71a7040edac6343e296c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70175628"
---
# <a name="lesson-4-create-a-database-in-azure-storage"></a>Lektion 4: Erstellen einer Datenbank in Azure Storage
  In dieser Lektion erfahren Sie, wie Sie eine Datenbank mithilfe des Features SQL Server Datendateien in Azure erstellen. Vor dieser Lektion müssen Sie Lektion 1, 2 und 3 abschließen. Lektion 3 ist ein sehr wichtiger Schritt, da Sie die Informationen über Ihren Azure-Speicher Container und den zugehörigen Richtlinien Namen und SAS-Schlüssel vor Lektion 4 im SQL Server Anmelde Informationsspeicher speichern müssen.  
  
 Für jeden Speichercontainer, der von einer Daten- oder Protokolldatei verwendet wird, müssen Sie SQL Server-Anmeldeinformationen erstellen, deren Namen mit dem Containerpfad übereinstimmen. Anschließend können Sie eine neue Datenbank in erstellen Azure Storage  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie verfügen über ein Azure Storage Konto.  
  
-   Sie haben unter Ihrem Azure Storage Konto einen Container erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben die SQL Server-Anmeldeinformationen auf dem Quellcomputer erstellt.  
  
 Führen Sie die folgenden Schritte aus, um eine Datenbank in Azure mithilfe der SQL Server Datendateien in Azure Storage zu erstellen:  
  
1.  Stellen Sie eine Verbindung mit SQL Server Management Studio her.  
  
2.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz der installierten Datenbank-Engine her.  
  
3.  Klicken Sie auf der Standardsymbolleiste auf "Neue Abfrage".  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf. Beachten Sie, dass das FILENAME-Feld auf den URI-Pfad der Datenbankdatei im Speichercontainer verweist und mit https beginnen muss.  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     Fügen Sie einige Daten zur Datenbank hinzu.  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  Um die neue Datenbank "TestDB1" auf einem lokalen SQL Server zu sehen, aktualisieren Sie die Datenbanken im Objekt-Explorer.  
  
6.  Um die neu erstellte Datenbank im Speicherkonto anzuzeigen, stellen Sie eine Verbindung mit dem Speicherkonto über SQL Server Management Studio (SSMS) her. Weitere Informationen zum Herstellen einer Verbindung mit einem Azure-Speicher mithilfe SQL Server Management Studio finden Sie in den folgenden Schritten:  
  
    1.  Rufen Sie zunächst die Speicherkontoinformationen ab. Melden Sie sich beim Verwaltungsportal an. Klicken Sie anschließend auf **Speicher** , und wählen Sie Ihr Speicherkonto aus. Wenn ein Speicherkonto ausgewählt ist, klicken Sie unten auf der Seite auf **Zugriffsschlüssel verwalten** . Dadurch wird ein ähnliches Dialogfeld geöffnet:  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")  
  
    2.  Kopieren Sie die Werte für **Speicherkonto Name** und **primärer Zugriffsschlüssel** in das Dialogfeld **mit Azure Storage verbinden** in SSMS. Klicken Sie dann auf **Verbinden**. Die Informationen zu Speicherkontocontainern werden in SSMS angezeigt, wie im folgenden Bildschirmfoto veranschaulicht:  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")  
  
 Der folgende Screenshot zeigt die neu erstellte Datenbank sowohl in der lokalen Umgebung als auch in Azure Storage Umgebung.  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")  
  
 **Hinweis:** Wenn aktive Verweise auf Datendateien in einem Container vorhanden sind, schlagen alle Versuche, die zugeordneten SQL Server Anmelde Informationen zu löschen, fehl. Wenn bereits eine Lease für eine bestimmte Datenbankdatei in einem BLOB vorhanden ist und Sie sie löschen möchten, müssen Sie die Lease auf dem BLOB unterbrechen. Um die Lease zu unterbrechen, können Sie [Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx)verwenden.  
  
 Mit dieser neuen Funktion können Sie SQL Server so konfigurieren, dass jede CREATE DATABASE-Anweisung standardmäßig eine Cloud-fähige Datenbank generiert. Anders ausgedrückt: Sie können Standarddaten und Protokoll Speicherorte in SQL Server Management Studio serverinstanzeigenschaften festlegen, sodass alle Datenbankdateien (MDF-, LDF-Dateien) in Azure Storage als seitenblobs erstellt werden, wenn Sie eine Datenbank erstellen.  
  
 Führen Sie die folgenden Schritte aus, um eine Datenbank in Azure Storage mithilfe SQL Server Management Studio Benutzeroberfläche zu erstellen:  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf "Datenbanken", und klicken Sie dann auf "Neue Datenbank".  
  
3.  Geben Sie im Dialogfeld "Neue Datenbank" einen Datenbanknamen ein.  
  
4.  Zum Ändern der Standardwerte der Primärdaten- und Transaktionsprotokolldateien klicken Sie im Bereich "Datenbankdateien" auf die entsprechende Zelle und geben den neuen Wert ein. Geben Sie auch den Pfad für den Dateispeicherort an. Geben Sie für "Pfad" den URL-Pfad des Speichercontainers ein, wie `https://teststorageaccnt.blob.core.windows.net/testcontainer/`. Geben Sie für "Dateiname" die physischen Dateinamen der Datenbankdateien (.mdf, .ldf) ein.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")  
  
     Weitere Informationen finden Sie unter [Hinzufügen von Daten oder Protokolldateien mit einer Datenbank](databases/add-data-or-log-files-to-a-database.md).  
  
5.  Behalten Sie alle anderen Standardwerte bei.  
  
6.  Klicken Sie auf OK.  
  
 Um die neue Datenbank "TestDB1" auf einem lokalen SQL Server zu sehen, aktualisieren Sie die Datenbanken im Objekt-Explorer. Um die neu erstellte Datenbank im Speicherkonto anzuzeigen, stellen Sie über SQL Server Management Studio (SSMS) eine Verbindung mit dem Speicherkonto her, wie weiter oben in dieser Lektion beschrieben.  
  
 **Nächste Lektion:**  
  
 [Lektion 5. &#40;optional,&#41; Ihre Datenbank mithilfe von TDE zu verschlüsseln.](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
