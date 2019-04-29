---
title: 'Lektion 4: Erstellen einer Datenbank in Windows Azure-Speicher | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 465928e8d7fc48785c5774a6bd50f457b0df58b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181994"
---
# <a name="lesson-4-create-a-database-in-windows-azure-storage"></a>Lektion 4: Erstellen einer Datenbank in Microsoft Azure Storage
  In dieser Lektion erfahren Sie, wie Sie eine Datenbank mit der Funktion für SQL Server-Datendateien in Windows Azure erstellen. Vor dieser Lektion müssen Sie Lektion 1, 2 und 3 abschließen. Lektion 3 ist ein sehr wichtiger Schritt, da Sie die Informationen über Ihren Windows Azure-Speichercontainer und den zugehörigen Richtliniennamen und SAS-Schlüssel vor Lektion 4 im SQL Server-Anmeldeinformationsspeicher speichern müssen.  
  
 Für jeden Speichercontainer, der von einer Daten- oder Protokolldatei verwendet wird, müssen Sie SQL Server-Anmeldeinformationen erstellen, deren Namen mit dem Containerpfad übereinstimmen. Anschließend können Sie eine neue Datenbank im Windows Azure-Speicher erstellen.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie verfügen über ein Windows Azure-Speicherkonto.  
  
-   Sie haben einen Container über Ihr Windows Azure-Speicherkonto erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben die SQL Server-Anmeldeinformationen auf dem Quellcomputer erstellt.  
  
 Um eine Datenbank in Windows Azure mithilfe der Funktion für SQL Server-Datendateien im Windows Azure-Speicher zu erstellen, führen Sie folgende Schritte aus:  
  
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
  
6.  Um die neu erstellte Datenbank im Speicherkonto anzuzeigen, stellen Sie eine Verbindung mit dem Speicherkonto über SQL Server Management Studio (SSMS) her. Um Informationen zum Herstellen einer Verbindung mit einem Windows Azure-Speicher unter Verwendung von SQL Server Management Studio zu erhalten, befolgen Sie diese Schritte:  
  
    1.  Rufen Sie zunächst die Speicherkontoinformationen ab. Melden Sie sich beim Verwaltungsportal an. Klicken Sie anschließend auf **Speicher** , und wählen Sie Ihr Speicherkonto aus. Wenn ein Speicherkonto ausgewählt ist, klicken Sie unten auf der Seite auf **Zugriffsschlüssel verwalten** . Dadurch wird ein ähnliches Dialogfeld geöffnet:  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")  
  
    2.  Kopieren Sie die Werte unter **Speicherkontoname** und **Primärer Zugriffsschlüssel** in das Dialogfeld **Mit Windows Azure-Speicher verbinden** in SSMS. Klicken Sie anschließend auf **Verbinden**. Die Informationen zu Speicherkontocontainern werden in SSMS angezeigt, wie im folgenden Bildschirmfoto veranschaulicht:  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")  
  
 Das folgende Bildschirmfoto zeigt die neu erstellte Datenbank in der lokalen Umgebung und in der Windows Azure-Speicherumgebung.  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")  
  
 **Hinweis**: Wenn aktive Verweise auf Datendateien in einem Container wird alle Versuche, die zugeordneten SQL Server-Anmeldeinformationen zu löschen schlägt fehl. Wenn bereits eine Lease für eine bestimmte Datenbankdatei in einem BLOB vorhanden ist und Sie sie löschen möchten, müssen Sie die Lease auf dem BLOB unterbrechen. Um die Lease zu unterbrechen, können Sie [Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx)verwenden.  
  
 Mit dieser neuen Funktion können Sie SQL Server so konfigurieren, dass jede CREATE DATABASE-Anweisung standardmäßig eine Cloud-fähige Datenbank generiert. Das heißt, Sie können Standarddaten und Protokollspeicherorte in SQL Server Management Studio Server-Instanzeigenschaften festlegen. Immer wenn Sie eine Datenbank erstellen, werden dann alle Datenbankdateien (.mdf, .ld) als Seiten-BLOBs im Windows Azure-Speicher erstellt.  
  
 Um eine Datenbank im Windows Azure-Speicher mithilfe der SQL Server Management Studio-Benutzeroberfläche zu erstellen, führen Sie die folgenden Schritte aus:  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf "Datenbanken", und klicken Sie dann auf "Neue Datenbank".  
  
3.  Geben Sie im Dialogfeld "Neue Datenbank" einen Datenbanknamen ein.  
  
4.  Zum Ändern der Standardwerte der Primärdaten- und Transaktionsprotokolldateien klicken Sie im Bereich "Datenbankdateien" auf die entsprechende Zelle und geben den neuen Wert ein. Geben Sie auch den Pfad für den Dateispeicherort an. Geben Sie für "Pfad" den URL-Pfad des Speichercontainers ein, wie `https://teststorageaccnt.blob.core.windows.net/testcontainer/`. Geben Sie für "Dateiname" die physischen Dateinamen der Datenbankdateien (.mdf, .ldf) ein.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")  
  
     Weitere Informationen finden Sie unter [Hinzufügen von Daten- oder Protokolldateien zu einer Datenbank](databases/add-data-or-log-files-to-a-database.md).  
  
5.  Behalten Sie alle anderen Standardwerte bei.  
  
6.  Klicken Sie auf OK.  
  
 Um die neue Datenbank "TestDB1" auf einem lokalen SQL Server zu sehen, aktualisieren Sie die Datenbanken im Objekt-Explorer. Um die neu erstellte Datenbank im Speicherkonto anzuzeigen, stellen Sie über SQL Server Management Studio (SSMS) eine Verbindung mit dem Speicherkonto her, wie weiter oben in dieser Lektion beschrieben.  
  
 **Nächste Lektion:**  
  
 [Lektion 5. &#40;Optional&#41; Verschlüsseln Ihrer Datenbank mithilfe von TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
