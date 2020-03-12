---
title: Anfängliche Konfiguration (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 24a52b9dd190032a55306c1fe738c3c1e1787dad
ms.sourcegitcommit: 59c09dbe29882cbed539229a9bc1de381a5a4471
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79112219"
---
# <a name="initial-configuration-powerpivot-for-sharepoint"></a>Anfängliche Konfiguration (PowerPivot für SharePoint)
  Verwenden Sie die Schritte in diesem Thema, um eine ursprüngliche Installation von PowerPivot für SharePoint zu konfigurieren. Die einfachste Möglichkeit zur Konfiguration einer ursprünglichen Installation ist die Verwendung des PowerPivot-Konfigurationstools. Dieses Tool automatisiert alle unten beschriebenen Konfigurationsschritte.  
  
 Wenn Sie mehr Kontrolle über die Konfiguration des Servers haben möchten, können Sie alternativ die Zentraladministration und die Informationen in diesem Thema verwenden, um jeden Schritt einzeln auszuführen.  
  
 
  
## <a name="prerequisites"></a>Voraussetzungen  
 Der SharePoint-Server muss im SharePoint-Setup mit der Installationsoption Serverfarm installiert worden sein. Ein eigenständiger SharePoint-Server, der eine integrierte Datenbank verwendet, wird nicht unterstützt. Weitere Informationen finden Sie unter [Anleitung für die Verwendung von SQL Server BI-Funktionen in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).  
  
> [!IMPORTANT]  
>  SharePoint 2010 SP1 muss installiert sein, bevor Sie PowerPivot für SharePoint oder eine SharePoint-Farm konfigurieren können, die einen [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Datenbankserver verwendet. Wenn Sie das Service Pack noch nicht installiert haben, holen Sie dies jetzt nach, bevor Sie mit der Serverkonfiguration beginnen.  
  
 PowerPivot für SharePoint muss installiert sein. Mindestens die Farmlösung muss bereitgestellt werden. Verwenden Sie das PowerPivot-Konfigurationstool oder das PowerShell-Skript, um die Farmlösung bereitzustellen. In diesem Thema erhalten Sie Anweisungen zu diesem Schritt.  
  
 Der Computer muss einer Domäne hinzugefügt werden. Die für Dienste angegebenen Konten müssen Domänenbenutzerkonten sein. Sie benötigen mindestens ein Domänenkonto für die PowerPivot-Dienstanwendung. Wenn Sie zusätzliche Dienste (z. B. Excel Services) konfigurieren, sollten Sie für alle bereitgestellten Dienste separate Konten besitzen.  
  
 Sie müssen Farmadministrator sein, um der Farm PowerPivot für SharePoint hinzuzufügen. Um der Farm Server und Anwendungen hinzuzufügen, müssen Sie die Passphrase kennen.  
  
##  <a name="deploywsp"></a>Schritt 1: Bereitstellen von Power Pivot-Lösungen  
 Es gibt zwei Lösungen, die installiert und bereitgestellt werden müssen: eine Farmlösung und eine Webanwendungslösung.  
  
### <a name="install-and-deploy-the-farm-solution"></a>Installieren und Bereitstellen die Farmlösung
  
 In der vorherigen Version wurde die Farmlösung von SQL Server-Setup installiert und bereitgestellt. In dieser Version müssen Sie die Farmlösung mit dem PowerPivot-Konfigurationstool oder dem PowerShell-Skript bereitstellen. Sie können die Farmlösung nicht mithilfe der Zentraladministration bereitstellen. Dies ist der einzige Schritt in der PowerPivot für SharePoint-Konfiguration, der nicht in der Zentraladministration ausgeführt werden kann. Nachdem die Farmlösung bereitgestellt wurde, können Sie die Zentraladministration und die Schritte in diesem Thema verwenden, um eine PowerPivot für SharePoint-Installation zu konfigurieren.  
  
 In diesem Schritt führen Sie PowerShell aus, um die Farmlösung zu installieren und bereitzustellen. Weitere Informationen finden Sie unter [Power Pivot-Konfiguration mit Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).  
  
1.  Öffnen Sie eine SharePoint 2010-Verwaltungsshell mithilfe der Option **Als Administrator ausführen** .  
  
2.  Führen Sie das erste Cmdlet aus:  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     Das Cmdlet gibt den Namen der Lösung, deren Lösungs-ID und "Deployed=False" zurück. Im nächsten Schritt wird die Lösung bereitgestellt.  
  
3.  Führen Sie das zweite Cmdlet aus, um die Lösung bereitzustellen:  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
### <a name="deploy-the-web-application-solution"></a>Bereitstellen der Webanwendungslösung
  
1.  Klicken Sie auf die Schaltfläche Start, wählen Sie **Alle Programme**und dann **Microsoft SharePoint-Produkte 2010**aus, und wählen Sie dann **SharePoint 2010-zentral Administration**aus.  
  
2.  Klicken Sie in der SharePoint 2010-Zentraladministration in Systemeinstellungen auf **Farmlösungen verwalten**.  
  
     Es sollten zwei separate Lösungspakete angezeigt werden: powerpivotfarm.wsp und powerpivotwebapp.wsp. Die erste Lösung (powerpivotfarm.wsp) muss bereits bereitgestellt worden sein. Nachdem die Lösung einmal bereitgestellt wurde, muss dieser Schritt nicht wiederholt werden. Die zweite Lösung (powerpivotwebapp.wsp) wird für die Zentraladministration bereitgestellt, muss jedoch manuell für jede SharePoint-Webanwendung bereitgestellt werden, die den PowerPivot-Datenzugriff unterstützt.  
  
3.  Klicken Sie auf **powerpivotwebapp. wsp**.  
  
4.  Klicken Sie auf Lösung bereitstellen **.**  
  
5.  Wählen Sie unter Bereitstellen **für?** die SharePoint-Webanwendung aus, der Sie die Unterstützung für Power Pivot-Funktionen hinzufügen möchten.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Wiederholen Sie die Schritte für andere SharePoint-Webanwendungen, die den PowerPivot-Datenzugriff ebenfalls unterstützen.  
  
##  <a name="Geneva"></a>Schritt 2: Starten von Diensten auf dem Server  
 Eine PowerPivot für SharePoint-Bereitstellung erfordert, dass die Farm die folgenden Dienste einschließt: Dienste für Excel-Berechnungen, Secure Store Service und c2WTS (Claims to Windows Token Service).  
  
 Der Claims to Windows Token Service ist für Excel Services und PowerPivot für SharePoint erforderlich. Er wird verwendet, um Verbindungen zu externen Datenquellen herzustellen, die die Windows-Identität des aktuellen SharePoint-Benutzers verwenden. Dieser Dienst muss auf jedem SharePoint-Server ausgeführt werden, auf dem Excel Services oder PowerPivot für SharePoint aktiviert ist. Wenn der Dienst noch nicht gestartet wurde, müssen Sie ihn jetzt starten, um Excel Services zu aktivieren, damit authentifizierte Anforderungen an den PowerPivot-Systemdienst weitergeleitet werden können.  
  
1.  Klicken Sie in der zentral Administration unter System Einstellungen auf **Dienste auf dem Server verwalten**.  
  
2.  Starten Sie c2WTS (Claims to Windows Token Service).  
  
3.  Starten Sie die Dienste für Excel-Berechnungen.  
  
4.  Starten Sie den Secure Store Service.  
  
5.  Überprüfen Sie, ob sowohl SQL Server Analysis Services als auch der SQL Server PowerPivot-Systemdienst gestartet wurden.  
  
##  <a name="createapp"></a>Schritt 3: Erstellen einer Power Pivot-Dienst Anwendung  
 Der nächste Schritt besteht darin, eine PowerPivot-Dienstanwendung zu erstellen.  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie im Menüband **Dienstanwendungen** auf **Neu**.  
  
3.  Wählen Sie **SQL Server Power Pivot-Dienst Anwendung**aus. Wenn diese Option nicht in der Liste angezeigt wird, wurde PowerPivot für SharePoint nicht installiert oder die Lösung nicht bereitgestellt.  
  
4.  Geben Sie auf der Seite **neue Power Pivot-Dienst Anwendung erstellen** einen Namen für die Anwendung ein. Der Standardwert ist PowerPivotServiceApplication\<Number>. Wenn Sie mehrere PowerPivot-Dienstanwendungen erstellen, hilft ein aussagekräftiger Name anderen Administratoren, den Verwendungszweck der Anwendung zu verstehen.  
  
5.  Erstellen Sie unter Anwendungspool einen neuen Anwendungspool, und wählen Sie ein Sicherheitskonto aus. Ein Domänenbenutzerkonto ist erforderlich.  
  
6.  Wählen Sie unter **Datenbankserver**einen Datenbankserver aus, auf dem die-Dienst Anwendungsdatenbank erstellt werden soll. Der Standardwert entspricht der SQL Server-Datenbank-Engine-Instanz, die die Datenbanken für die Farmkonfiguration hostet.  
  
7.  Der Standardwert unter **Datenbankname**ist PowerPivotServiceApplication1_\<GUID>. Der Standardname für die Datenbank entspricht dem Standardnamen der Dienstanwendung. Wenn Sie einen eindeutigen Dienstanwendungsnamen eingegeben haben, verwenden Sie eine ähnliche Benennungskonvention für den Datenbanknamen, damit Sie sie zusammen verwalten können.  
  
8.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie **SQL-Authentifizierung**auswählen, finden Sie im SharePoint-Administratorhandbuch bewährte Methoden zur Verwendung dieses Authentifizierungstyps in einer SharePoint-Bereitstellung.  
  
9. Aktivieren Sie dieses Kontrollkästchen, um der **Standard Proxy Gruppe den Proxy für diese Power Pivot-Dienst Anwendung hinzuzufügen.** . Dadurch wird der Standard-Dienstverbindungsgruppe die Dienstanwendungsverbindung hinzugefügt. Es muss mindestens eine PowerPivot-Dienstanwendung in der Standardverbindungsgruppe vorhanden sein.  
  
     Wenn eine PowerPivot-Dienstanwendung bereits in der Standardverbindungsgruppe aufgeführt ist, fügen Sie dieser Gruppe keine zweite Dienstanwendung hinzu. Das Hinzufügen von zwei Dienstanwendungen desselben Typs zur Standardverbindungsgruppe ist keine unterstützte Konfiguration. Weitere Informationen zur Verwendung zusätzlicher Dienst Anwendungen in einer Verbindungsgruppe finden Sie unter [Verbinden einer Power Pivot-Dienst Anwendung mit einer SharePoint-Webanwendung in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca).  
  
10. Klicken Sie auf **OK**. Der Dienst wird zusammen mit anderen verwalteten Diensten in der Dienstanwendungsliste der Farm angezeigt.  
  
##  <a name="ExcelServ"></a>Schritt 4: Aktivieren von Excel Services  
 PowerPivot für SharePoint erfordert Excel Services, um den PowerPivot-Datenzugriff in der Farm zu unterstützen. Sie können feststellen, ob Excel Services bereits aktiviert sind, indem Sie überprüfen, ob die Excel Services-Anwendung in der Liste der Dienstanwendungen in der Zentraladministration angezeigt wird. Falls Excel Services nicht aufgeführt sind, führen Sie folgende Schritte aus, um die Anwendung jetzt zu aktivieren.  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie im Menüband Dienst Anwendungen unter Erstellen auf **neu**.  
  
3.  Wählen Sie **Excel Services-Anwendung**aus.  
  
4.  Geben Sie unter Neue Excel Services-Anwendung erstellen einen Namen ein (z. B. Excel Services-Anwendung).  
  
5.  Wählen Sie unter Anwendungspool die Option Neuen Anwendungspool erstellen, und geben Sie ihm einen aussagekräftigen Namen (z. B., Excel Services-Anwendungspool).  
  
6.  Wählen Sie ein Windows-Domänenbenutzerkonto für diese Anwendungspoolidentität unter Konfigurierbar aus.  
  
7.  Lassen Sie das Standardkontrollkästchen aktiviert, das der Standarddienstverbindungsliste den Dienstanwendungsproxy hinzufügt.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie auf die Excel Services-Anwendung, die Sie gerade erstellt haben.  
  
10. Klicken Sie auf **Vertrauenswürdige Dateispeicher Orte** , und wählen Sie auf dieser Seite ihren vertrauenswürdigen Speicherort (In der Regel wird dies in der Adressspalte als **http://** aufgeführt.) Um sicherzustellen, dass sowohl Excel Services als auch der Power Pivot-Dienst Zugriff auf die-Arbeitsmappe haben, müssen Sie SharePoint als vertrauenswürdigen Excel Services-Speicherort einschließen. Der PowerPivot-Systemdienst kann nicht auf Arbeitsmappen zugreifen, die außerhalb einer SharePoint-Farm gespeichert sind.  
  
11. Legen Sie im Bereich Eigenschaften der Arbeitsmappe die **Maximale Arbeitsmappengröße** auf 50 fest.  
  
12. Legen Sie unter Externe Daten die Option **externe Daten zulassen** auf **vertrauenswürdige Daten Verbindungs Bibliotheken und Embedded**fest. Diese Einstellung ist für den PowerPivot-Datenzugriff in einer Arbeitsmappe erforderlich.  
  
13. Deaktivieren Sie das Kontrollkästchen **Warnung bei Datenaktualisierung** , um Vorschaubilder einzelner Arbeitsblätter im Power Pivot-Katalog zuzulassen. Wenn Sie die Warnung beibehalten möchten und in den Einstellungen der Arbeitsmappe Beim Öffnen aktualisieren aktiviert ist, können Sie anstatt der Seiten in der Arbeitsmappe ein einzelnes Vorschaubild der Warnung erhalten.  
  
14. Klicken Sie auf **OK**.  
  
##  <a name="SSS"></a>Schritt 5: Aktivieren von einmaliges Anmelden und Konfigurieren der Datenaktualisierung  
 PowerPivot für SharePoint erfordert den Secure Store Service zum Speichern von Anmeldeinformationen und das Konto für die unbeaufsichtigte Ausführung zur Datenaktualisierung. Sie können feststellen, ob Secure Store Service bereits aktiviert ist, indem Sie überprüfen, ob er in der Liste der Dienstanwendungen angezeigt wird.  
  
> [!IMPORTANT]  
>  Wenn Secure Store Service aktiviert ist, sollten Sie trotzdem überprüfen, ob ein Hauptschlüssel dafür generiert wurde. Anweisungen finden Sie unter Teil 2: Generieren des Hauptschlüssels im folgenden Verfahren.  
  
 Wenn Secure Store Service nicht aufgeführt ist, führen Sie folgende Schritte aus, um ihn jetzt zu aktivieren. Arbeitsmappenautoren und Dokumentbesitzer können auf einen breiteren Bereich von Datenquellenverbindungsoptionen zugreifen, indem sie Einmaliges Anmelden aktivieren, wenn sie eine Datenaktualisierung für ihre veröffentlichten Arbeitsmappen planen.  
  
##### <a name="part-1-enable-secure-store-service"></a>Teil 1: Aktivieren von Secure Store Service  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Klicken Sie im Menüband Dienst Anwendungen unter Erstellen auf **neu**.  
  
3.  Wählen Sie **einmaliges Anmelden**aus.  
  
4.  Geben Sie auf der Seite **Secure Store-Anwendung erstellen** einen Namen für die Anwendung ein.  
  
5.  Geben Sie unter **Datenbank**die SQL Server Instanz an, die die Datenbank für diese Dienst Anwendung hostet. Der Standardwert entspricht der SQL Server-Datenbank-Engine-Instanz, die die Datenbanken für die Farmkonfiguration hostet.  
  
6.  Geben Sie unter **Datenbankname**den Namen der Datenbank der Dienst Anwendung ein. Der Standardwert ist Secure_Store_Service_DB_\<GUID->. Der Standardname entspricht dem Standardnamen der Dienstanwendung. Wenn Sie einen eindeutigen Dienstanwendungsnamen eingegeben haben, verwenden Sie eine ähnliche Benennungskonvention für den Datenbanknamen, damit Sie sie zusammen verwalten können.  
  
7.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie die SQL-Authentifizierung auswählen, finden Sie im SharePoint-Administratorhandbuch eine Anleitung zum Verwenden des Authentifizierungstyps in der Farm.  
  
8.  Wählen Sie unter Anwendungs Pool die Option **neuen Anwendungs Pool erstellen aus.** Geben Sie einen aussagekräftigen Namen an, der anderen Serveradministratoren hilft, den Verwendungszweck des Anwendungspools zu erkennen.  
  
9. Wählen Sie ein Sicherheitskonto für den Anwendungspool aus. Geben Sie ein verwaltetes Konto an, das als Domänenbenutzerkonto verwendet werden soll.  
  
10. Übernehmen Sie die restlichen Standardwerte, und klicken Sie dann auf **OK.** Die Dienstanwendung wird zusammen mit anderen verwalteten Diensten in der Dienstanwendungsliste der Farm angezeigt.  
  
##### <a name="part-2-generate-the-master-key"></a>Teil 2: Generieren des Hauptschlüssels  
  
1.  Klicken Sie in der Liste auf die Secure Store Service-Anwendung.  
  
2.  Klicken Sie im Menüband Dienst Anwendungen auf **Verwalten**.  
  
3.  Klicken Sie Unterschlüssel Verwaltung auf **neuen Schlüssel generieren**.  
  
4.  Geben Sie eine Passphrase ein, und bestätigen Sie sie dann. Die Passphrase wird zum Hinzufügen zusätzlicher freigegebener Secure Store Service-Anwendungen verwendet.  
  
5.  Klicken Sie auf **OK**.  
  
##### <a name="part-3-configure-the-unattended-powerpivot-data-refresh-account"></a>Teil 3: Konfigurieren des PowerPivot-Kontos für die unbeaufsichtigte Datenaktualisierung  
 Häufig muss ein Konto für die unbeaufsichtigte Datenaktualisierung für den PowerPivot-Datenzugriff erstellt werden, damit während der Datenaktualisierung auf externe Daten zugegriffen werden kann. Wenn Kerberos z. B. nicht aktiviert ist, müssen Sie ein unbeaufsichtigtes Konto erstellen, über das der PowerPivot-Dienst eine Verbindung mit externen Datenquellen herstellen kann.  
  
 Anweisungen zum Erstellen des unbeaufsichtigten Power Pivot-Daten Aktualisierungs Kontos oder anderer gespeicherter Anmelde Informationen, die bei der Datenaktualisierung verwendet werden, finden Sie unter [Konfigurieren des unbeaufsichtigten Daten](../../analysis-services/configure-unattended-data-refresh-account-powerpivot-sharepoint.md) Aktualisierungs Kontos für Power Pivot &#40;PowerPivot für SharePoint&#41;und [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../../../2014/analysis-services/configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="Usage"></a>Schritt 6: Aktivieren der Sammlung von Verwendungs Daten  
 PowerPivot für SharePoint erfasst Informationen zur PowerPivot-Verwendung überall in der Farm mithilfe der Infrastruktur zur Sammlung von SharePoint-Verwendungsdaten. Obwohl Verwendungsdaten immer Teil einer SharePoint-Installation sind, müssen sie möglicherweise aktiviert werden, damit sie verwendet werden können. Anweisungen finden Sie unter [Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint).  
  
##  <a name="Upload"></a>Schritt 7: Vergrößern der maximalen Uploadgröße für SharePoint-Webanwendungen und Excel Services  
 Da PowerPivot-Arbeitsmappen sehr groß werden können, kann es sinnvoll sein, die maximale Dateigröße zu erhöhen. Sie können zwei Einstellungen für die Dateigröße konfigurieren: Maximale Uploadgröße für die Webanwendung und Maximale Arbeitsmappengröße in Excel Services. Die maximale Dateigröße sollte in beiden Anwendungen auf den gleichen Wert festgelegt werden. Anweisungen finden Sie unter [Konfigurieren der maximalen Dateiuploadgröße &#40;PowerPivot für SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint).  
  
##  <a name="activatePP"></a>Schritt 8: Aktivieren der Power Pivot-Funktions Integration für Website Sammlungen  
 Die Funktionsaktivierung auf der Ebene der Websitesammlung stellt Anwendungsseiten und Vorlagen zur Verfügung, z. B. Konfigurationsseiten für geplante Datenaktualisierungen und Anwendungsseiten für den PowerPivot-Katalog und Datenfeedbibliotheken.  
  
1.  Klicken Sie auf einer SharePoint-Website auf **Websiteaktionen**.  
  
     Standardmäßig wird auf SharePoint-Webanwendungen über Port 80 zugegriffen. Dies bedeutet, dass Sie häufig auf eine SharePoint-Website zugreifen können\<, indem Sie http://Computername> eingeben, um die Stammweb Site Sammlung zu öffnen.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie unter Websitesammlungsverwaltung auf **Websitesammlungsfeatures**.  
  
4.  Scrollen Sie auf der Seite nach unten, bis Sie die **Funktion zur Power Pivot-Integration-Website Sammlung**  
  
5.  Klicken Sie auf **Aktivieren**.  
  
6.  Wiederholen Sie diesen Schritt für zusätzliche Website Sammlungen, indem Sie jede Website öffnen und auf **Website Aktionen**klicken  
  
 Weitere Informationen finden Sie unter [Aktivieren der Power Pivot-Funktions Integration für Website Sammlungen in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca).  
  
##  <a name="bkmk_redist"></a>Schritt 9: Installieren des SQL Server 2008 R2-Version des OLE DB Anbieters auf einer SQL Server 2012 PowerPivot für SharePoint-Instanz  
 Wenn Sie ältere und neuere Versionen von PowerPivot-Arbeitsmappen parallel auf demselben Server ausführen möchten, müssen Sie den im Lieferumfang von SQL Server 2008 R2 enthaltenen Analysis Services OLE-DB-Anbieter auf einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot für SharePoint-Server installieren.  
  
 Durch die Installation des Anbieters funktionieren Arbeitsmappen, die in der Datenverbindungszeichenfolge auf MSOLAP.4 verweisen, erwartungsgemäß auf einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot-Server. Die Installation des SQL Server 2008 R2 OLE DB-Anbieters ist eine alternative Methode zum Aktualisieren der in einer früheren Version von PowerPivot für Excel erstellten Arbeitsmappen.  
  
 Sie können den Anbieter von der [Seite SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272)herunterladen. Suchen Sie nach **Microsoft® Analysis Services OLE DB-Anbieter für Microsoft® SQL Server® 2008 R2**, und laden Sie das x64-Paket `SQLServer2008_ASOLEDB10.msi` des-Installationsprogramms herunter.  
  
 Weitere Informationen zum Installieren des Anbieters, einschließlich der Überprüfungs Schritte, finden Sie unter [install the Analysis Services OLE DB-Anbieter on SharePoint Servers](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
##  <a name="verifyinstall"></a>Schritt 10: Überprüfen der Installation  
 Die PowerPivot-Abfrageverarbeitung in der Farm tritt auf, wenn ein Benutzer oder eine Anwendung eine Excel-Arbeitsmappe öffnet, die PowerPivot-Daten enthält. Sie können Seiten auf SharePoint-Sites kontrollieren, um zu überprüfen, ob PowerPivot-Funktionen verfügbar sind. Um jedoch eine Installation vollständig zu überprüfen, müssen Sie eine PowerPivot-Arbeitsmappe haben, die Sie in SharePoint veröffentlichen können und auf die Sie über eine Bibliothek zugreifen können. Zu Testzwecken können Sie eine Beispielarbeitsmappe veröffentlichen, die bereits PowerPivot-Daten enthält, und damit überprüfen, ob die SharePoint-Integration ordnungsgemäß konfiguriert wurde.  
  
 Um die PowerPivot-Integration in eine SharePoint-Website zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Öffnen Sie in einem Browser die Webanwendung, die Sie erstellt haben. Wenn Sie Standardwerte verwendet haben, können Sie http://\<Ihren Computernamen in der URL-Adresse> angeben.  
  
2.  Überprüfen Sie, ob der PowerPivot-Datenzugriff und die Verarbeitungsfunktionen in der Anwendung verfügbar sind. Überprüfen Sie hierzu das Vorhandensein von durch PowerPivot bereitgestellte Bibliotheksvorlagen:  
  
    1.  Klicken Sie unter Website Aktionen auf **Weitere Optionen..**.  
  
    2.  In Bibliotheken sollten die **datenfeedbibliothek** und der **Power Pivot**-Katalog angezeigt werden. Diese Bibliotheksvorlagen werden von der PowerPivot-Funktion bereitgestellt und sind in der Bibliothekenliste sichtbar, falls die Funktion ordnungsgemäß integriert wurde.  
  
 Um den PowerPivot-Datenzugriff auf dem Server zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Laden Sie eine PowerPivot-Arbeitsmappe in den PowerPivot-Katalog oder in eine beliebige SharePoint-Bibliothek hoch.  
  
2.  Klicken Sie auf das Dokument, um es von der Bibliothek aus zu öffnen.  
  
3.  Klicken Sie auf einen Slicer, oder filtern Sie die Daten, um eine PowerPivot-Abfrage zu starten. Der Server lädt PowerPivot-Daten im Hintergrund und gibt die Ergebnisse zurück. Im nächsten Schritt stellen Sie eine Verbindung mit dem Server her, um zu überprüfen, ob die Daten geladen und zwischengespeichert wurden.  
  
4.  Starten Sie SQL Server Management Studio im Startmenü in der Programmgruppe Microsoft SQL Server 2008 R2. Wenn dieses Tool nicht auf dem Server installiert ist, können Sie mit dem letzten Schritt fortfahren, um das Vorhandensein zwischengespeicherter Dateien zu bestätigen.  
  
5.  Wählen Sie unter Servertyp die Option **Analysis Services**aus.  
  
6.  Geben Sie ** \<** ** \<unter Servername den Namen Servername> \powerpivot**ein, wobei Servername>der Name des Computers ist, auf dem sich die PowerPivot für SharePoint Installation befindet.  
  
7.  Klicken Sie auf **Verbinden**.  
  
8.  Klicken Sie in Objekt-Explorer auf **Datenbanken** , um die Liste der Power Pivot-Datendateien anzuzeigen, die geladen werden.  
  
9. Überprüfen Sie im Computerdateisystem den folgenden Ordner, um zu bestimmen, ob Dateien auf dem Datenträger zwischengespeichert wurden. Das Vorhandensein zwischengespeicherter Dateien ist eine weitere Bestätigung, dass die Bereitstellung betriebsbereit ist. Um den Dateicache anzuzeigen, wechseln Sie zum Ordner \Programme\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup.  
  
##  <a name="nextsteps"></a>Schritte nach der Installation  
 Nachdem Sie die Installation überprüft haben, beenden Sie die Dienstkonfiguration durch das Erstellen eines PowerPivot-Katalogs oder durch Anpassen einzelner Konfigurationseinstellungen. Um die Serverkomponenten, die Sie gerade installiert haben, vollständig zu nutzen, können Sie [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] herunterladen und dann Ihre erste PowerPivot-Arbeitsmappe erstellen und veröffentlichen.  
  
### <a name="install-data-providers-used-for-data-refresh"></a>Installieren von für die Datenaktualisierung verwendeten Datenanbietern  
 Wenn Sie die Datenaktualisierung aktiviert haben, benötigt der Server die gleichen Datenanbieter für den externen Datenzugriff, die auch von der PowerPivot-Clientanwendung zum Importieren der ursprünglichen Daten verwendet wurden. Wenn die Daten beispielsweise ursprünglich mit einem 32-Bit-Anbieter importiert wurden, ist für die serverseitige Datenaktualisierung auch ein 32-Bit-Anbieter erforderlich, wenn sie auf die gleiche externe Datenquelle zugreift. Weitere Informationen finden Sie unter [Power Pivot-Datenaktualisierung mit SharePoint 2010](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md).  
  
### <a name="install-adonet-data-services"></a>Installieren von ADO.NET Data Services  
 Sie müssen ADO.NET Data Services 3.5 SP1 installieren, wenn Sie SharePoint-Listen als Datenfeeds exportieren möchten. Anweisungen finden [Sie unter Install ADO.NET Data Services, um Datenfeed-Exporte von SharePoint-Listen zu unterstützen](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
### <a name="create-a-powerpivot-gallery"></a>Erstellen eines PowerPivot-Katalogs  
 Der PowerPivot-Katalog ist eine Bibliothek, die Vorschau- und Präsentationsoptionen zum Anzeigen von PowerPivot-Arbeitsmappen auf einer SharePoint-Website enthält. Das Verwenden des PowerPivot-Katalogs zum Veröffentlichen und Anzeigen von PowerPivot-Arbeitsmappen wird für die Vorschaufunktion empfohlen. Wenn Sie überdies auch Reporting Services auf dem gleichen SharePoint-Server bereitgestellt haben, bietet ein PowerPivot-Katalog Benutzerfreundlichkeit beim Erstellen von Berichten. Sie können den Berichts-Generator innerhalb des PowerPivot-Katalogs starten, um als Grundlage für einen neuen Bericht eine veröffentlichte PowerPivot-Arbeitsmappe zu verwenden. Weitere Informationen zum Erstellen und Verwenden der Bibliothek finden Sie unter [Erstellen und Anpassen des Power Pivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery) -Katalogs und [Verwenden des Power Pivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/use-power-pivot-gallery)-Katalogs.  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Erstellen von zusätzlichen vertrauenswürdigen Websites in Excel Services  
 Sie können vertrauenswürdige Websites in Excel Services hinzufügen, um die Berechtigungen und Konfigurationseinstellungen auf Websites zu variieren, die Excel-Arbeitsmappen und PowerPivot-Daten bereitstellen. Weitere Informationen finden Sie unter [Create a trusted location for PowerPivot sites in Central Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration).  
  
### <a name="tune-configuration-settings"></a>Optimieren von Konfigurationseinstellungen  
 Eine PowerPivot-Dienstanwendung wird mit Standardeigenschaften und -werten erstellt. Sie können Konfigurationseinstellungen für einzelne Dienstanwendungen ändern, um die Methodik zu ändern, anhand der die Anforderungen zugeordnet werden. Außerdem können Sie Servertimeouts festlegen, die Schwellenwerte für Abfrageantwortberichtsereignisse ändern oder festlegen, wie lange die Verwendungsdaten beibehalten werden sollen. Weitere Informationen zur Konfiguration in der zentral Administration oder zum Verwenden von Power Pivot-Funktionen in SharePoint-Webanwendungen finden Sie unter [Power Pivot-Server Verwaltung und-Konfiguration in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
### <a name="install-powerpivot-for-excel-and-build-a-powerpivot-workbook"></a>Installieren von PowerPivot für Excel und Erstellen einer PowerPivot-Arbeitsmappe  
 Nachdem Sie die Serverkomponenten in einer Farm installiert haben, können Sie die erste Excel 2010-Arbeitsmappe erstellen, die eingebettete PowerPivot-Daten verwendet, und sie dann in einer SharePoint-Bibliothek einer Webanwendung veröffentlichen. Bevor Sie Excel-Arbeitsmappen erstellen können, die PowerPivot-Daten enthalten, müssen Sie mit einer Installation von Excel 2010 beginnen, gefolgt vom PowerPivot-Add-In für Excel, das Excel erweitert, um den PowerPivot-Datenimport und die Datenbereicherung zu unterstützen.  
  
### <a name="add-servers-or-applications"></a>Hinzufügen von Servern oder Anwendungen  
 Wenn Sie die PowerPivot-Lösung bereitstellen, wird die Funktionsintegration auf der Websitesammlungsebene für alle Websitesammlungen in der Webanwendung aktiviert. Wenn Sie im Laufe der Zeit neue Webanwendungen erstellen, müssen Sie die powerpivotwebapp-Lösung für jede Anwendung bereitstellen. Anweisungen finden Sie unter Bereitstellen von [Power Pivot-Lösungen in SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint).  
  
 Je nach Konfiguration der PowerPivot-Dienstanwendung wird der PowerPivot-Systemdienst der Standardverbindungsgruppe hinzugefügt und somit für alle Webanwendungen verfügbar gemacht, die Standardverbindungen verwenden. Wenn Sie die Webanwendungen jedoch so konfiguriert haben, dass sie benutzerdefinierte Verbindungslisten für Dienstanwendungen verwenden, müssen Sie jeder SharePoint-Webanwendung, für die Sie die PowerPivot-Datenverarbeitung aktivieren möchten, die PowerPivot-Dienstanwendung hinzufügen. Weitere Informationen finden Sie unter [Verbinden einer Power Pivot-Dienst Anwendung mit einer SharePoint-Webanwendung in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca).  
  
 Wenn Sie mit der Zeit feststellen, dass zusätzlicher Datenspeicher und zusätzliche Verarbeitungskapazität erforderlich sind, können Sie der Farm eine zweite Serverinstanz mit PowerPivot für SharePoint hinzufügen. Der Installationsvorgang ist fast identisch mit den Schritten, die Sie ausgeführt haben, um den ersten Server hinzuzufügen, mit Ausnahme der Anforderungen, wie Sie Instanznamen und Dienstkontoinformationen angeben. Anweisungen finden Sie unter [Bereitstellungs Prüfliste: horizontales Skalieren durch Hinzufügen von Power Pivot-Servern zu einer SharePoint 2010-Farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von den-Editionen unterstützte Funktionen SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Konfigurieren von Power Pivot-Dienst Konten](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts)   
 [Erstellen und Konfigurieren einer Power Pivot-Dienst Anwendung in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca)   
 [Bereitstellen von Power Pivot-Lösungen in SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint)   
 [Aktivieren der Power Pivot-Funktions Integration für Website Sammlungen in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca)   
 [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
