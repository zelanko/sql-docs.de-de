---
title: Installieren Reporting Services SharePoint-Modus für SharePoint 2010 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 47efa72e-1735-4387-8485-f8994fb08c8c
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 758c76bf243af66157aa06f761df010a1e086a91
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798348"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2010"></a>Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010
  Die Prozeduren in diesem Thema führen Sie durch eine einzelne Serverinstallation eines Reporting Services-Bericht-Servers im SharePoint-Modus. Die Schritte schließen das Ausführen des SQL Server-Installations-Assistenten sowie zusätzlicher Konfigurationsaufgaben mit SharePoint 2010-Zentraladministration ein. Das Thema dient auch der Informationsfindung hinsichtlich einzelner Prozeduren, die für eine vorhandene Installation erforderlich sind, beispielsweise dem Erstellen einer neuen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienstanwendung. Weitere Informationen zum Hinzufügen zusätzlicher [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Server zu einer vorhandenen Farm finden [Sie unter Hinzufügen eines zusätzlichen Berichts Servers &#40;zu einer Farm SSRS&#41; Scale-Out](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) und [Hinzufügen eines zusätzlichen Reporting Services Web-Front-Ends zu einer Farm](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
 Eine einzelne Serverinstallation ist zur Entwicklung und dem Testen von Szenarien nützlich, aber wird nicht für Produktionsumgebungen empfohlen.  
  
> [!NOTE]  
>  Informationen zum Aktualisieren von und vorhandenem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]finden Sie unter [Upgrade and Migration Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  

  
##  <a name="bkmk_prereq"></a>Voraussetzungen  
  
-   > [!IMPORTANT]  
    >  Zum Konfigurieren und Verwalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager nicht mehr benötigt oder unterstützt. Verwenden Sie zum Konfigurieren eines Berichtsservers im SharePoint-Modus die SharePoint-Zentraladministration. Weitere Informationen finden Sie unter [Verwalten einer Reporting Services SharePoint-Dienst Anwendung](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
-   Informationen zu den Anforderungen, einschließlich für SharePoint 2010-Produkte, finden Sie in den folgenden Themen:  
  
    -   [Online Anmerkungen zu dieser Version](https://msdn.microsoft.com/library/dn169381.aspx)
  
    -   [Leitfaden zum Verwenden von SQL Server BI-Features in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
-   Dieses Thema befasst sich nicht mit der Installation von SharePoint 2010-Produkten. Weitere Informationen finden Sie unter [Anleitung für die Verwendung von SQL Server BI-Funktionen in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).  
  
-   Diese Prozeduren sind für das Konfigurieren eines [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Berichtsservers bestimmt und funktionieren nicht mit früheren Berichtsserverversionen. Die Architektur des gemeinsamen SharePoint-Diensts wurde in früheren Berichtsserverversionen nicht verwendet. Beispielsweise SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver und SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver.  
  
-   Vergewissern Sie sich, dass der **SharePoint 2010-Verwaltungs** Dienst in Windows Server-Manager gestartet wurde.  
  
 ![SSRS-Komponenten auf einer 1 Server-Installation](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "SSRS-Komponenten auf einer 1 Server-Installation")  
  
### <a name="database-considerations-for-a-single-server-configuration"></a>Überlegungen zu Datenbanken für eine Konfiguration mit einem einzelnen Server  
  
-   Sowohl Reporting Services als auch SharePoint-Produkte und -Technologien verwenden relationale SQL Server-Datenbanken zum Speichern von Anwendungsdaten.  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] erfordert eine kompatible SQL Engine-Instanz einer SQL Server Evaluation-Edition.  
  
-   SharePoint-Produkte können eine vorhandene Datenbankinstanz verwenden. Wenn eine Instanz von Datenbank-Engine nicht installiert ist, installiert das Setup Programm für SharePoint-Produkte SQL Server Express Edition für die SharePoint-Anwendungsdatenbanken.  
  
-   Die SQL Server Express-Edition kann nicht für die Datenbank der Berichtsserverinstanz verwendet werden. Die mit dem SharePoint-Produkt installierte Instanz der SQL Server Express Edition kann jedoch gleichzeitig mit anderen Datenbank-Engine-Editionen ausgeführt werden.  
  

  
##  <a name="bkmk_install_SSRS"></a>Installieren von Reporting Services Berichts Server im SharePoint-Modus  
  
1.  Führen Sie den SQL Server-Installations-Assistenten aus.  
  
2.  Klicken Sie links im Assistenten auf **Installation** , und klicken Sie anschließend auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
3.  Klicken Sie auf **OK** auf der Seite **Setupunterstützungsregeln** , in der Annahme, dass alle Regeln den Status Bestanden aufweisen.  
  
4.  Klicken Sie auf der Seite **Setupunterstützungsdateien** auf **Installieren** .  
  
5.  Klicken Sie auf **weiter** , nachdem die Unterstützungs Dateien installiert wurden **und in den Unterstützungs Regeln der Status**erfolgreich angezeigt wird. Überprüfen Sie alle Warnungen oder Probleme, die eine Blockierung verursachen.  
  
6.  Geben Sie auf der Seite **Product Key** Ihren Schlüssel ein, oder übernehmen Sie den Standardwert der Enterprise Evaluation Edition.  
  
     Klicken Sie auf **Weiter**.  
  
7.  Lesen und akzeptieren Sie die Lizenzbedingungen. Microsoft ist Ihnen dankbar, wenn Sie durch Klicken bestätigen, dass Sie damit einverstanden sind, Daten zur Funktionsverwendung zu senden, damit wir Produktfunktionen und -support verbessern können.  
  
     Klicken Sie auf **Weiter**.  
  
8.  Wählen Sie auf der Seite **Setup Rolle** die Option **SQL Server Featureinstallation** aus.  
  
     Klicken Sie auf **Weiter**.  
  
     ![SQL Server Featureinstallation für Setup Rolle](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Featureinstallation für Setup Rolle")  
  
9. Wählen Sie Folgendes auf der Seite **Funktionsauswahl** aus:  
  
    -   **Reporting Services – SharePoint**  
  
    -   **Reporting Services-Add-in für SharePoint 2010-Produkte**. ![Hinweis](../../../2014/reporting-services/media/rs-fyinote.png "nbezeichnet) Die Option Installations-Assistent für die Installation des Add-Ins ist neu in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version.  
  
    -   Wenn Sie noch keine Instanz von SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]haben, können Sie auch **Datenbank-Engine-Dienste** und **Verwaltungstools - Vollständig** für eine vollständige Umgebung auswählen.  
  
     Klicken Sie auf **Weiter**.  
  
     ![SSRS-Funktionsauswahl für den SharePoint-Modus](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS-Funktionsauswahl für den SharePoint-Modus")  
  
10. Klicken Sie auf der Seite **Installations Regeln** auf **weiter** . Überprüfen Sie alle Warnungen oder Probleme, die eine Blockierung verursachen.  
  
11. Wenn Sie Datenbank-Engine-Dienste ausgewählt haben, akzeptieren Sie die Standardinstanz von **MSSQLSERVER** auf der Seite **Instanzkonfiguration** , und klicken Sie auf **Weiter**. Die Architektur des gemeinsamen Diensts von Reporting Services basiert nicht auf einer SQL Server-Instanz wie bei der vorherigen Reporting Services-Architektur.  
  
12. Prüfen Sie die Seite **Erforderlicher Speicherplatz** , und klicken Sie auf **Weiter**.  
  
13. Geben Sie auf der Seite **Server Konfiguration** die entsprechenden Anmelde Informationen ein. Wenn Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenwarn- oder Abonnementfunktionen verwenden möchten, müssen Sie den **Starttyp** für den SQL Server-Agent auf **Automatisch**ändern.  
  
     Klicken Sie auf **Weiter**.  
  
14. Wenn Sie Datenbank-Engine-Dienste auswählten, wird die Seite **Datenbank-Engine-Konfiguration** angezeigt, auf der Sie entsprechende Konten der Liste der SQL-Administratoren hinzufügen können. Klicken Sie anschließend auf **Weiter**.  
  
15. Auf der Seite **Reporting Services-Konfiguration** sollten Sie sehen, dass die Option **Nur Installieren** aktiviert ist. Diese Option installiert die Berichtsserverdateien; sie konfiguriert jedoch nicht die SharePoint-Umgebung für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Nach Abschluss der SQL Server-Installation müssen Sie den anderen Abschnitten dieses Themas folgen, um die SharePoint-Umgebung zu konfigurieren. Dies schließt die Installation des gemeinsamen Diensts von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und das Erstellen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen ein.  
  
     ![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")  
  
16. Helfen Sie Microsoft bei der Verbesserung der SQL Server-Funktionen und -Dienste, indem Sie das Kontrollkästchen aktivieren und somit Fehlerberichte auf der Seite **Fehlerberichterstellung** weiterleiten.  
  
     Klicken Sie auf **Weiter**.  
  
17. Überprüfen Sie alle Warnungen, und klicken Sie anschließend auf der Seite **Installationskonfigurationsregeln** auf **Weiter** .  
  
18. Lesen Sie auf der Seite **Installationsbereit** die Installationszusammenfassung, und klicken Sie anschließend auf **Weiter**. Die Zusammenfassung enthält einen **Reporting Services** Knoten, der den installationsmoduswert **sharepointfilesonlymode** sowie die Kontoinformationen enthält.  
  

  
##  <a name="bkmk_install_SSRS_sharedservice"></a>Installieren und Starten des Reporting Services SharePoint-Dienstanbieter  
 ![PowerShell-bezogener Inhalt](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell-bezogener Inhalt")  
  
> [!NOTE]  
>  Wenn Sie in einer vorhandenen SharePoint-Farm installieren, **müssen Sie** die Schritte in diesem Abschnitt nicht ausführen. Der SharePoint-Dienst für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wurde installiert und gestartet, als Sie im vorherigen Abschnitt den SQL Server-Installations-Assistenten ausgeführt haben.  
  
 Die notwendigen Dateien wurden als Teil des SQL Server-Installations-Assistenten installiert, die Dienste müssen jedoch in der SharePoint-Farm registriert werden. Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version führt PowerShell-Unterstützung für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus ein. Die unten stehenden Schritte zeigen Ihnen, wie die SharePoint-Verwaltungsshell geöffnet und Cmdlets ausgeführt werden:  
  
1.  Klicken Sie auf die Schaltfläche **Start** .  
  
2.  Klicken Sie auf die Gruppe **Microsoft SharePoint 2010-Produkte** .  
  
3.  Klicken Sie mit der rechten Maustaste auf **SharePoint 2010-Verwaltungsshell** klicken Sie auf **als Administrator ausführen**  
  
4.  Führen Sie den folgenden PowerShell-Befehl aus, um den SharePoint Service zu installieren. Ein erfolgreicher Abschluss des Befehls zeigt eine neue Zeile in der Verwaltungsshell an. Wurde der Befehl erfolgreich ausgeführt, wird keine Meldung an die Verwaltungsshell zurückgegeben:  
  
    ```powershell
    Install-SPRSService  
    ```  
  
5.  Führen Sie den folgenden PowerShell-Befehl aus, um den Dienstproxy zu installieren.  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  Führen Sie den folgenden PowerShell-Befehl aus, um den Dienst zu starten, oder starten Sie den Dienst von der SharePoint-Zentraladministration anhand der unten stehenden Anweisungen:  
  
    ```powershell
    Get-SPServiceInstance -All | Where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 Sie können den Dienst auch von der SharePoint-Zentraladministration starten anstatt den dritten PowerShell-Befehl auszuführen. Die folgenden Schritte sind auch nützlich, um sicherzustellen, dass der Dienst gestartet wurde.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Dienste auf dem Server verwalten** .  
  
2.  Suchen Sie den **SQL Server Reporting Services-Dienst** , und klicken Sie in der Spalte Aktion auf **Starten** .  
  
3.  Der Status des Reporting Services-Diensts ändert sich von **Beendet** auf **Gestartet**. Installieren Sie den Reporting Services-Dienst mit PowerShell, wenn sich dieser nicht in der Liste befindet.  
  
    > [!NOTE]  
    >  Wenn der Reporting Services-Dienst **im Status wird** gestartet bleibt und sich nicht in **gestartet**ändert, vergewissern Sie sich, dass der Dienst SharePoint 2010 Administration in Windows Server-Manager gestartet wurde.  

##  <a name="bkmk_create_serrviceapplication"></a>Erstellen einer Reporting Services-Dienst Anwendung  
 Dieser Abschnitt enthält die Schritte zum Erstellen einer Dienstanwendung und eine Beschreibung der Eigenschaften, wenn Sie eine vorhandene Dienstanwendung überprüfen.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Anwendungsverwaltung** auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie im SharePoint-Menüband auf die Schaltfläche **Neu** .  
  
3.  Klicken Sie im Menü Neu auf **SQL Server Reporting Services-Dienstanwendung**.  
  
    > [!WARNING]  
    >  Wenn die Option [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht in der Liste angezeigt wird, ist dies ein **Hinweis darauf, dass der gemeinsame Dienst [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht installiert ist**. Lesen Sie den vorherigen Abschnitt, in dem das Installieren des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Diensts mithilfe von PowerShell-Cmdlets beschrieben wird.  
  
4.  Geben Sie auf der Seite **SQL Server Reporting Services-Dienstanwendung erstellen** einen Namen für die Anwendung ein. Wenn Sie mehrere Reporting Services-Dienstanwendungen erstellen, hilft ein aussagekräftiger Name oder eine Benennungskonvention bei der Organisation von Administrations- und Verwaltungsvorgängen.  
  
5.  Erstellen Sie im Abschnitt **Anwendungspool** einen neuen Anwendungspool für die Anwendung (empfohlen). Die Verwendung des gleichen Namens für den neuen Anwendungspool und die Dienstanwendung kann Ihre laufenden Verwaltungsaufgaben vereinfachen.  
  
     Wählen Sie ein verwaltetes Konto für den Anwendungspool aus, oder erstellen Sie es. Sie müssen ein Domänenbenutzerkonto angeben. Ein Domänenbenutzerkonto ermöglicht die Verwendung der in SharePoint verfügbaren Funktion "Verwaltetes Konto", mit der Sie Kennwörter und Kontoinformationen zentral aktualisieren können. Domänenkonten sind auch erforderlich, wenn Sie beabsichtigen, die Bereitstellung auf zusätzlichen Dienstinstanzen, die unter der gleichen Identität ausgeführt werden, zu skalieren.  
  
6.  Im **Datenbankserver**können Sie den aktuellen Server verwenden oder einen anderen SQL Server auswählen.  
  
7.  Der Standardwert von **Datenbankname** ist `ReportingService_<guid>`. Dies ist ein eindeutiger Datenbankname. Wenn Sie einen neuen Wert eingeben, geben Sie einen eindeutigen Wert ein.  
  
8.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie **SQL-Authentifizierung**auswählen, finden Sie im SharePoint-Administratorhandbuch bewährte Methoden zur Verwendung dieses Authentifizierungstyps in einer SharePoint-Bereitstellung.  
  
9. Wählen Sie im Abschnitt **Webanwendungszuordnungen** die Webanwendung aus, die für Zugriff von der aktuellen Reporting Services-Dienstanwendung bereitgestellt werden soll. Sie können einer Webanwendung eine Reporting Services-Dienstanwendung zuordnen. Wenn alle aktuellen Webanwendungen bereits einer Reporting Services-Dienstanwendung zugeordnet sind, wird eine Warnmeldung angezeigt.  
  
10. Klicken Sie auf **OK**.  
  
11. Der Dienstanwendungserstellungsprozess dauert möglicherweise mehrere Minuten. Wenn es vollständig ist, sehen Sie eine Bestätigungsmeldung und einen Link zu einer Seite **Abonnements und Warnungen bereitstellen** . Sie müssen den Bereitstellungsschritt ausführen, wenn Sie die Abonnement- und Warnungsfunktionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwenden möchten. Weitere Informationen finden Sie unter [Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
 ![PowerShell-bezogener Inhalt](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell-bezogener Inhalt") Informationen zur Verwendung von PowerShell zum Erstellen einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst Anwendung finden Sie [unter So erstellen Sie eine Reporting Services Service-Anwendung mithilfe von PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).  
  

  
##  <a name="bkmk_powerview"></a>Aktivieren Sie die Power View Website Sammlungs Funktion.  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], eine Funktion des [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-Ins für [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition, ist eine Website Sammlungs Funktion. Die Funktion wird für Stammwebsitesammlungen und Websitesammlungen automatisch aktiviert, die nach der Installation des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins erstellt wurden. Wenn Sie die Verwendung von [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]planen, sollten Sie sicherstellen, dass die Funktion aktiviert ist.  
  
 Wenn Sie nach der Installation des SharePoint 2010-Produkts das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint 2010-Produkte installieren, werden die Berichtsserverintegrationsfunktion und die Power View-Integrationsfunktion nur für Stammwebsitesammlungen aktiviert. Für andere Websitesammlungen müssen Sie die Funktionen manuell aktivieren.  
  
#### <a name="to-activate-the-power-view-feature"></a>So aktivieren Sie die Power View-Funktion  
  
1.  Öffnen Sie die gewünschte SharePoint-Website in Ihrem Browser.  
  
2.  Klicken Sie auf **Websiteaktionen**.  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe „Websitesammlungsverwaltung“ auf **Websitesammlungs-Features** .  
  
5.  Suchen Sie **Power View-Integrationsfunktion** in der Liste.  
  
6.  Klicken Sie auf **Aktivieren**.  
  
 Diese Prozedur wird pro Websitesammlung abgeschlossen. Weitere Informationen finden Sie unter [Aktivieren des Berichts Servers und Power View Integrations Features in SharePoint](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) .  
  
##  <a name="bkmk_additional_config"></a> Zusätzliche Konfiguration  
 In diesem Abschnitt werden zusätzliche Konfigurationsschritte beschrieben, die in den meisten SharePoint-Bereitstellungen wichtig sind.  
  
###  <a name="bkmk_provision_agent"></a> Abonnements und Warnungen bereitstellen  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Abonnements und -Datenwarnungen erfordern möglicherweise die Konfiguration von SQL Server-Agent-Berechtigungen. Wenn eine Fehlermeldung darauf hinweist, dass SQL Server-Agent erforderlich ist, Sie jedoch sichergestellt haben, dass SQL Server-Agent gestartet wurde, müssen Sie die Berechtigungen aktualisieren. Sie können auf der Seite mit der Erfolgsmeldung nach der Dienstanwendungserstellung auf den Link **Abonnements und Warnmeldungen bereitstellen** klicken, um eine andere Seite für die SQL Server-Agent-Bereitstellung aufzurufen. Der Bereitstellungsschritt ist erforderlich, wenn die Bereitstellung über mehrere Computer erfolgt (wenn sich z. B. die SQL Server-Datenbankinstanz auf einem anderen Computer befindet). Weitere Informationen finden Sie unter [Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  

  
### <a name="configure-e-mail-for-a-service-application"></a>Konfigurieren von E-Mail-Einstellungen für eine Dienstanwendung  
 Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenwarnungsfunktion sendet Warnungen in E-Mail-Nachrichten. Um E-Mails übermitteln zu können, kann es notwendig sein, dass Sie Ihre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung konfigurieren und die E-Mail-Übermittlungserweiterung für die Dienstanwendung ändern müssen. Die E-Mail-Einstellungen sind erforderlich, wenn Sie beabsichtigen, die E-Mail-Übermittlungserweiterung für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Abonnementfunktion zu verwenden. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  

  
### <a name="add-reporting-services-content-types"></a>Hinzufügen von Reporting Services-Inhaltstypen  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt vordefinierte Inhaltstypen bereit, die zum Verwalten freigegebener Datenquellendateien (RSDS), Berichtsmodelldateien (SMDL) und Berichts-Generator-Berichtsdefinitionsdateien (RDL) verwendet werden können. Wenn einer Bibliothek ein Inhaltstyp ( **Berichts-Generator-Bericht**, **Berichtsmodell**und **Berichtsdatenquelle** ) hinzugefügt wird, wird der Befehl **Neu** aktiviert, sodass Sie neue Dokumente des betreffenden Typs erstellen können. Weitere Informationen finden Sie unter [Hinzufügen von Berichts Server-Inhaltstypen &#40;zu einer Bibliothek Reporting Services im integrierten&#41;SharePoint-Modus](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  

  
### <a name="activate-the-file-sync-feature"></a>Aktivieren der Dateisynchronisierungsfunktion  
 Wenn die Benutzer häufig veröffentlichte Berichtselemente direkt in SharePoint-Dokumentbibliotheken hochladen, ist die Berichtsserverdateisynchronisierungsfunktion nützlich. Die Dateisynchronisierungsfunktion synchronisiert den Berichtsserverkatalog regelmäßiger mit Elementen in Dokumentbibliotheken. Weitere Informationen finden Sie unter [Aktivieren des Features zur Berichtsserver-Dateisynchronisierung in der SharePoint-Zentraladministration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [PowerShell-Cmdlets für SharePoint-Modus von Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
 [Von den Editionen von SQL Server 2012 unterstützte Funktionen](https://go.microsoft.com/fwlink/?linkid=232473)   
 [Reporting Services-SharePoint-Dienst und -Dienstanwendungen](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
