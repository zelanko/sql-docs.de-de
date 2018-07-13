---
title: Überprüfen der PowerPivot für SharePoint-Installation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7116c698e987ca86da83763dd1994c098a99026d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189377"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a>Überprüfen der PowerPivot für SharePoint-Installation
  Eine Instanz von PowerPivot für SharePoint, die Sie in einer SharePoint-Farm installieren, wird über die SharePoint-Zentraladministration verwaltet. Sie können zumindest die Seiten in der Zentraladministration und auf SharePoint-Websites überprüfen, um zu überprüfen, ob PowerPivot-Serverkomponenten und -funktionen verfügbar sind. Um jedoch eine Installation vollständig zu überprüfen, müssen Sie eine PowerPivot-Arbeitsmappe haben, die Sie in SharePoint veröffentlichen können und auf die Sie über eine Bibliothek zugreifen können. Zu Testzwecken können Sie eine Beispielarbeitsmappe veröffentlichen, die bereits PowerPivot-Daten enthält, und damit überprüfen, ob die SharePoint-Integration ordnungsgemäß konfiguriert wurde.  
  
##  <a name="verifyinstall"></a> Überprüfen der Integration der Zentraladministration  
 Um die PowerPivot-Integration in die Zentraladministration zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Klicken Sie auf im Menü Start auf **Programme**, öffnen Sie Microsoft SharePoint 2010-Produkte aus, und klicken Sie auf **SharePoint 2010 Central Administration**.  
  
2.  Geben Sie Ihren Benutzernamen und Ihr Kennwort ein, und klicken Sie dann auf **OK**.  
  
     Optional können Sie Browsereinstellungen ändern, damit Sie den Benutzernamen und das Kennwort nicht bei jedem Öffnen der Zentraladministration eingeben müssen. Gehen Sie wie folgt vor, um die Zentraladministration als vertrauenswürdige Website hinzuzufügen:  
  
    1.  Klicken Sie in Internet Explorer im Menü „Extras“ auf **Internetoptionen**.  
  
    2.  Klicken Sie auf der Registerkarte „Sicherheit“ im Abschnitt **Zone auswählen, um Einstellungen anzuzeigen oder zu ändern** auf „Vertrauenswürdige Sites“ und dann auf „Sites“.  
  
    3.  Deaktivieren Sie das Kontrollkästchen **Für Sites dieser Zone ist eine Serverüberprüfung (https:) erforderlich** .  
  
    4.  Geben Sie in **Diese Website zur Zone hinzufügen**die URL zu Ihrer Website ein, und klicken Sie dann auf **Hinzufügen**.  
  
    5.  Klicken Sie auf **Schließen**und dann auf **OK**.  
  
        > [!NOTE]  
        >  Die Dokumentation zur SharePoint-Installation enthält weitere Anweisungen zum Umgehen von Proxyserverfehlern und Deaktivieren der verstärkten Sicherheitskonfiguration für Internet Explorer, damit Updates heruntergeladen und installiert werden können. Weitere Informationen finden Sie im Abschnitt **Ausführen zusätzlicher Aufgaben** unter [Bereitstellen eines einzelnen Servers mit SQL Server](http://go.microsoft.com/fwlink/?LinkId=177754) auf der Microsoft-Website.  
  
3.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Farmfunktionen verwalten**.  
  
4.  Überprüfen Sie, ob **Funktion zur PowerPivot-Integration** auf **Aktiv**festgelegt ist.  
  
5.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Dienste auf dem Server verwalten**.  
  
6.  Überprüfen Sie, ob **SQL Server Analysis Services** und **SQL Server PowerPivot System Service** gestartet wurden.  
  
7.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
8.  Klicken Sie auf **PowerPivot-Standarddienstanwendung** zu PowerPivot-Management-Dashboard für diese Anwendung zu öffnen. Bei seiner ersten Verwendung dauert das Laden des Dashboards einige Minuten.  
  
     Alternativ klicken Sie auf den leeren Bereich neben **PowerPivot-Standarddienstanwendung** die Zeile, und klicken Sie auf **Eigenschaften** um die Konfigurationseinstellungen für diese dienstanwendung anzuzeigen. Sie können sowohl die Konfigurationseinstellungen als auch die Anwendungseigenschaften ändern, um Ihre Serverkonfiguration zu ändern. Weitere Informationen zu diesen Einstellungen finden Sie unter [erstellen und konfigurieren Sie eine PowerPivot-Dienstanwendung in der Zentraladministration](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).  
  
## <a name="verify-integration-at-the-site-level"></a>Überprüfen der Integration auf Websiteebene  
 Um die PowerPivot-Integration in eine SharePoint-Website zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Öffnen Sie in einem Browser die Webanwendung, die Sie erstellt haben. Wenn Sie Standardwerte verwendet haben, können Sie angeben, dass http://\<Ihr Computername > in der URL-Adresse.  
  
2.  Überprüfen Sie, ob der PowerPivot-Datenzugriff und die Verarbeitungsfunktionen in der Anwendung verfügbar sind. Überprüfen Sie hierzu das Vorhandensein von durch PowerPivot bereitgestellte Bibliotheksvorlagen:  
  
    1.  Klicken Sie unter Websiteaktionen auf **Weitere Optionen...** .  
  
    2.  Bibliotheken sollte **Datenfeedbibliothek** und **PowerPivot-Katalog**. Diese Bibliotheksvorlagen werden von der PowerPivot-Funktion bereitgestellt und sind in der Bibliothekenliste sichtbar, falls die Funktion ordnungsgemäß integriert wurde.  
  
## <a name="verify-data-access-on-the-server"></a>Überprüfen des Datenzugriffs auf dem Server  
 Um den PowerPivot-Datenzugriff auf dem Server zu überprüfen, gehen Sie wie folgt vor:  
  
1.  [Laden Sie das Datenbeispiel „Picnic“ herunter](http://go.microsoft.com/fwlink/?LinkID=219108) , das zu einem Reporting Services-Tutorial gehört. Sie verwenden die Beispielarbeitsmappe in diesem Download, um den PowerPivot-Datenzugriff zu überprüfen. Extrahieren Sie die Dateien.  
  
2.  Laden Sie die Excel-Arbeitsmappe (.xlsx) in die freigegebenen Dokumente hoch. Die Arbeitsmappe enthält eingebettete PowerPivot-Daten.  
  
3.  Klicken Sie auf das Dokument, um es von der Bibliothek aus zu öffnen.  
  
4.  Klicken Sie oben in der Arbeitsmappe auf einen Slicer oder einen Filter. Slicer in dieser Arbeitsmappe sind Month, Color und Type. Durch das Klicken auf einen Slicer wird eine PowerPivot-Abfrage gestartet und die Betriebsbereitschaft des Servers nachgewiesen. Der Server lädt PowerPivot-Daten im Hintergrund und gibt die Ergebnisse zurück.  
  
5.  Wechseln Sie erneut zur Bibliothek. Klicken Sie auf den Abwärtspfeil rechts neben der Arbeitsmappe und dann auf **Power View starten**. Durch diesen Schritt wird bestätigt, dass die [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] -Funktion in Reporting Services betriebsbereit ist. Überspringen Sie diesen Schritt, wenn Sie Reporting Services nicht installiert haben.  
  
     Im nächsten Schritt stellen Sie eine Verbindung mit dem Server in Management Studio her, um zu überprüfen, ob die Daten geladen und zwischengespeichert wurden.  
  
6.  Starten Sie SQL Server Management Studio im Startmenü in der Programmgruppe [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] . Wenn dieses Tool nicht auf dem Server installiert ist, können Sie mit dem letzten Schritt fortfahren, um das Vorhandensein zwischengespeicherter Dateien zu bestätigen.  
  
7.  Wählen Sie unter Servertyp die Option **Analysis Services**aus.  
  
8.  Geben Sie im Server-Namen,  **\<Servername > \powerpivot**, wobei  **\<Servername >** ist der Name des Computers, der dem PowerPivot für SharePoint-Installation ist.  
  
9. Klicken Sie auf **Verbinden**. Dies überprüft, ob der Analysis Services-Server verfügbar ist.  
  
10. Sie können im Objekt-Explorer klicken **Datenbanken** zum Anzeigen der Liste der PowerPivot-Datendateien, die geladen werden.  
  
11. Überprüfen Sie im Computerdateisystem den folgenden Ordner, um zu bestimmen, ob Dateien auf dem Datenträger zwischengespeichert wurden. Das Vorhandensein zwischengespeicherter Dateien ist eine weitere Bestätigung, dass die Bereitstellung betriebsbereit ist. Um den Dateicache anzuzeigen, wechseln Sie zu der \<Laufwerk >: \Programme\Microsoft SQL Server\MSAS11. PowerPivot-Dienstanwendung POWERPIVOT\OLAP\Backup\Sandboxes\Default-Ordner. Jede zwischengespeicherte Datenbank wird in einem eigenen Ordner gespeichert. Dabei wird eine GUID-basierte Namenskonvention verwendet, um einen eindeutigen Namen sicherzustellen.  
  
  
