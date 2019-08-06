---
title: Installieren von Analysis Services Beispiel Daten und-Projekten | Microsoft-Dokumentation
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c89ee3edf9338c4f74b0738d930ee74dbec7244
ms.sourcegitcommit: bcc3b2c7474297aba17b7a63b17c103febdd0af9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68794979"
---
# <a name="install-sample-data-and-multidimensional-projects"></a>Installieren von Beispiel Daten und mehrdimensionalen Projekten 
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

Verwenden Sie die Anweisungen und Links in diesem Artikel, um die Daten-und Projektdateien zu installieren, die in den Analysis Services-Tutorials verwendet werden. 
  
## <a name="step-1-install-prerequisites"></a>Schritt 1: Installieren der erforderlichen Komponenten 
In den Lektionen dieses Lernprogramms wird vorausgesetzt, dass Sie folgende Software installiert haben. Sie können alle-Funktionen auf einem einzelnen Computer installieren. Um diese Funktionen zu installieren, führen Sie SQL Server-Setup aus, und wählen Sie auf der Seite Funktionsauswahl diese Funktionen aus.  
  
-   SQL Server-Datenbank-Engine  
  
-   SQL Server Analysis Services (SSAS) 
  
    Analysis Services ist nur in diesen Editionen verfügbar: Evaluation, Enterprise, Business Intelligence, Standard. Mehrdimensionale Modelle werden in Azure Analysis Services nicht unterstützt.
  
    Standardmäßig wird Analysis Services 2016 und höher als tabellarische Instanz installiert, die Sie überschreiben können, indem Sie auf der Seite Server Konfiguration des Installations-Assistenten auf der Seite Serverkonfiguration die Option mehrdimensionaler Server Modus auswählen.
  
## <a name="step-2-download-and-install-developer-and-management-tools"></a>Schritt 2: Herunterladen und Installieren von Entwickler-und Verwaltungs Tools
SQL Server Data Tools (SSDT) für Visual Studio wird separat von anderen SQL Server Features heruntergeladen und installiert. Die zum Erstellen von BI-Modellen und-Berichten verwendeten Designer und Projektvorlagen sind in SSDT für Visual Studio 2015 oder [nuget-Pakete](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) für Visual Studio 2017 enthalten.  
  
[Laden Sie SQL Server Data Tools (SSDT) herunter](http://go.microsoft.com/fwlink/?LinkID=827542).   

SQL Server Management Studio (SSMS) wird separat von anderen SQL Server Features heruntergeladen und installiert.  

[Hier können Sie SQL Server Management Studio herunterladen](../../ssms/download-sql-server-management-studio-ssms.md)  

Sie können Excel optional installieren, um mehrdimensionale Daten zu durchsuchen, während Sie das Lernprogramm ausführen. Durch die Installation von Excel wird die Funktion **In Excel analysieren** aktiviert. Diese startet Excel mit einer PivotTable-Feldliste, die mit dem Cube verbunden ist, den Sie erstellen. Es wird empfohlen, zum Durchsuchen von Daten Excel zu verwenden, da Sie schnell einen Pivotbericht erstellen können, der Ihnen das Interagieren mit den Daten ermöglicht.  
  
Alternativ können Sie Daten mithilfe des integrierten MDX-Abfrage-Designers durchsuchen, der in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] integriert ist. Der Abfrage-Designer gibt die gleichen Daten zurück, jedoch werden die Daten als flaches Rowset dargestellt.  
  
## <a name="step-3-install-databases"></a>Schritt 3: Installieren von Datenbanken  
In einem mehrdimensionalen Analysis Services-Modell werden Transaktionsdaten verwendet, die Sie aus einem Managementsystem für relationale Datenbanken importieren. Im Rahmen dieses Tutorials verwenden Sie die folgende relationale Datenbank als Datenquelle.  
  
-   **AdventureWorksDW2012 oder** höher: Dies ist eine relationale Data Warehouse, die auf einer Datenbank-Engine-Instanz ausgeführt wird. Es enthält die ursprünglichen Daten, die von den Analysis Services-Datenbanken und-Projekten verwendet werden, die Sie im gesamten Tutorial erstellen und bereitstellen. In diesem Tutorial wird davon ausgegangen, dass Sie AdventureWorksDW2012 verwenden. spätere Versionen funktionieren jedoch nicht.
  
    Sie können diese Beispieldatenbank mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher verwenden. Im Allgemeinen sollten Sie die Version der-Beispieldatenbank verwenden, die mit der Datenbank-Engine-Version übereinstimmt.
  
Gehen Sie zum Installieren der Datenbank wie folgt vor:  
  
1.  Laden Sie eine [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) -Datenbanksicherung von GitHub herunter.  
  
2.  Kopieren Sie die Sicherungsdatei in das Datenverzeichnis der lokalen SQL Server Datenbank-Engine-Instanz.
  
3.  Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der Datenbank-Engine-Instanz her.  
  
4.  Stellen Sie die Datenbank wieder her.  
  
## <a name="step-4-grant-database-permissions"></a>Schritt 4: Erteilen von Daten Bank Berechtigungen  
In den Beispielprojekten werden Einstellungen für den Datenquellenidentitätswechsel verwendet, die den Sicherheitskontext angeben, unter dem Daten importiert oder verarbeitet werden. Standardmäßig geben die Identitätswechseleinstellungen das Analysis Services-Dienstkonto für den Zugriff auf die Daten an. Um diese Standardeinstellung verwenden zu können, müssen Sie sicherstellen, dass das Dienst Konto, unter dem Analysis Services ausgeführt wird, über Daten Leser Berechtigungen für die **AdventureWorksDW** -Datenbank verfügt.  
  
> [!NOTE]  
> Um den Lerneffekt zu verbessern, wird empfohlen, die standardmäßige Identitätswechseloption für das Dienstkonto zu verwenden und dem Dienstkonto in SQL Server Datenleserberechtigungen zu erteilen. Es sind zwar weitere Identitätswechseloptionen verfügbar, jedoch sind nicht alle von ihnen für Verarbeitungsvorgänge geeignet. Insbesondere wird die Option zum Verwenden der Anmeldeinformationen des aktuellen Benutzers nicht für Verarbeitungsvorgänge unterstützt.  
  
1.  Bestimmen Sie das Dienstkonto. Sie können Kontoinformationen mit dem SQL Server-Konfigurations-Manager oder der Konsolenanwendung Dienste anzeigen. Wenn Sie Analysis Services als Standardinstanz installiert haben, wird der Dienst als **NT Service\MSSQLServerOLAPService**ausgeführt.  
  
2.  Stellen Sie in Management Studio eine Verbindung mit der Datenbank-Engine-Instanz her.  
  
3.  Erweitern Sie den Knoten Sicherheit, klicken Sie mit der rechten Maustaste auf Anmeldungen, und wählen Sie **Neue Anmeldung**aus.  
  
4.  Geben Sie auf der Seite Allgemein in Anmeldename den Namen **NT Service\MSSQLServerOLAPService** (bzw. den Namen des Kontos, unter dem der Dienst ausgeführt wird) ein.  
  
5.  Klicken Sie auf **Benutzerzuordnung**.  
  
6.  Aktivieren Sie das Kontrollkästchen neben der **AdventureWorksDW** -Datenbank. Zu den Mitgliedern der Rolle sollten automatisch **db_datareader** und **public**gehören. Klicken Sie auf **OK** , um die Standardeinstellungen zu übernehmen.  
  
## <a name="step-5-install-projects"></a>Schritt 5: Installieren von Projekten  

Das Lernprogramm enthält Beispielprojekte, damit Sie Ihre Ergebnisse mit einem fertigen Projekt vergleichen oder eine fortgeschrittenere Lektion beginnen können.  
  
1.  Laden Sie die Datei [Adventure-Works-Multidimensional-Tutorial-projects. zip](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services) von der Seite Adventure Works for Analysis Services Samples auf GitHub herunter.  
  
    Die Lernprogramm Projekte funktionieren [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] für und höher.  
  
2.  Verschieben Sie die ZIP-Datei in einen Ordner direkt unterhalb des Stammlaufwerks (beispielsweise C:\Tutorial). Durch diesen Schritt wird der "Pfad zu lang"-Fehler verringert, der manchmal auftritt, wenn Sie versuchen, die Dateien im Ordner "Downloads" zu entzippen.  
  
3.  Entzippen der Beispielprojekte: Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Alle extrahieren**aus. Nachdem Sie die Dateien extrahiert haben, sollten die Ordner Lesson 1, 2, 3, 5, 6, 7, 8, 9, 10 Complete und Lesson 4 Start sein. 
  
4.  Entfernen Sie den Schreibschutz dieser Dateien. Klicken Sie mit der rechten Maustaste auf den übergeordneten Ordner, wählen Sie **Eigenschaften**aus, und deaktivieren **Sie**das Kontrollkästchen schreibgeschützt. Klicken Sie auf **OK**. Wenden Sie die Änderungen auf diesen Ordner sowie Unterordner und Dateien an.  

5.  Öffnen Sie die Projektmappendatei (. sln), die der Lektion entspricht, in der Sie sich befinden. Im Ordner mit der Bezeichnung Lesson 1 Complete würden Sie z. B. die Datei Analysis Services Tutorial.sln öffnen.  
  
6.  Stellen Sie die Lösung bereit, um zu überprüfen, ob Daten Bank Berechtigungen und Serverstandort Informationen ordnungsgemäß eingerichtet sind  
  
    Wenn Analysis Services und die Datenbank-Engine als Standardinstanz (MSSQLServer) installiert sind und sämtliche Software auf demselben Computer ausgeführt wird, können Sie im Menü Erstellen auf **Projektmappe bereitstellen** klicken, um das Beispielprojekt zu erstellen und auf der lokalen Instanz von Analysis Services bereitzustellen. Während der Bereitstellung werden die Daten aus der **AdventureWorksDW** -Datenbank auf der lokalen Datenbank-Engine Instanz verarbeitet (oder importiert). Auf der Analysis Services-Instanz, die die aus der Datenbank-Engine abgerufenen Daten enthält, wird eine neue Analysis Services Datenbank erstellt.  
  
    Wenn Fehler auftreten, überprüfen Sie die vorherigen Schritte zum Einrichten von Datenbankberechtigungen. Zusätzlich müssen u. U. auch Servernamen geändert werden. Der Standardservername lautet "localhost". Wenn die Server auf Remotecomputern oder als benannte Instanzen installiert werden, müssen Sie den Standardnamen mit einem für Ihre Installation gültigen Servernamen überschreiben. Wenn sich die Server auf Remotecomputern befinden, müssen Sie möglicherweise außerdem die Windows-Firewall so konfigurieren, dass sie den Zugriff auf die Server zulässt.  
  
    Der Servername für Verbindungen mit der Datenbank-Engine wird im Datenquellenobjekt der mehrdimensionalen Projektmappe (Adventure Works-Lernprogramm) angegeben und im Projektmappen-Explorer angezeigt.  
  
    Der Servername für Verbindungen mit Analysis Services wird in den Eigenschaftenseiten des Projekts auf der Registerkarte Bereitstellung angegeben und ebenfalls im Projektmappen-Explorer angezeigt.  
  
7.  Stellen Sie in SQL Server Management Studio eine Verbindung mit Analysis Services her. Überprüfen Sie, ob auf dem Server eine Datenbank mit dem Namen **Analysis Services Tutorial** ausgeführt wird.  
  
## <a name="next-step"></a>Nächster Schritt  
Jetzt können Sie das Lernprogramm verwenden. Weitere Informationen für den Einstieg finden Sie unter [Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md).  
  
## <a name="see-also"></a>Siehe auch  
[Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
[Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
