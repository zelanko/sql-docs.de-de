---
title: 'Lektion 2: Definieren einer Datenverbindung und einer Datentabelle für den übergeordneten Bericht | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 987e6924fe3fbffb416e4266861ae7cfede16596
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66108494"
---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a>Lektion 2: Definieren einer Datenverbindung und einer Datentabelle für den übergeordneten Bericht
  Nachdem Sie ein neues Websiteprojekt mithilfe der ASP.NET-Websitevorlage für Visual C# erstellt haben, erstellen Sie im nächsten Schritt eine Datenverbindung und eine Datentabelle für den übergeordneten Bericht. In diesem Lernprogramm wird eine Datenverbindung mit der AdventureWorks2008-Datenbank hergestellt. Alternativ können Sie auch eine Verbindung mit der AdventureWorks2012-Datenbank herstellen.  
  
### <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a>So definieren Sie eine Datenverbindung und eine Datentabelle durch Hinzufügen eines Datasets (für den übergeordneten Bericht)  
  
1.  Wählen Sie im Menü **Website** die Option **Neues Element hinzufügen**aus.  
  
2.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **DataSet** , und klicken Sie auf **hinzufügen**. Wenn Sie aufgefordert werden, sollten Sie das Element, das Hinzufügen der **"App_Code"** Ordner durch Klicken auf **Ja**.  
  
     Dadurch wird dem Projekt die neue XSD-Datei **DataSet1.xsd** hinzugefügt und der DataSet-Designer geöffnet.  
  
3.  Ziehen Sie ein **[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** -Steuerelement aus der Toolbox auf die Entwurfsoberfläche. Dadurch wird der Konfigurations-Assistent **TableAdapter** gestartet.  
  
4.  Klicken Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** auf **Neue Verbindung**.  
  
5.  Wenn Sie zum ersten Mal eine Datenquelle in Visual Studio erstellen, wird die Seite **Datenquelle auswählen** angezeigt. Wählen Sie im Feld **Datenquelle** die Option **Microsoft SQL Server**aus.  
  
6.  Führen Sie im Dialogfeld **Verbindung hinzufügen** die folgenden Schritte aus:  
  
    1.  Geben Sie im Feld **Servername** den Server ein, auf dem sich die Datenbank **AdventureWorks2008** befindet.  
  
         Die SQL Server Express-Standardinstanz lautet **(local)\sqlexpress**.  
  
    2.  Wählen Sie im Abschnitt **Am Server anmelden** die Option aus, die Ihnen den Zugriff auf die Daten ermöglicht. Die Standardeinstellung ist**Windows-Authentifizierung verwenden** .  
  
    3.  Von der **auswählen oder Eingeben eines Datenbanknamens** Dropdown-Liste, klicken Sie auf **AdventureWorks2008**.  
  
    4.  Klicken Sie auf **OK**, und klicken Sie dann auf **Weiter**.  
  
7.  Wenn Sie in Schritt 6 (b) **SQL Server-Authentifizierung verwenden** ausgewählt haben, legen Sie fest, ob die vertraulichen Daten in die Zeichenfolge eingeschlossen oder ob die Informationen im Anwendungscode festgelegt werden sollen.  
  
8.  Geben Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** den Namen der Verbindungszeichenfolge ein, oder übernehmen Sie den Standardwert **AdventureWorks2008ConnectionString**. Klicken Sie auf **Weiter**.  
  
9. Wählen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** die Option **SQL-Anweisungen verwenden**aus, und klicken Sie auf **Weiter**.  
  
10. Auf der **Geben Sie eine SQL-Anweisung** geben die folgende Transact-SQL-Abfrage zum Abrufen von Daten aus der **AdventureWorks2008** Datenbank, und klicken Sie dann auf **Weiter**.  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
     Sie können die Abfrage auch erstellen, indem Sie auf **Abfragegenerator**, und klicken Sie dann überprüfen Sie die Abfrage, indem Sie auf **Abfrage ausführen**. Wenn die Abfrage nicht die erwarteten Daten zurückgibt, verwenden Sie möglicherweise eine frühere Version von AdventureWorks. Weitere Informationen zum Installieren der **AdventureWorks2008** -Version von AdventureWorks finden Sie unter [Exemplarische Vorgehensweise: Installieren der AdventureWorks-Datenbank](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).  
  
11. Auf der **zu generierende Methode auswählen** Seite, deaktivieren **Methoden erstellen, um Updates direkt an die Datenbank (GenerateDBDirectMethods) senden**, und klicken Sie dann auf **Fertig stellen**.  
  
    > [!WARNING]  
    >  Die Option Erstellen muss deaktiviert sein.  
  
     Die Konfiguration des ADO.NET DataTable-Objekts als Datenquelle für Ihren Bericht ist jetzt abgeschlossen. Auf der DataSet-Designer-Seite in Visual Studio sollte das hinzugefügte DataTable-Objekt jetzt mit den in der Abfrage angegebenen Spalten aufgeführt werden. DataSet1 enthält die Daten aus der Product-Tabelle basierend auf der Abfrage.  
  
12. Speichern Sie die Datei.  
  
13. Um die Daten in der Vorschau anzuzeigen, klicken Sie im Menü **Daten** auf **Datenvorschau** , und klicken Sie dann auf **Vorschau**.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben erfolgreich eine Datenverbindung und eine Datentabelle für den übergeordneten Bericht erstellt. Als Nächstes erstellen Sie den übergeordneten Bericht mithilfe des Berichts-Assistenten.  
  
  
