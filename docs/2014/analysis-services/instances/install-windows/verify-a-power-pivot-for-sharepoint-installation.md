---
title: Überprüfen einer PowerPivot für SharePoint Installation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5578bed4ce59ffb3c431c30e33418abe693a4165
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543842"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a>Überprüfen der PowerPivot für SharePoint-Installation
  Eine Instanz von PowerPivot für SharePoint, die Sie in einer SharePoint-Farm installieren, wird über die SharePoint-Zentraladministration verwaltet. Sie können zumindest die Seiten in der Zentraladministration und auf SharePoint-Websites überprüfen, um zu überprüfen, ob PowerPivot-Serverkomponenten und -funktionen verfügbar sind. Um jedoch eine Installation vollständig zu überprüfen, müssen Sie eine PowerPivot-Arbeitsmappe haben, die Sie in SharePoint veröffentlichen können und auf die Sie über eine Bibliothek zugreifen können. Zu Testzwecken können Sie eine Beispielarbeitsmappe veröffentlichen, die bereits PowerPivot-Daten enthält, und damit überprüfen, ob die SharePoint-Integration ordnungsgemäß konfiguriert wurde.  
  
##  <a name="verify-central-administration-integration"></a><a name="verifyinstall"></a>Überprüfen der Integration der zentral Administration  
 Um die PowerPivot-Integration in die Zentraladministration zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Klicken Sie im Startmenü auf **Alle Programme**, öffnen Sie Microsoft SharePoint 2010-Produkte, und klicken Sie auf **SharePoint 2010-zentral Administration**.  
  
2.  Geben Sie Ihren Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.  
  
     Optional können Sie Browsereinstellungen ändern, damit Sie den Benutzernamen und das Kennwort nicht bei jedem Öffnen der Zentraladministration eingeben müssen. Gehen Sie wie folgt vor, um die Zentraladministration als vertrauenswürdige Website hinzuzufügen:  
  
    1.  Klicken Sie in Internet Explorer im Menü Extras auf **Internet Optionen**.  
  
    2.  Klicken Sie auf der Registerkarte „Sicherheit“ im Abschnitt **Zone auswählen, um Einstellungen anzuzeigen oder zu ändern** auf „Vertrauenswürdige Sites“ und dann auf „Sites“.  
  
    3.  Deaktivieren Sie das Kontrollkästchen **Für Sites dieser Zone ist eine Serverüberprüfung (https:) erforderlich** .  
  
    4.  Geben Sie in **Diese Website zur Zone hinzufügen**die URL zu Ihrer Website ein, und klicken Sie dann auf **Hinzufügen**.  
  
    5.  Klicken Sie auf **Schließen** und dann auf **OK**.  
  
        > [!NOTE]  
        >  Die Dokumentation zur SharePoint-Installation enthält weitere Anweisungen zum Umgehen von Proxyserverfehlern und Deaktivieren der verstärkten Sicherheitskonfiguration für Internet Explorer, damit Updates heruntergeladen und installiert werden können. Weitere Informationen finden Sie im Abschnitt **Ausführen zusätzlicher Aufgaben** unter [Bereitstellen eines einzelnen Servers mit SQL Server](https://go.microsoft.com/fwlink/?LinkId=177754) auf der Microsoft-Website.  
  
3.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmfunktionen verwalten**.  
  
4.  Überprüfen Sie, ob **Funktion zur PowerPivot-Integration** auf **Aktiv**festgelegt ist.  
  
5.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Dienste auf dem Server verwalten**.  
  
6.  Überprüfen Sie, ob **SQL Server Analysis Services** und **SQL Server PowerPivot System Service** gestartet wurden.  
  
7.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
8.  Klicken Sie auf **Power Pivot-Standard Dienst Anwendung** , um Power Pivot-Management-Dashboard für diese Anwendung zu öffnen. Bei seiner ersten Verwendung dauert das Laden des Dashboards einige Minuten.  
  
     Klicken Sie alternativ auf den leeren Bereich neben **Standard-Power Pivot-Dienst Anwendung** , um die Zeile auszuwählen, und klicken Sie auf **Eigenschaften** , um die Konfigurationseinstellungen für diese Dienst Anwendung anzuzeigen. Sie können sowohl die Konfigurationseinstellungen als auch die Anwendungseigenschaften ändern, um Ihre Serverkonfiguration zu ändern. Weitere Informationen zu diesen Einstellungen finden Sie unter [Erstellen und Konfigurieren einer Power Pivot-Dienst Anwendung in der zentral Administration](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).  
  
## <a name="verify-integration-at-the-site-level"></a>Überprüfen der Integration auf Websiteebene  
 Um die PowerPivot-Integration in eine SharePoint-Website zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Öffnen Sie in einem Browser die Webanwendung, die Sie erstellt haben. Wenn Sie Standardwerte verwendet haben, können Sie http:// \<your computer name> in der URL-Adresse angeben.  
  
2.  Überprüfen Sie, ob der PowerPivot-Datenzugriff und die Verarbeitungsfunktionen in der Anwendung verfügbar sind. Überprüfen Sie hierzu das Vorhandensein von durch PowerPivot bereitgestellte Bibliotheksvorlagen:  
  
    1.  Klicken Sie unter Website Aktionen auf **Weitere Optionen..**.  
  
    2.  In Bibliotheken sollten die **datenfeedbibliothek** und der **Power Pivot**-Katalog angezeigt werden. Diese Bibliotheksvorlagen werden von der PowerPivot-Funktion bereitgestellt und sind in der Bibliothekenliste sichtbar, falls die Funktion ordnungsgemäß integriert wurde.  
  
## <a name="verify-data-access-on-the-server"></a>Überprüfen des Datenzugriffs auf dem Server  
 Um den PowerPivot-Datenzugriff auf dem Server zu überprüfen, gehen Sie wie folgt vor:  
  
1.  [Laden Sie das Datenbeispiel „Picnic“ herunter](https://go.microsoft.com/fwlink/?LinkID=219108) , das zu einem Reporting Services-Tutorial gehört. Sie verwenden die Beispielarbeitsmappe in diesem Download, um den PowerPivot-Datenzugriff zu überprüfen. Extrahieren Sie die Dateien.  
  
2.  Laden Sie die Excel-Arbeitsmappe (.xlsx) in die freigegebenen Dokumente hoch. Die Arbeitsmappe enthält eingebettete PowerPivot-Daten.  
  
3.  Klicken Sie auf das Dokument, um es von der Bibliothek aus zu öffnen.  
  
4.  Klicken Sie oben in der Arbeitsmappe auf einen Slicer oder einen Filter. Slicer in dieser Arbeitsmappe sind Month, Color und Type. Durch das Klicken auf einen Slicer wird eine PowerPivot-Abfrage gestartet und die Betriebsbereitschaft des Servers nachgewiesen. Der Server lädt PowerPivot-Daten im Hintergrund und gibt die Ergebnisse zurück.  
  
5.  Wechseln Sie erneut zur Bibliothek. Klicken Sie auf den Abwärtspfeil rechts neben der Arbeitsmappe und dann auf **Power View starten**. Durch diesen Schritt wird bestätigt, dass die [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] -Funktion in Reporting Services betriebsbereit ist. Überspringen Sie diesen Schritt, wenn Sie Reporting Services nicht installiert haben.  
  
     Im nächsten Schritt stellen Sie eine Verbindung mit dem Server in Management Studio her, um zu überprüfen, ob die Daten geladen und zwischengespeichert wurden.  
  
6.  Starten Sie SQL Server Management Studio im Startmenü in der Programmgruppe [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] . Wenn dieses Tool nicht auf dem Server installiert ist, können Sie mit dem letzten Schritt fortfahren, um das Vorhandensein zwischengespeicherter Dateien zu bestätigen.  
  
7.  Wählen Sie unter Servertyp die Option **Analysis Services**aus.  
  
8.  Geben Sie unter Server Name den Namen ** \<server-name> \powerpivot**ein, wobei **\<server-name>** der Name des Computers ist, auf dem sich die PowerPivot für SharePoint-Installation befindet.  
  
9. Klicken Sie auf **Verbinden**. Dies überprüft, ob der Analysis Services-Server verfügbar ist.  
  
10. In Objekt-Explorer können Sie auf **Datenbanken** klicken, um die Liste der geladenen Power Pivot-Datendateien anzuzeigen.  
  
11. Überprüfen Sie im Computerdateisystem den folgenden Ordner, um zu bestimmen, ob Dateien auf dem Datenträger zwischengespeichert wurden. Das Vorhandensein zwischengespeicherter Dateien ist eine weitere Bestätigung, dass die Bereitstellung betriebsbereit ist. Um den Dateicache anzuzeigen, wechseln Sie zu " \<drive> : \Programme\Microsoft SQL server\msas11.". Powerpivot\olap\backup\sandboxes\standard-Power Pivot-Dienst Anwendungsordner. Jede zwischengespeicherte Datenbank wird in einem eigenen Ordner gespeichert. Dabei wird eine GUID-basierte Namenskonvention verwendet, um einen eindeutigen Namen sicherzustellen.  
  
  
