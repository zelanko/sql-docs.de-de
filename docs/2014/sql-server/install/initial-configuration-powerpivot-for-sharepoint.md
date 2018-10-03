---
title: Anfängliche Konfiguration (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6e236f2ccd1478fc98d712e89b1d6d0a781a8ac2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211346"
---
# <a name="initial-configuration-powerpivot-for-sharepoint"></a>Anfängliche Konfiguration (PowerPivot für SharePoint)
  Verwenden Sie die Schritte in diesem Thema, um eine ursprüngliche Installation von PowerPivot für SharePoint zu konfigurieren. Die einfachste Möglichkeit zur Konfiguration einer ursprünglichen Installation ist die Verwendung des PowerPivot-Konfigurationstools. Dieses Tool automatisiert alle unten beschriebenen Konfigurationsschritte.  
  
 Wenn Sie mehr Kontrolle über die Konfiguration des Servers haben möchten, können Sie alternativ die Zentraladministration und die Informationen in diesem Thema verwenden, um jeden Schritt einzeln auszuführen.  
  
 
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Der SharePoint-Server muss im SharePoint-Setup mit der Installationsoption Serverfarm installiert worden sein. Ein eigenständiger SharePoint-Server, der eine integrierte Datenbank verwendet, wird nicht unterstützt. Weitere Informationen finden Sie unter [Anleitungen für die Verwendung von SQL Server BI-Funktionen in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).  
  
> [!IMPORTANT]  
>  SharePoint 2010 SP1 muss installiert sein, bevor Sie PowerPivot für SharePoint oder eine SharePoint-Farm konfigurieren können, die einen [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Datenbankserver verwendet. Wenn Sie das Service Pack noch nicht installiert haben, holen Sie dies jetzt nach, bevor Sie mit der Serverkonfiguration beginnen.  
  
 PowerPivot für SharePoint muss installiert sein. Mindestens die Farmlösung muss bereitgestellt werden. Verwenden Sie das PowerPivot-Konfigurationstool oder das PowerShell-Skript, um die Farmlösung bereitzustellen. In diesem Thema erhalten Sie Anweisungen zu diesem Schritt.  
  
 Der Computer muss einer Domäne hinzugefügt werden. Die für Dienste angegebenen Konten müssen Domänenbenutzerkonten sein. Sie benötigen mindestens ein Domänenkonto für die PowerPivot-Dienstanwendung. Wenn Sie zusätzliche Dienste (z. B. Excel Services) konfigurieren, sollten Sie für alle bereitgestellten Dienste separate Konten besitzen.  
  
 Sie müssen Farmadministrator sein, um der Farm PowerPivot für SharePoint hinzuzufügen. Um der Farm Server und Anwendungen hinzuzufügen, müssen Sie die Passphrase kennen.  
  
##  <a name="deploywsp"></a> Schritt 1: Bereitstellen von PowerPivot-Lösungen  
 Es gibt zwei Lösungen, die installiert und bereitgestellt werden müssen: eine Farmlösung und eine Webanwendungslösung.  
  
 **Installieren und Bereitstellen der Farmlösung**  
  
 In der vorherigen Version wurde die Farmlösung von SQL Server-Setup installiert und bereitgestellt. In dieser Version müssen Sie die Farmlösung mit dem PowerPivot-Konfigurationstool oder dem PowerShell-Skript bereitstellen. Sie können die Farmlösung nicht mithilfe der Zentraladministration bereitstellen. Dies ist der einzige Schritt in der PowerPivot für SharePoint-Konfiguration, der nicht in der Zentraladministration ausgeführt werden kann. Nachdem die Farmlösung bereitgestellt wurde, können Sie die Zentraladministration und die Schritte in diesem Thema verwenden, um eine PowerPivot für SharePoint-Installation zu konfigurieren.  
  
 In diesem Schritt führen Sie PowerShell aus, um die Farmlösung zu installieren und bereitzustellen. Weitere Informationen finden Sie unter [PowerPivot-Konfiguration, die mithilfe von Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).  
  
1.  Öffnen Sie eine SharePoint 2010-Verwaltungsshell mithilfe der Option **Als Administrator ausführen** .  
  
2.  Führen Sie das erste Cmdlet aus:  
  
    ```  
    Add-SPSolution –LiteralPath “C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp”  
    ```  
  
     Das Cmdlet gibt den Namen der Lösung, deren Lösungs-ID und "Deployed=False" zurück. Im nächsten Schritt wird die Lösung bereitgestellt.  
  
3.  Führen Sie das zweite Cmdlet aus, um die Lösung bereitzustellen:  
  
    ```  
    Install-SPSolution –Identity PowerPivotFarm.wsp –GACDeployment -Force  
    ```  
  
 **Die webanwendungslösung bereitstellen**  
  
1.  Klicken Sie auf die Schaltfläche "Start", wählen Sie **Programme**Option **Microsoft SharePoint 2010-Produkte**, und wählen Sie dann **SharePoint 2010 Central Administration**.  
  
2.  Klicken Sie in der SharePoint 2010-Zentraladministration in Systemeinstellungen auf **Farmlösungen verwalten**.  
  
     Es sollten zwei separate Lösungspakete angezeigt werden: powerpivotfarm.wsp und powerpivotwebapp.wsp. Die erste Lösung (powerpivotfarm.wsp) muss bereits bereitgestellt worden sein. Nachdem die Lösung einmal bereitgestellt wurde, muss dieser Schritt nicht wiederholt werden. Die zweite Lösung (powerpivotwebapp.wsp) wird für die Zentraladministration bereitgestellt, muss jedoch manuell für jede SharePoint-Webanwendung bereitgestellt werden, die den PowerPivot-Datenzugriff unterstützt.  
  
3.  Klicken Sie auf **powerpivotwebapp.wsp**.  
  
4.  Klicken Sie auf **Lösung bereitstellen.**  
  
5.  In **bereitstellen für?**, wählen Sie die SharePoint-Webanwendung, die Sie die PowerPivot-funktionsunterstützung hinzufügen möchten.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Wiederholen Sie die Schritte für andere SharePoint-Webanwendungen, die den PowerPivot-Datenzugriff ebenfalls unterstützen.  
  
##  <a name="Geneva"></a> Schritt 2: Starten von Diensten auf dem Server  
 Eine PowerPivot für SharePoint-Bereitstellung erfordert, dass die Farm die folgenden Dienste einschließt: Dienste für Excel-Berechnungen, Secure Store Service und c2WTS (Claims to Windows Token Service).  
  
 Der Claims to Windows Token Service ist für Excel Services und PowerPivot für SharePoint erforderlich. Er wird verwendet, um Verbindungen zu externen Datenquellen herzustellen, die die Windows-Identität des aktuellen SharePoint-Benutzers verwenden. Dieser Dienst muss auf jedem SharePoint-Server ausgeführt werden, auf dem Excel Services oder PowerPivot für SharePoint aktiviert ist. Wenn der Dienst noch nicht gestartet wurde, müssen Sie ihn jetzt starten, um Excel Services zu aktivieren, damit authentifizierte Anforderungen an den PowerPivot-Systemdienst weitergeleitet werden können.  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Dienste auf dem Server verwalten**.  
  
2.  Starten Sie c2WTS (Claims to Windows Token Service).  
  
3.  Starten Sie die Dienste für Excel-Berechnungen.  
  
4.  Starten Sie den Secure Store Service.  
  
5.  Überprüfen Sie, ob sowohl SQL Server Analysis Services als auch der SQL Server PowerPivot-Systemdienst gestartet wurden.  
  
##  <a name="createapp"></a> Schritt 3: Erstellen einer PowerPivot-Dienstanwendung  
 Der nächste Schritt besteht darin, eine PowerPivot-Dienstanwendung zu erstellen.  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie im Menüband **Dienstanwendungen** auf **Neu**.  
  
3.  Wählen Sie **SQL Server PowerPivot-Dienstanwendung**. Wenn diese Option nicht in der Liste angezeigt wird, wurde PowerPivot für SharePoint nicht installiert oder die Lösung nicht bereitgestellt.  
  
4.  In der **erstellen neue PowerPivot-Dienstanwendung** Seite, geben Sie einen Namen für die Anwendung. Der Standardwert ist PowerPivotServiceApplication\<Anzahl >. Wenn Sie mehrere PowerPivot-Dienstanwendungen erstellen, hilft ein aussagekräftiger Name anderen Administratoren, den Verwendungszweck der Anwendung zu verstehen.  
  
5.  Erstellen Sie unter Anwendungspool einen neuen Anwendungspool, und wählen Sie ein Sicherheitskonto aus. Ein Domänenbenutzerkonto ist erforderlich.  
  
6.  In **Datenbankserver**, wählen Sie einen Datenbankserver, auf dem die dienstanwendungs-Datenbank erstellt. Der Standardwert entspricht der SQL Server-Datenbank-Engine-Instanz, die die Datenbanken für die Farmkonfiguration hostet.  
  
7.  In **Datenbanknamen**, der Standardwert ist PowerPivotServiceApplication1_\<Guid >. Der Standardname für die Datenbank entspricht dem Standardnamen der Dienstanwendung. Wenn Sie einen eindeutigen Dienstanwendungsnamen eingegeben haben, verwenden Sie eine ähnliche Benennungskonvention für den Datenbanknamen, damit Sie sie zusammen verwalten können.  
  
8.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie **SQL-Authentifizierung**auswählen, finden Sie im SharePoint-Administratorhandbuch bewährte Methoden zur Verwendung dieses Authentifizierungstyps in einer SharePoint-Bereitstellung.  
  
9. Aktivieren Sie das Kontrollkästchen **Proxy für diese PowerPivot-dienstanwendung zur Standardgruppe "Proxy" hinzufügen.** . Dadurch wird der Standard-Dienstverbindungsgruppe die Dienstanwendungsverbindung hinzugefügt. Es muss mindestens eine PowerPivot-Dienstanwendung in der Standardverbindungsgruppe vorhanden sein.  
  
     Wenn eine PowerPivot-Dienstanwendung bereits in der Standardverbindungsgruppe aufgeführt ist, fügen Sie dieser Gruppe keine zweite Dienstanwendung hinzu. Das Hinzufügen von zwei Dienstanwendungen desselben Typs zur Standardverbindungsgruppe ist keine unterstützte Konfiguration. Weitere Informationen zur Verwendung von zusätzlichen dienstanwendungen in einer Verbindungsgruppe finden Sie unter [Verbinden einer PowerPivot-Dienstanwendung zu einer SharePoint-Webanwendung in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
10. Klicken Sie auf **OK.** Der Dienst wird zusammen mit anderen verwalteten Diensten in der Dienstanwendungsliste der Farm angezeigt.  
  
##  <a name="ExcelServ"></a> Schritt 4: Aktivieren von Excel Services  
 PowerPivot für SharePoint erfordert Excel Services, um den PowerPivot-Datenzugriff in der Farm zu unterstützen. Sie können feststellen, ob Excel Services bereits aktiviert sind, indem Sie überprüfen, ob die Excel Services-Anwendung in der Liste der Dienstanwendungen in der Zentraladministration angezeigt wird. Falls Excel Services nicht aufgeführt sind, führen Sie folgende Schritte aus, um die Anwendung jetzt zu aktivieren.  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie im Menüband Dienstanwendungen unter Erstellen auf **neu**.  
  
3.  Wählen Sie **Excel Services-Anwendung**.  
  
4.  Geben Sie unter Neue Excel Services-Anwendung erstellen einen Namen ein (z. B. Excel Services-Anwendung).  
  
5.  Wählen Sie unter Anwendungspool die Option Neuen Anwendungspool erstellen, und geben Sie ihm einen aussagekräftigen Namen (z. B., Excel Services-Anwendungspool).  
  
6.  Wählen Sie ein Windows-Domänenbenutzerkonto für diese Anwendungspoolidentität unter Konfigurierbar aus.  
  
7.  Lassen Sie das Standardkontrollkästchen aktiviert, das der Standarddienstverbindungsliste den Dienstanwendungsproxy hinzufügt.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie auf die Excel Services-Anwendung, die Sie gerade erstellt haben.  
  
10. Klicken Sie auf **Vertrauenswürdige Dateispeicherorte** und auf dieser Seite Wählen Sie den vertrauenswürdigen Speicherort. (Dies wird in der Regel als aufgeführt **http://** in der Spalte Adresse.) Um sicherzustellen, dass sowohl der Excel Services- als auch PowerPivot-Dienst Zugriff auf die Arbeitsmappe haben, müssen Sie SharePoint als Speicherort einschließen, dem von Excel Services vertraut wird. Der PowerPivot-Systemdienst kann nicht auf Arbeitsmappen zugreifen, die außerhalb einer SharePoint-Farm gespeichert sind.  
  
11. Legen Sie die Eigenschaften der Arbeitsmappe im Bereich **maximale Arbeitsmappengröße** auf 50.  
  
12. Legen Sie unter Externe Daten **können externe Daten** zu **Vertrauenswürdige Datenverbindungsbibliotheken und eingebettete**. Diese Einstellung ist für den PowerPivot-Datenzugriff in einer Arbeitsmappe erforderlich.  
  
13. Deaktivieren der **beim Aktualisieren warnen** Kontrollkästchen, um Vorschaubilder einzelner Arbeitsblätter im PowerPivot-Katalog zu ermöglichen. Wenn Sie die Warnung beibehalten möchten und in den Einstellungen der Arbeitsmappe Beim Öffnen aktualisieren aktiviert ist, können Sie anstatt der Seiten in der Arbeitsmappe ein einzelnes Vorschaubild der Warnung erhalten.  
  
14. Klicken Sie auf **OK**.  
  
##  <a name="SSS"></a> Schritt 5: Aktivieren von Secure Store Service und Konfigurieren der Datenaktualisierung  
 PowerPivot für SharePoint erfordert den Secure Store Service zum Speichern von Anmeldeinformationen und das Konto für die unbeaufsichtigte Ausführung zur Datenaktualisierung. Sie können feststellen, ob Secure Store Service bereits aktiviert ist, indem Sie überprüfen, ob er in der Liste der Dienstanwendungen angezeigt wird.  
  
> [!IMPORTANT]  
>  Wenn Secure Store Service aktiviert ist, sollten Sie trotzdem überprüfen, ob ein Hauptschlüssel dafür generiert wurde. Anweisungen finden Sie unter Teil 2: Generieren des Hauptschlüssels im folgenden Verfahren.  
  
 Wenn Secure Store Service nicht aufgeführt ist, führen Sie folgende Schritte aus, um ihn jetzt zu aktivieren. Arbeitsmappenautoren und Dokumentbesitzer können auf einen breiteren Bereich von Datenquellenverbindungsoptionen zugreifen, indem sie Einmaliges Anmelden aktivieren, wenn sie eine Datenaktualisierung für ihre veröffentlichten Arbeitsmappen planen.  
  
##### <a name="part-1-enable-secure-store-service"></a>Teil 1: Aktivieren von Secure Store Service  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie im Menüband Dienstanwendungen unter Erstellen auf **neu**.  
  
3.  Wählen Sie **Secure Store Service-**.  
  
4.  In der **Secure Store-Anwendung erstellen** Seite, geben Sie einen Namen für die Anwendung.  
  
5.  In **Datenbank**, geben Sie die SQL Server-Instanz, die die Datenbank für diese dienstanwendung hostet. Der Standardwert entspricht der SQL Server-Datenbank-Engine-Instanz, die die Datenbanken für die Farmkonfiguration hostet.  
  
6.  In **Datenbanknamen**, geben Sie den Namen der dienstanwendungs-Datenbank. Der Standardwert entspricht Secure_Store_Service_DB_\<Guid >. Der Standardname entspricht dem Standardnamen der Dienstanwendung. Wenn Sie einen eindeutigen Dienstanwendungsnamen eingegeben haben, verwenden Sie eine ähnliche Benennungskonvention für den Datenbanknamen, damit Sie sie zusammen verwalten können.  
  
7.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie die SQL-Authentifizierung auswählen, finden Sie im SharePoint-Administratorhandbuch eine Anleitung zum Verwenden des Authentifizierungstyps in der Farm.  
  
8.  Wählen Sie unter Anwendungspool **neuen Anwendungspool erstellen.** Geben Sie einen aussagekräftigen Namen an, der anderen Serveradministratoren hilft, den Verwendungszweck des Anwendungspools zu erkennen.  
  
9. Wählen Sie ein Sicherheitskonto für den Anwendungspool aus. Geben Sie ein verwaltetes Konto an, das als Domänenbenutzerkonto verwendet werden soll.  
  
10. Akzeptieren Sie die übrigen Standardwerte, und klicken Sie dann auf **OK.** Die Dienstanwendung wird zusammen mit anderen verwalteten Diensten in der Dienstanwendungsliste der Farm angezeigt.  
  
##### <a name="part-2-generate-the-master-key"></a>Teil 2: Generieren des Hauptschlüssels  
  
1.  Klicken Sie in der Liste auf die Secure Store Service-Anwendung.  
  
2.  Klicken Sie im Menüband Dienstanwendungen auf **verwalten**.  
  
3.  Klicken Sie unter Schlüsselverwaltung auf **neuen Schlüssel generieren**.  
  
4.  Geben Sie eine Passphrase ein, und bestätigen Sie sie dann. Die Passphrase wird zum Hinzufügen zusätzlicher freigegebener Secure Store Service-Anwendungen verwendet.  
  
5.  Klicken Sie auf **OK**.  
  
##### <a name="part-3-configure-the-unattended-powerpivot-data-refresh-account"></a>Teil 3: Konfigurieren des PowerPivot-Kontos für die unbeaufsichtigte Datenaktualisierung  
 Häufig muss ein Konto für die unbeaufsichtigte Datenaktualisierung für den PowerPivot-Datenzugriff erstellt werden, damit während der Datenaktualisierung auf externe Daten zugegriffen werden kann. Wenn Kerberos z. B. nicht aktiviert ist, müssen Sie ein unbeaufsichtigtes Konto erstellen, über das der PowerPivot-Dienst eine Verbindung mit externen Datenquellen herstellen kann.  
  
 Anweisungen zum Erstellen für die unbeaufsichtigte PowerPivot-Daten für Aktualisierung von-Konto oder andere gespeicherte Anmeldeinformationen, die verwendet werden Daten zu aktualisieren, finden Sie unter [konfigurieren Sie die PowerPivot-datenaktualisierungskonto &#40;PowerPivot für SharePoint&#41; ](../../analysis-services/configure-unattended-data-refresh-account-powerpivot-sharepoint.md) und [konfigurieren gespeicherter Anmeldeinformationen für die PowerPivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../../../2014/analysis-services/configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="Usage"></a> Schritt 6: Aktivieren der Sammlung von Verwendungsdaten  
 PowerPivot für SharePoint erfasst Informationen zur PowerPivot-Verwendung überall in der Farm mithilfe der Infrastruktur zur Sammlung von SharePoint-Verwendungsdaten. Obwohl Verwendungsdaten immer Teil einer SharePoint-Installation sind, müssen sie möglicherweise aktiviert werden, damit sie verwendet werden können. Anweisungen hierzu finden Sie unter [konfigurieren Sammlung von Verwendungsdaten für &#40;PowerPivot für SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
##  <a name="Upload"></a> Schritt 7: Erhöhung maximale Uploadgröße für SharePoint-Webanwendungen und Excel Services  
 Da PowerPivot-Arbeitsmappen sehr groß werden können, kann es sinnvoll sein, die maximale Dateigröße zu erhöhen. Sie können zwei Einstellungen für die Dateigröße konfigurieren: Maximale Uploadgröße für die Webanwendung und Maximale Arbeitsmappengröße in Excel Services. Die maximale Dateigröße sollte in beiden Anwendungen auf den gleichen Wert festgelegt werden. Anweisungen hierzu finden Sie unter [konfigurieren maximale Dateiuploadgröße &#40;PowerPivot für SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).  
  
##  <a name="activatePP"></a> Schritt 8: Aktivieren der PowerPivot-Funktionsintegration für Websitesammlungen  
 Die Funktionsaktivierung auf der Ebene der Websitesammlung stellt Anwendungsseiten und Vorlagen zur Verfügung, z. B. Konfigurationsseiten für geplante Datenaktualisierungen und Anwendungsseiten für den PowerPivot-Katalog und Datenfeedbibliotheken.  
  
1.  Klicken Sie auf einer SharePoint-Website auf **Websiteaktionen**.  
  
     Standardmäßig wird auf SharePoint-Webanwendungen über Port 80 zugegriffen. Dies bedeutet, dass Sie häufig eine SharePoint-Website zugreifen können, durch Eingabe von http://\<Computername > um die Stammwebsitesammlung zu öffnen.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie unter Websitesammlungsverwaltung auf **Websitesammlungsfeatures**.  
  
4.  Führen Sie einen Bildlauf nach unten bis Sie finden **PowerPivot-Integration für Webseitensammlungen**.  
  
5.  Klicken Sie auf **Aktivieren**.  
  
6.  Wiederholen Sie den Schritt für zusätzliche Websitesammlungen, indem Sie jede Website öffnen und auf **Websiteaktionen**klicken.  
  
 Weitere Informationen finden Sie unter [PowerPivot-Funktionsintegration für Websitesammlungen in der Zentraladministration aktivieren](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md).  
  
##  <a name="bkmk_redist"></a> Schritt 9: Installieren der SQL Server 2008 R2-Version des OLE DB-Anbieters auf einer SQL Server 2012 PowerPivot für SharePoint-Instanz  
 Wenn Sie ältere und neuere Versionen von PowerPivot-Arbeitsmappen parallel auf demselben Server ausführen möchten, müssen Sie den im Lieferumfang von SQL Server 2008 R2 enthaltenen Analysis Services OLE-DB-Anbieter auf einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot für SharePoint-Server installieren.  
  
 Durch die Installation des Anbieters funktionieren Arbeitsmappen, die in der Datenverbindungszeichenfolge auf MSOLAP.4 verweisen, erwartungsgemäß auf einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot-Server. Die Installation des SQL Server 2008 R2 OLE DB-Anbieters ist eine alternative Methode zum Aktualisieren der in einer früheren Version von PowerPivot für Excel erstellten Arbeitsmappen.  
  
 Sie können den Anbieter von [SQL Server 2008 R2 Feature Pack-Seite](http://go.microsoft.com/fwlink/?LinkId=159570). Suchen Sie nach **Microsoft® Analysis Services OLE DB-Anbieter für Microsoft® SQL Server® 2008 R2**, und klicken Sie dann Herunterladen der X64 Paket mit der `SQLServer2008_ASOLEDB10.msi` Installationsprogramm.  
  
 Weitere Informationen zum Installieren des Anbieters, einschließlich der Überprüfungsschritte, finden Sie unter [Installieren von Analysis Services OLE DB-Anbieter auf SharePoint-Servern](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
##  <a name="verifyinstall"></a> Schritt 10: Überprüfen der Installation  
 Die PowerPivot-Abfrageverarbeitung in der Farm tritt auf, wenn ein Benutzer oder eine Anwendung eine Excel-Arbeitsmappe öffnet, die PowerPivot-Daten enthält. Sie können Seiten auf SharePoint-Sites kontrollieren, um zu überprüfen, ob PowerPivot-Funktionen verfügbar sind. Um jedoch eine Installation vollständig zu überprüfen, müssen Sie eine PowerPivot-Arbeitsmappe haben, die Sie in SharePoint veröffentlichen können und auf die Sie über eine Bibliothek zugreifen können. Zu Testzwecken können Sie eine Beispielarbeitsmappe veröffentlichen, die bereits PowerPivot-Daten enthält, und damit überprüfen, ob die SharePoint-Integration ordnungsgemäß konfiguriert wurde.  
  
 Um die PowerPivot-Integration in eine SharePoint-Website zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Öffnen Sie in einem Browser die Webanwendung, die Sie erstellt haben. Wenn Sie Standardwerte verwendet haben, können Sie angeben, dass http://\<Ihr Computername > in der URL-Adresse.  
  
2.  Überprüfen Sie, ob der PowerPivot-Datenzugriff und die Verarbeitungsfunktionen in der Anwendung verfügbar sind. Überprüfen Sie hierzu das Vorhandensein von durch PowerPivot bereitgestellte Bibliotheksvorlagen:  
  
    1.  Klicken Sie unter Websiteaktionen auf **Weitere Optionen...** .  
  
    2.  Bibliotheken sollte **Datenfeedbibliothek** und **PowerPivot-Katalog**. Diese Bibliotheksvorlagen werden von der PowerPivot-Funktion bereitgestellt und sind in der Bibliothekenliste sichtbar, falls die Funktion ordnungsgemäß integriert wurde.  
  
 Um den PowerPivot-Datenzugriff auf dem Server zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Laden Sie eine PowerPivot-Arbeitsmappe in den PowerPivot-Katalog oder in eine beliebige SharePoint-Bibliothek hoch.  
  
2.  Klicken Sie auf das Dokument, um es von der Bibliothek aus zu öffnen.  
  
3.  Klicken Sie auf einen Slicer, oder filtern Sie die Daten, um eine PowerPivot-Abfrage zu starten. Der Server lädt PowerPivot-Daten im Hintergrund und gibt die Ergebnisse zurück. Im nächsten Schritt stellen Sie eine Verbindung mit dem Server her, um zu überprüfen, ob die Daten geladen und zwischengespeichert wurden.  
  
4.  Starten Sie SQL Server Management Studio im Startmenü in der Programmgruppe Microsoft SQL Server 2008 R2. Wenn dieses Tool nicht auf dem Server installiert ist, können Sie mit dem letzten Schritt fortfahren, um das Vorhandensein zwischengespeicherter Dateien zu bestätigen.  
  
5.  Wählen Sie unter Servertyp die Option **Analysis Services**aus.  
  
6.  Geben Sie im Server-Namen,  **\<Servername > \powerpivot**, wobei  **\<Servername >** ist der Name des Computers, der dem PowerPivot für SharePoint-Installation ist.  
  
7.  Klicken Sie auf **Verbinden**.  
  
8.  Klicken Sie im Objekt-Explorer auf **Datenbanken** zum Anzeigen der Liste der PowerPivot-Datendateien, die geladen werden.  
  
9. Überprüfen Sie im Computerdateisystem den folgenden Ordner, um zu bestimmen, ob Dateien auf dem Datenträger zwischengespeichert wurden. Das Vorhandensein zwischengespeicherter Dateien ist eine weitere Bestätigung, dass die Bereitstellung betriebsbereit ist. Um den Dateicache anzuzeigen, wechseln Sie zum Ordner \Programme\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup.  
  
##  <a name="nextsteps"></a> Schritte nach der Installation  
 Nachdem Sie die Installation überprüft haben, beenden Sie die Dienstkonfiguration durch das Erstellen eines PowerPivot-Katalogs oder durch Anpassen einzelner Konfigurationseinstellungen. Um die Serverkomponenten, die Sie gerade installiert haben, vollständig zu nutzen, können Sie [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] herunterladen und dann Ihre erste PowerPivot-Arbeitsmappe erstellen und veröffentlichen.  
  
### <a name="install-data-providers-used-for-data-refresh"></a>Installieren von für die Datenaktualisierung verwendeten Datenanbietern  
 Wenn Sie die Datenaktualisierung aktiviert haben, benötigt der Server die gleichen Datenanbieter für den externen Datenzugriff, die auch von der PowerPivot-Clientanwendung zum Importieren der ursprünglichen Daten verwendet wurden. Wenn die Daten beispielsweise ursprünglich mit einem 32-Bit-Anbieter importiert wurden, ist für die serverseitige Datenaktualisierung auch ein 32-Bit-Anbieter erforderlich, wenn sie auf die gleiche externe Datenquelle zugreift. Weitere Informationen finden Sie unter [PowerPivot-Datenaktualisierung mit SharePoint 2010](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md).  
  
### <a name="install-adonet-data-services"></a>Installieren von ADO.NET Data Services  
 Sie müssen ADO.NET Data Services 3.5 SP1 installieren, wenn Sie SharePoint-Listen als Datenfeeds exportieren möchten. Anweisungen hierzu finden Sie unter [Installieren von ADO.NET Data Services zur Unterstützung von datenfeedexporte von SharePoint-Listen](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
### <a name="create-a-powerpivot-gallery"></a>Erstellen eines PowerPivot-Katalogs  
 Beim PowerPivot-Katalog handelt es sich um eine Bibliothek, die Vorschau- und Präsentationsoptionen zum Anzeigen von PowerPivot-Arbeitsmappen auf einer SharePoint-Site enthält. Das Verwenden des PowerPivot-Katalogs zum Veröffentlichen und Anzeigen von PowerPivot-Arbeitsmappen wird für die Vorschaufunktion empfohlen. Wenn Sie überdies auch Reporting Services auf dem gleichen SharePoint-Server bereitgestellt haben, bietet ein PowerPivot-Katalog Benutzerfreundlichkeit beim Erstellen von Berichten. Sie können den Berichts-Generator innerhalb des PowerPivot-Katalogs starten, um als Grundlage für einen neuen Bericht eine veröffentlichte PowerPivot-Arbeitsmappe zu verwenden. Weitere Informationen zum Erstellen und Verwenden der Bibliotheks finden Sie unter [erstellen und Anpassen von PowerPivot-Katalog](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md) und [Verwenden des PowerPivot-Katalogs](../../analysis-services/power-pivot-sharepoint/use-power-pivot-gallery.md).  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Erstellen von zusätzlichen vertrauenswürdigen Websites in Excel Services  
 Sie können vertrauenswürdige Websites in Excel Services hinzufügen, um die Berechtigungen und Konfigurationseinstellungen auf Websites zu variieren, die Excel-Arbeitsmappen und PowerPivot-Daten bereitstellen. Weitere Informationen finden Sie unter [Create a trusted location for PowerPivot sites in Central Administration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
### <a name="tune-configuration-settings"></a>Optimieren von Konfigurationseinstellungen  
 Eine PowerPivot-Dienstanwendung wird mit Standardeigenschaften und -werten erstellt. Sie können Konfigurationseinstellungen für einzelne Dienstanwendungen ändern, um die Methodik zu ändern, anhand der die Anforderungen zugeordnet werden. Außerdem können Sie Servertimeouts festlegen, die Schwellenwerte für Abfrageantwortberichtsereignisse ändern oder festlegen, wie lange die Verwendungsdaten beibehalten werden sollen. Weitere Informationen zur Konfiguration in der Zentraladministration oder zum Verwenden von PowerPivot-Funktionen in SharePoint-Webanwendungen finden Sie unter [PowerPivot-Serververwaltung und-Konfiguration in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
### <a name="install-powerpivot-for-excel-and-build-a-powerpivot-workbook"></a>Installieren von PowerPivot für Excel und Erstellen einer PowerPivot-Arbeitsmappe  
 Nachdem Sie die Serverkomponenten in einer Farm installiert haben, können Sie die erste Excel 2010-Arbeitsmappe erstellen, die eingebettete PowerPivot-Daten verwendet, und sie dann in einer SharePoint-Bibliothek einer Webanwendung veröffentlichen. Bevor Sie Excel-Arbeitsmappen erstellen können, die PowerPivot-Daten enthalten, müssen Sie mit einer Installation von Excel 2010 beginnen, gefolgt vom PowerPivot-Add-In für Excel, das Excel erweitert, um den PowerPivot-Datenimport und die Datenbereicherung zu unterstützen.  
  
### <a name="add-servers-or-applications"></a>Hinzufügen von Servern oder Anwendungen  
 Wenn Sie die PowerPivot-Lösung bereitstellen, wird die Funktionsintegration auf der Websitesammlungsebene für alle Websitesammlungen in der Webanwendung aktiviert. Wenn Sie im Laufe der Zeit neue Webanwendungen erstellen, müssen Sie die powerpivotwebapp-Lösung für jede Anwendung bereitstellen. Anweisungen hierzu finden Sie unter [Bereitstellen der PowerPivot-Lösungen in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md).  
  
 Je nach Konfiguration der PowerPivot-Dienstanwendung wird der PowerPivot-Systemdienst der Standardverbindungsgruppe hinzugefügt und somit für alle Webanwendungen verfügbar gemacht, die Standardverbindungen verwenden. Wenn Sie die Webanwendungen jedoch so konfiguriert haben, dass sie benutzerdefinierte Verbindungslisten für Dienstanwendungen verwenden, müssen Sie jeder SharePoint-Webanwendung, für die Sie die PowerPivot-Datenverarbeitung aktivieren möchten, die PowerPivot-Dienstanwendung hinzufügen. Weitere Informationen finden Sie unter [Verbinden einer PowerPivot-Dienstanwendung zu einer SharePoint-Webanwendung in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
 Wenn Sie mit der Zeit feststellen, dass zusätzlicher Datenspeicher und zusätzliche Verarbeitungskapazität erforderlich sind, können Sie der Farm eine zweite Serverinstanz mit PowerPivot für SharePoint hinzufügen. Der Installationsvorgang ist fast identisch mit den Schritten, die Sie ausgeführt haben, um den ersten Server hinzuzufügen, mit Ausnahme der Anforderungen, wie Sie Instanznamen und Dienstkontoinformationen angeben. Anleitungen hierzu finden Sie [Bereitstellungsprüfliste: Horizontales durch Hinzufügen von PowerPivot-Server zu einer SharePoint 2010-Farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Von den Editionen von SQLServer 2014 unterstützte Funktionen](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Konfigurieren von PowerPivot-Dienstkonten](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)   
 [Erstellen und Konfigurieren einer PowerPivot-Dienstanwendung in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)   
 [Bereitstellen von PowerPivot-Lösungen in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)   
 [Aktivieren der PowerPivot-Funktionsintegration für Websitesammlungen in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md)   
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
