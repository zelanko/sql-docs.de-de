---
title: PowerPivot für SharePoint 2013-Installation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 614674d3ac7a14ec3a6143381ef249a215850bc0
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53373972"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a>PowerPivot for SharePoint 2013 Installation
  In den Verfahren in diesem Thema werden Sie durch die Installation eines einzelnen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Servers im SharePoint-Bereitstellungsmodus geführt. In den Schritten führen Sie u. a. den Installations-Assistenten für SQL Server sowie Konfigurationsaufgaben unter Verwendung der SharePoint 2013-Zentraladministration aus.  
  
 **[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 201  
  
 **In diesem Thema:**  
  
 [Hintergrund](#bkmk_background)  
  
 [Erforderliche Komponenten](#bkmk_prereq)  
  
 [Schritt 1: Installieren von PowerPivot für SharePoint](#InstallSQL)  
  
 [Schritt 2: Konfigurieren Sie die grundlegende Analysis Services-SharePoint-Integration](#bkmk_config)  
  
 [Schritt 3: Überprüfen der Integration](#bkmk_verify)  
  
 [Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](#bkmk_firewall)  
  
 [Aktualisieren von Arbeitsmappen und geplanter Datenaktualisierung](#bkmk_upgrade_workbook)  
  
 [Nach der Installation auf einem Server – PowerPivot für Microsoft SharePoint](#bkmk_multiple_servers)  
  
##  <a name="bkmk_background"></a> Hintergrund  
 PowerPivot für SharePoint umfasst Dienste der mittleren Ebene sowie Back-End-Dienste, die den PowerPivot-Datenzugriff in einer SharePoint 2013-Farm ermöglichen.  
  
-   **Back-End-Dienste:** Bei Verwendung von PowerPivot für Excel zum Erstellen von Arbeitsmappen, die analytische Daten enthalten, müssen Sie PowerPivot für SharePoint den Zugriff auf diese Daten in einer serverumgebung verfügen. Sie können SQL Server-Setup auf einem Computer ausführen, auf dem SharePoint Server 2013 installiert ist, oder auf einem anderen Computer, der keine SharePoint-Software enthält. Zwischen Analysis Services und SharePoint bestehen keine Abhängigkeiten.  
  
     **Hinweis**: In diesem Thema wird beschrieben, die Installation der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Server und die Back-End-Dienste.  
  
-   **Mittlere Ebene:** Erweiterungen zur PowerPivot-Funktionalität in SharePoint einschließlich PowerPivot-Katalog, planmäßiger Datenaktualisierung, Management-Dashboard und Datenanbieter. Weitere Informationen zur Installation und Konfiguration der mittleren Ebene finden Sie unter:  
  
    -   [Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
    -   [Konfigurieren von PowerPivot und Bereitstellen von Lösungen &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
##  <a name="bkmk_prereq"></a> Erforderliche Komponenten  
  
1.  Sie müssen lokaler Administrator sein, um SQL Server-Setup auszuführen.  
  
2.  SharePoint Server 2013 Enterprise Edition ist für PowerPivot für SharePoint erforderlich. Sie können auch die Evaluation Enterprise Edition verwenden.  
  
3.  Der Computer muss einer Domäne in derselben Active Directory-Gesamtstruktur wie Excel Services beitreten.  
  
4.  Der Name der PowerPivot-Instanz muss vorhanden sein. Der Computer, auf dem Sie Analysis Services im SharePoint-Modus installieren, darf keine benannte PowerPivot-Instanz enthalten.  
  
5.  Überprüfen Sie [Hardware- und Softwareanforderungen für Analysis Services-Server im SharePoint-Modus &#40;SQLServer 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).  
  
6.  Überprüfen Sie die Versionshinweise unter [SQL Server 2012 Service Pack 1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).  
  
###  <a name="bkmk_sqleditions"></a> Anforderungen für die SQL Server-Edition  
 Nicht alle Business Intelligence-Funktionen sind in allen Editionen von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]verfügbar. Weitere Informationen finden Sie unter [von den SQL Server 2012-Editionen unterstützte Funktionen (https://go.microsoft.com/fwlink/?linkid=232473) ](https://go.microsoft.com/fwlink/?linkid=232473) und [Editionen und Komponenten von SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
 Die aktuellen versionsanmerkungen finden Sie unter [Versionsanmerkungen zu SQL Server 2012 SP1](ttp://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).  
  
 [Versionsanmerkungen für Microsoft SQL Server 2012 (https://go.microsoft.com/fwlink/?LinkId=236893)](https://go.microsoft.com/fwlink/?LinkId=236893).  
  
##  <a name="InstallSQL"></a> Schritt 1: Installieren von PowerPivot für SharePoint  
 In diesem Schritt führen Sie SQL Server-Setup aus, um einen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus zu installieren. In einem anschließenden Schritt konfigurieren Sie Excel Services so, dass dieser Server für Arbeitsmappen-Datenmodelle verwendet wird.  
  
1.  Führen Sie den Installations-Assistenten für SQL Server (Setup.exe) aus.  
  
2.  Klicken Sie im linken Navigationsbereich auf **Installation** .  
  
3.  Klicken Sie auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
4.  Wenn die Seite **Product Key** angezeigt wird, geben Sie die Evaluation Edition an, oder geben Sie einen Product Key für eine lizenzierte Kopie der Enterprise Edition ein. Klicken Sie auf **Weiter**. Weitere Informationen zu den Editionen finden Sie unter [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
5.  Überprüfen und akzeptieren Sie die Microsoft-Software-Lizenzbedingungen, und klicken Sie dann auf **Weiter**.  
  
6.  Wenn die Seite **Globale Regeln** geöffnet wird, lesen Sie alle Regelinformationen, die vom Setup-Assistenten angezeigt werden.  
  
7.  Auf der Seite **Microsoft Update** sollten Sie mithilfe von Microsoft Update nach Updates suchen und dann auf **Weiter**klicken.  
  
8.  Die Seite **Setupdateien installieren** wird mehrere Minuten lang ausgeführt. Überprüfen Sie alle Regelwarnungen oder fehlerhaften Regeln, und klicken Sie dann auf **Weiter**.  
  
9. Wenn erneut **Setupunterstützungsregeln**angezeigt wird, lesen Sie alle Warnungen und klicken auf **Weiter**.  
  
     **Hinweis**: Da Windows-Firewall aktiviert ist, sehen Sie gewarnt, Ports zum Aktivieren des Remotezugriffs zu öffnen.  
  
10. Wählen Sie auf der Seite **Setuprolle** die Option **SQL Server PowerPivot für SharePoint**aus. Durch diese Option wird Analysis Services im SharePoint-Modus installiert.  
  
     Optional können Sie der Installation eine Instanz der Datenbank-Engine hinzufügen. Sie können die Datenbank-Engine hinzufügen, wenn Sie eine neue Farm einrichten und benötigen einen Datenbankserver der Farm-Konfiguration und-Inhaltsdatenbanken ausgeführt. Durch diese Option wird auch [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]installiert.  
  
     Wenn Sie die Datenbank-Engine hinzufügen, wird sie als benannte **PowerPivot** -Instanz installiert. Wenn Sie eine Verbindung mit dieser Instanz angeben, geben Sie den Datenbanknamen im folgenden Format an: [`servername`]\PowerPivot.  
  
     Klicken Sie auf **Weiter**.  
  
     ![Setuprolle](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Setuprolle")  
  
11. Unter Funktionsauswahl wird zu Informationszwecken eine schreibgeschützte Liste der Funktionen angezeigt. Sie können keine Elemente hinzufügen oder entfernen, die vorab für diese Rolle ausgewählt wurden. Klicken Sie auf **Weiter**.  
  
12. Auf der Seite **Instanzkonfiguration** wird der schreibgeschützte Instanzname 'PowerPivot' zu Informationszwecken angezeigt. Dieser Instanzname ist erforderlich und kann nicht geändert werden. Sie können jedoch eine eindeutige Instanz-ID eingeben, um einen beschreibenden Verzeichnisnamen und Registrierungsschlüssel anzugeben. Klicken Sie auf **Weiter**.  
  
13. Legen Sie alle Dienste auf der Seite **Serverkonfiguration** auf den **Starttyp**"Automatisch" fest. Geben Sie das gewünschte Domänenkonto und Kennwort für **SQL Server Analysis Services**an, **(1)** im folgenden Diagramm.  
  
    -   Für [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]können Sie ein **Domänenbenutzerkonto** oder ein **NetworkService-Konto** verwenden. Das LocalSystem- oder LocalService-Konto sollte nicht verwendet werden.  
  
    -   Wenn Sie die SQL Server-Datenbank-Engine und den SQL Server-Agent hinzugefügt haben, können Sie die Dienste zur Ausführung unter Domänenbenutzerkonten oder unter dem standardmäßigen virtuellen Konto konfigurieren.  
  
    -   Stellen Sie niemals Dienstkonten unter Ihrem eigenen Domänenbenutzerkonto bereit. Dies gewährt dem Server die gleichen Berechtigungen, über die Sie für die Ressourcen im Netzwerk verfügen. Wenn der Server von einem böswilligen Benutzer angegriffen wird, wird dieser Benutzer mit Ihren Domänenanmeldeinformationen angemeldet. Der Benutzer ist dann berechtigt, die gleichen Daten und Anwendungen herunterzuladen und zu verwenden wie Sie.  
  
     Klicken Sie auf **Weiter**.  
  
     ![SSAS-Serverkonfiguration](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server-Konfiguration")  
  
14. Wenn Sie das [!INCLUDE[ssDE](../../../includes/ssde-md.md)]installieren, wird die Seite **Datenbank-Engine-Konfiguration** angezeigt. Klicken Sie in der [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Konfiguration auf **Aktuellen Benutzer hinzufügen** , um Ihrem Benutzerkonto Administratorberechtigungen für die Datenbank-Engine-Instanz zu gewähren.  
  
     Klicken Sie auf **Weiter**.  
  
15. Klicken Sie auf der Seite **Analysis Services-Konfiguration** auf **Aktuellen Benutzer hinzufügen** , um Ihrem Benutzerkonto Administratorberechtigungen zu gewähren. Sie benötigen die Administratorberechtigung, um den Server nach Abschluss von Setup zu konfigurieren.  
  
    -   Fügen Sie auf der gleichen Seite das Windows-Benutzerkonto einer Person hinzu, die ebenfalls Administratorberechtigungen benötigt. Beispielsweise muss jeder Benutzer, der in [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] eine Verbindung mit der [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Instanz herstellen möchte, um Datenbankverbindungsprobleme zu beheben, über Systemadministratorberechtigungen verfügen. Fügen Sie das Benutzerkonto einer Person hinzu, die möglicherweise jetzt die Problembehandlung oder Verwaltung des Servers ausführen möchte.  
  
    -   > [!NOTE]  
        >  Alle Dienstanwendungen, die Zugriff auf die Analysis Services-Serverinstanz erfordern, müssen über Analysis Services-Administratorberechtigungen verfügen. Fügen Sie z. B. die Dienstkonten für Excel Services, Power View und PerformancePoint-Dienste hinzu. Fügen Sie zusätzlich das SharePoint-Farmkonto hinzu, das als Identität der Webanwendung verwendet wird, von der die Zentraladministration gehostet wird.  
  
     Klicken Sie auf **Weiter**.  
  
16. Klicken Sie auf der Seite **Fehlerberichterstellung** auf **Weiter**.  
  
17. Klicken Sie auf der Seite **Installationsbereit** auf **Installieren**.  
  
18. Wenn das Dialogfeld **Computerneustart erforderlich**angezeigt wird, klicken Sie auf **OK**.  
  
19. Wenn die Installation abgeschlossen ist, klicken Sie auf **Schließen**.  
  
20. Starten Sie den Computer neu.  
  
21. Wenn in Ihrer Umgebung eine Firewall verwendet wird, informieren Sie sich im Thema [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md)der SQL Server-Onlinedokumentation.  
  
### <a name="verify-the-sql-server-installation"></a>Überprüfen der SQL Server-Installation  
 Vergewissern Sie sich, dass der Analysis Services-Dienst ausgeführt wird.  
  
1.  Klicken Sie in Microsoft Windows auf **Start**, **Alle Programme**und dann auf die Gruppe **Microsoft SQL Server 2012** .  
  
2.  Klicken Sie auf **SQL Server Management Studio**.  
  
3.  Stellen Sie eine Verbindung mit der Analysis Services-Instanz her, beispielsweise **[Servername]\POWERPIVOT**. Wenn Sie eine Verbindung mit der Instanz herstellen können, ist sichergestellt, dass der Dienst ausgeführt wird.  
  
##  <a name="bkmk_config"></a> Schritt 2: Konfigurieren Sharepoint-Integration von Basic Analysis Services  
 In den folgenden Schritten werden die erforderlichen Konfigurationsänderungen beschrieben, die die Interaktion mit erweiterten Excel-Datenmodellen innerhalb einer SharePoint-Dokumentbibliothek ermöglichen. Führen Sie diese Schritte nach der Installation von SharePoint Server 2013 und SQL Server Analysis Services aus.  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a>Gewähren von Excel Services-Serveradministratorrechten für Analysis Services  
 Die in diesem Abschnitt beschriebenen Schritte müssen nicht ausgeführt werden, wenn Sie das Dienstkonto für die Excel Services-Anwendung während der Analysis Services-Installation als Analysis Services-Administrator hinzugefügt haben.  
  
1.  Starten Sie auf dem Analysis Services-Server die Anwendung SQL Server Management Studio, und stellen Sie eine Verbindung mit der Analysis Services-Instanz her, z. B. `[MyServer]\POWERPIVOT`.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Instanznamen, und klicken Sie auf **Eigenschaften**.  
  
     ![Anzeigen der Eigenschaften eines SSAS-Servers](../../../sql-server/install/media/as-ssms-proeprties.gif "Eigenschaften eines SSAS-Servers anzeigen")  
  
3.  Klicken Sie im linken Bereich auf **Sicherheit**. Fügen Sie die Domänenanmeldung hinzu, die Sie in Schritt 1 für die Excel Services-Anwendung konfiguriert haben.  
  
     ![Die Sicherheitseinstellungen eines SSAS-Servers](../../../sql-server/install/media/as-ssms-security.gif "Sicherheitseinstellungen eines SSAS-Servers")  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a>Konfigurieren von Excel Services für die Analysis Services-Integration  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie auf den Namen der Dienstanwendung; der Standardname lautet **Excel Services-Anwendung**.  
  
3.  Klicken Sie auf der Seite **Excel Services-Anwendung verwalten**auf **Datenmodelleinstellungen**.  
  
4.  Klicken Sie auf **Server hinzufügen**.  
  
5.  Geben Sie unter **Servername**den Namen des Analysis Services-Servers und der PowerPivot-Instanz ein. Beispiel: `MyServer\POWERPIVOT`. Der Name der PowerPivot-Instanz ist erforderlich.  
  
     Geben Sie eine Beschreibung ein.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Die Änderungen werden innerhalb einiger Minuten wirksam. Alternativ können Sie für den Dienst **Dienste für Excel-Berechnungen** auch auf **Beenden** bzw. **Starten**klicken. Aktion  
  
     Eine andere Möglichkeit besteht darin, eine Eingabeaufforderung unter Verwendung von Administratorprivilegien zu öffnen und `iisreset /noforce`einzugeben.  
  
     Anhand der Einträge im ULS-Protokoll können Sie feststellen, ob der Server von Excel Services erkannt wird. Die Einträge lauten etwa wie folgt:  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="bkmk_verify"></a> Schritt 3: Überprüfen der Integration  
 In den folgenden Schritten erfahren Sie, wie eine neue Arbeitsmappe erstellt und hochgeladen wird, um zu überprüfen, ob die Analysis Services-Integration erfolgreich war. Sie benötigen für diese Schritte eine SQL Server-Datenbank.  
  
1.  **Hinweis**: Wenn Sie bereits über eine erweiterte Arbeitsmappe mit Slicern oder Filtern verfügen, können Sie sie in die SharePoint-Dokumentbibliothek hochladen und überprüfen, ob Sie in der Lage sind, mit den Slicern und Filtern in der Dokumentbibliotheksansicht zu interagieren.  
  
2.  Starten Sie in Excel eine neue Arbeitsmappe.  
  
3.  Klicken Sie auf der Registerkarte Daten im Menüband in **Externe Daten abrufen** auf **Aus anderen Quellen**.  
  
4.  Wählen Sie **Aus SQL Server**.  
  
5.  Geben Sie im **Datenverbindungs-Assistenten** den Namen der SQL Server-Instanz ein, in der die Datenbank enthalten ist, die Sie verwenden möchten.  
  
6.  Stellen Sie sicher, dass für die Anmeldeinformationen **Windows-Authentifizierung verwenden** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7.  Wählen Sie die Datenbank aus, die Sie verwenden möchten.  
  
8.  Achten Sie darauf, dass das Kontrollkästchen **Mit einer ausgewählten Tabelle verbinden** aktiviert ist.  
  
9. Klicken Sie auf das Kontrollkästchen **Auswahl mehrerer Tabellen aktivieren und Tabellen zum Excel-Datenmodell hinzufügen** .  
  
10. Wählen Sie die Tabellen aus, die Sie importieren möchten.  
  
11. Klicken Sie auf das Kontrollkästchen **Beziehungen zwischen ausgewählten Tabellen importieren**und dann auf **Weiter**. Durch den Import mehrerer Tabellen aus einer relationalen Datenbank können Sie mit Tabellen arbeiten, die bereits verknüpft sind. Sie sparen Arbeitsschritte, da Sie die Beziehungen nicht manuell erstellen müssen.  
  
12. Geben Sie auf der Assistentenseite **Datenverbindungsdatei speichern und fertig stellen** einen Namen für die Verbindung ein, und klicken Sie auf **Fertig stellen**.  
  
13. Das Dialogfeld **Daten importieren** wird angezeigt. Wählen Sie **PivotTable-Bericht**aus, und klicken Sie dann auf **OK**.  
  
14. In der Arbeitsmappe wird eine PivotTable-Feldliste angezeigt.   
    Klicken Sie in der Feldliste auf die Registerkarte **Alle** .  
  
15. Fügen Sie den Bereichen Zeile, Spalten und Wert in der Feldliste Felder hinzu.  
  
16. Fügen Sie der PivotTable einen Slicer oder Filter hinzu. **Sie sollten diesen Schritt nicht überspringen**. Mithilfe eines Slicers oder Filters können Sie auf einfache Weise die Analysis Services-Installation überprüfen.  
  
17. Speichern Sie die Arbeitsmappe in einer Dokumentbibliothek auf einem SharePoint 2013-Server, auf dem Excel Services konfiguriert ist. Sie können die Arbeitsmappe auch auf einer Dateifreigabe speichern und dann in die Dokumentbibliothek auf dem SharePoint 2013-Server hochladen.  
  
18. Klicken Sie auf den Namen der Arbeitsmappe, um sie in SharePoint anzuzeigen, und klicken Sie auf den Slicer, oder ändern Sie den Filter, den Sie zuvor hinzugefügt haben. Im Fall eines Datenupdates wissen Sie, dass Analysis Services installiert und für Excel Services verfügbar ist. Wenn Sie die Arbeitsmappe in Excel öffnen, verwenden Sie eine zwischengespeicherte Kopie und nicht den Analysis Services-Server.  
  
##  <a name="bkmk_firewall"></a> Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen  
 Anhand der Informationen im Thema [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) können Sie feststellen, ob Sie die Blockierung von Ports in einer Firewall aufheben müssen, um den Zugriff auf Analysis Services oder PowerPivot für SharePoint zuzulassen. Führen Sie die Schritte in diesem Thema aus, um Port- und Firewalleinstellungen zu konfigurieren. In der Praxis sollten Sie diese Schritte zusammen ausführen, um den Zugriff auf Ihren Analysis Services-Server zuzulassen.  
  
##  <a name="bkmk_upgrade_workbook"></a> Aktualisieren von Arbeitsmappen und geplanter Datenaktualisierung  
 Welche Schritte Sie zum Aktualisieren von Arbeitsmappen ausführen müssen, die in früheren Versionen von PowerPivot erstellt wurden, hängt von der PowerPivot-Version ab, mit der die Arbeitsmappe erstellt wurde. Weitere Informationen finden Sie unter [Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
##  <a name="bkmk_multiple_servers"></a> Nach der Installation auf einem Server – PowerPivot für Microsoft SharePoint  
 **Web-Front-End (WFE)** oder **mittlere Ebene:**: Verwenden einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Server im SharePoint-Modus in einer größeren Sharepointfarm und zusätzliche PowerPivot-Funktionen in der Farm, führen Sie das Installer-Paket installieren **spPowerPivot.msi** auf jedem der SharePoint-Server. Mithilfe von spPowerPivot.msi werden die erforderlichen Datenanbieter und das PowerPivot für SharePoint 2013-Konfigurationstool installiert.  
  
 Weitere Informationen zur Installation und Konfiguration der mittleren Ebene finden Sie unter:  
  
-   [Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
-   Informationen zum Herunterladen der MSI-Datei finden Sie unter [Microsoft SQL Server 2014 PowerPivot für Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)  
  
-   [Konfigurieren von PowerPivot und Bereitstellen von Lösungen &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
 **Redundanz und serverauslastung:** Installieren einer zweiten bzw. weiterer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus werden die Redundanz der der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Serverfunktionen. Durch Hinzufügen zusätzlicher Server wird die Arbeitsauslastung auf mehrere Server verteilt. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [Konfigurieren von Analysis Services für die Verarbeitung von Datenmodellen in Excel Services](https://technet.microsoft.com/library/jj614437\(v=office.15\)) (https://technet.microsoft.com/library/jj614437(v=office.15)).  
  
-   [Verwalten von Excel Services-datenmodelleinstellungen (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\)) (https://technet.microsoft.com/library/jj219780(v=office.15)).  
  
 ![SharePoint-Einstellungen](../../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") [Senden von Feedback und Kontaktinformationen Informationen über Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren von PowerPivot zu SharePoint 2013](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)   
 [Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
