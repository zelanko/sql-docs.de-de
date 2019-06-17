---
title: Installieren von Analysis Services-Beispieldaten und-Projekten | Microsoft-Dokumentation
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 999e1c1434bd727fe0ac889c2041145a5c1ec750
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404092"
---
# <a name="install-sample-data-and-multidimensional-projects"></a>Installieren von Beispieldaten und mehrdimensionale Projekte 
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

Verwenden Sie die Anweisungen und Links in diesem Artikel, um die in der Analysis Services-Tutorials verwendeten Daten- und Projektdateien-Dateien zu installieren. 
  
## <a name="step-1-install-prerequisites"></a>Schritt 1: Installieren der erforderlichen Komponenten 
In den Lektionen dieses Lernprogramms wird vorausgesetzt, dass Sie folgende Software installiert haben. Sie können alle Features auf einem einzelnen Computer installieren. Um diese Funktionen zu installieren, führen Sie SQL Server-Setup aus, und wählen Sie auf der Seite Funktionsauswahl diese Funktionen aus.  
  
-   SQL Server-Datenbank-Engine  
  
-   SQL Server Analysis Services  (SSAS) 
  
    Analysis Services ist in diesen Editionen nur zur Verfügung: Evaluation, Enterprise, Business Intelligence, Standard. Mehrdimensionale Modelle werden in Azure Analysis Services nicht unterstützt.
  
    Standardmäßig wird der Analysis Services 2016 und höher als tabellarische Instanz, die Sie überschreiben können, durch Auswählen von mehrdimensionalen Servermodus auf dem Server Configuration-Seite des Installations-Assistenten installiert.
  
## <a name="step-2-download-and-install-developer-and-management-tools"></a>Schritt 2: Herunterladen Sie und installieren Sie die Entwickler und Verwaltungstools
SQL Server Data Tools (SSDT) für Visual Studio ist heruntergeladen und getrennt von anderen SQL Server-Funktionen installiert. Der Designer und Projektvorlagen zum Erstellen von BI-Modelle und Berichte befinden sich im SSDT für Visual Studio 2015 oder als [Nuget-Pakete](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) für Visual Studio 2017.  
  
[Laden Sie SQL Server Data Tools (SSDT) herunter](http://go.microsoft.com/fwlink/?LinkID=827542).   

SQL Server Management Studio (SSMS) wird heruntergeladen und getrennt von anderen SQL Server-Funktionen installiert.  

[Hier können Sie SQL Server Management Studio herunterladen](../../ssms/download-sql-server-management-studio-ssms.md)  

Sie können Excel optional installieren, um mehrdimensionale Daten zu durchsuchen, während Sie das Lernprogramm ausführen. Durch die Installation von Excel wird die Funktion **In Excel analysieren** aktiviert. Diese startet Excel mit einer PivotTable-Feldliste, die mit dem Cube verbunden ist, den Sie erstellen. Es wird empfohlen, zum Durchsuchen von Daten Excel zu verwenden, da Sie schnell einen Pivotbericht erstellen können, der Ihnen das Interagieren mit den Daten ermöglicht.  
  
Alternativ können Sie Daten mithilfe des integrierten MDX-Abfrage-Designers durchsuchen, der in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] integriert ist. Der Abfrage-Designer gibt die gleichen Daten zurück, jedoch werden die Daten als flaches Rowset dargestellt.  
  
## <a name="step-3-install-databases"></a>Schritt 3: Installieren von Datenbanken  
In einem mehrdimensionalen Analysis Services-Modell werden Transaktionsdaten verwendet, die Sie aus einem Managementsystem für relationale Datenbanken importieren. Für die Zwecke dieses Tutorials verwenden Sie die folgende relationale Datenbank als Datenquelle aus.  
  
-   **AdventureWorksDW2012 oder höher** – Dies ist ein relationales Datawarehouse, die in einer-Engine-Datenbankmodulinstanz ausgeführt wird. Es enthält die ursprünglichen Daten, die von der Analysis Services-Datenbanken und -Projekte, die Sie erstellen und bereitstellen, die im Lernprogramm verwendet werden. Dieses Tutorial setzt voraus, AdventureWorksDW2012 kann, jedoch höher funktionieren.
  
    Sie können diese Beispieldatenbank mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher. Im Allgemeinen sollten Sie die Beispiel-Datenbankversion Abgleich Ihrer Datenbank-Engine-Version verwenden.
  
Führen Sie folgende Schritte aus, um die Datenbank zu installieren:  
  
1.  Herunterladen einer [AdventureWorkDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) datenbanksicherung aus GitHub.  
  
2.  Kopieren Sie die backup-Datei in das Datenverzeichnis der lokalen SQL Server-Datenbank-Engine-Instanz.
  
3.  Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der Datenbank-Engine-Instanz her.  
  
4.  Stellen Sie die Datenbank wieder her.  
  
## <a name="step-4-grant-database-permissions"></a>Schritt 4: Erteilen von Datenbankberechtigungen  
In den Beispielprojekten werden Einstellungen für den Datenquellenidentitätswechsel verwendet, die den Sicherheitskontext angeben, unter dem Daten importiert oder verarbeitet werden. Standardmäßig geben die Identitätswechseleinstellungen das Analysis Services-Dienstkonto für den Zugriff auf die Daten an. Um diese Standardeinstellung zu verwenden, müssen Sie sicherstellen, dass das Dienstkonto, unter denen Analysis Services ausgeführt wird, über datenleserberechtigungen hat, auf die **"AdventureWorksDW"** Datenbank.  
  
> [!NOTE]  
> Um den Lerneffekt zu verbessern, wird empfohlen, die standardmäßige Identitätswechseloption für das Dienstkonto zu verwenden und dem Dienstkonto in SQL Server Datenleserberechtigungen zu erteilen. Es sind zwar weitere Identitätswechseloptionen verfügbar, jedoch sind nicht alle von ihnen für Verarbeitungsvorgänge geeignet. Insbesondere wird die Option zum Verwenden der Anmeldeinformationen des aktuellen Benutzers nicht für Verarbeitungsvorgänge unterstützt.  
  
1.  Bestimmen Sie das Dienstkonto. Sie können Kontoinformationen mit dem SQL Server-Konfigurations-Manager oder der Konsolenanwendung Dienste anzeigen. Wenn Sie Analysis Services als Standardinstanz installiert haben, wird der Dienst als **NT Service\MSSQLServerOLAPService**ausgeführt.  
  
2.  Stellen Sie in Management Studio eine Verbindung mit der Datenbank-Engine-Instanz her.  
  
3.  Erweitern Sie den Knoten Sicherheit, klicken Sie mit der rechten Maustaste auf Anmeldungen, und wählen Sie **Neue Anmeldung**aus.  
  
4.  Geben Sie auf der Seite Allgemein in Anmeldename den Namen **NT Service\MSSQLServerOLAPService** (bzw. den Namen des Kontos, unter dem der Dienst ausgeführt wird) ein.  
  
5.  Klicken Sie auf **Benutzerzuordnung**.  
  
6.  Aktivieren Sie das Kontrollkästchen neben den **"AdventureWorksDW"** Datenbank. Zu den Mitgliedern der Rolle sollten automatisch **db_datareader** und **public**gehören. Klicken Sie auf **OK** , um die Standardeinstellungen zu übernehmen.  
  
## <a name="step-5-install-projects"></a>Schritt 5: Installieren von Projekten  

Das Lernprogramm enthält Beispielprojekte, damit Sie Ihre Ergebnisse mit einem fertigen Projekt vergleichen oder eine fortgeschrittenere Lektion beginnen können.  
  
1.  Herunterladen der [Adventure-Works-MDX-Tutorial – projects.zip](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services) aus der Adventure Works für Analysis Services-Beispielseite auf GitHub.  
  
    Die Lernprogrammprojekte funktionieren für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.  
  
2.  Verschieben Sie die ZIP-Datei in einen Ordner direkt unterhalb des Stammlaufwerks (beispielsweise C:\Tutorial). Dadurch verringert, den "Pfad zu lang"-Fehler, der manchmal ausgegeben, wenn Sie versuchen, die Dateien im Ordner Downloads zu Entzippen.  
  
3.  Entzippen der Beispielprojekte: Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Alle extrahieren**aus. Nach dem Entpacken der Dateien, müssen Sie die Ordner Lektion 1, 2, 3, 5, 6, 7, 8, 9, 10 abschließen und Lesson 4 Start. 
  
4.  Entfernen Sie den Schreibschutz dieser Dateien. Mit der rechten Maustaste in des übergeordneten Ordners, wählen Sie **Eigenschaften**, und deaktivieren Sie das Kontrollkästchen **schreibgeschützte**. Klicken Sie auf **OK**. Wenden Sie die Änderungen auf diesen Ordner sowie Unterordner und Dateien an.  

5.  Öffnen Sie die Projektmappendatei (.sln), die der Lektion, die Sie entspricht sich befinden. Im Ordner mit der Bezeichnung Lesson 1 Complete würden Sie z. B. die Datei Analysis Services Tutorial.sln öffnen.  
  
6.  Bereitstellen der Lösung, um sicherzustellen, dass die Berechtigungen für die Datenbank und Informationen zum Serverstandort ordnungsgemäß eingerichtet sind.  
  
    Wenn Analysis Services und die Datenbank-Engine als Standardinstanz (MSSQLServer) installiert sind und sämtliche Software auf demselben Computer ausgeführt wird, können Sie im Menü Erstellen auf **Projektmappe bereitstellen** klicken, um das Beispielprojekt zu erstellen und auf der lokalen Instanz von Analysis Services bereitzustellen. Während der Bereitstellung Daten verarbeitet (oder nicht importiert) aus der **"AdventureWorksDW"** Datenbank in der lokalen Datenbank-Engine-Instanz. Auf der Analysis Services-Instanz, die von der Datenbank-Engine abgerufenen Daten enthält, wird eine neue Analysis Services-Datenbank erstellt.  
  
    Wenn Fehler auftreten, überprüfen Sie die vorherigen Schritte zum Einrichten von Datenbankberechtigungen. Zusätzlich müssen u. U. auch Servernamen geändert werden. Der Standardservername lautet "localhost". Wenn die Server auf Remotecomputern oder als benannte Instanzen installiert werden, müssen Sie den Standardnamen mit einem für Ihre Installation gültigen Servernamen überschreiben. Wenn sich die Server auf Remotecomputern befinden, müssen Sie möglicherweise außerdem die Windows-Firewall so konfigurieren, dass sie den Zugriff auf die Server zulässt.  
  
    Der Servername für Verbindungen mit der Datenbank-Engine wird im Datenquellenobjekt der mehrdimensionalen Projektmappe (Adventure Works-Lernprogramm) angegeben und im Projektmappen-Explorer angezeigt.  
  
    Der Servername für Verbindungen mit Analysis Services wird in den Eigenschaftenseiten des Projekts auf der Registerkarte Bereitstellung angegeben und ebenfalls im Projektmappen-Explorer angezeigt.  
  
7.  Stellen Sie in SQL Server Management Studio eine Verbindung mit Analysis Services her. Überprüfen Sie, ob auf dem Server eine Datenbank mit dem Namen **Analysis Services Tutorial** ausgeführt wird.  
  
## <a name="next-step"></a>Nächster Schritt  
Jetzt können Sie das Lernprogramm verwenden. Weitere Informationen für den Einstieg finden Sie unter [Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md).  
  
## <a name="see-also"></a>Siehe auch  
[Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
[Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  