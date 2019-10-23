---
title: Installieren Reporting Services SharePoint-Modus für SharePoint 2013 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: b29d0f45-0068-4c84-bd7e-5b8a9cd1b538
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1a249c7a6fa260d5800c81b33b7674a2affa4eb5
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952223"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2013"></a>Installieren des SharePoint-Modus von Reporting Services für SharePoint 2013
  In den Verfahren in diesem Thema werden Sie durch die Installation eines einzelnen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Servers im SharePoint-Modus geführt. In den Schritten führen Sie u. a. den Installations-Assistenten für SQL Server sowie Konfigurationsaufgaben unter Verwendung der SharePoint-Zentraladministration aus. Außerdem können Sie sich in diesem Thema auch über einzelne Verfahren zum Aktualisieren einer vorhandenen Installation informieren, beispielsweise um eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung zu erstellen.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; - **Hinweis:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-SharePoint-Modus unterstützt **nicht** die mehr Instanzen Fähigkeit von SharePoint Server.|  
  
 Informationen darüber, wie Sie einer vorhandenen Farm weitere [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Server hinzufügen, finden Sie unter:  
  
-   [Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm &#40;Horizontales Skalieren für SSRS&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [Add an Additional Reporting Services Web Front-end to a Farm (Hinzufügen eines zusätzlichen Reporting Services-Web-Front-Ends zu einer Farm)](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 Die Installation auf einem einzelnen Server ist für Entwicklungs- und Testszenarien geeignet, wird aber für Produktionsumgebungen nicht empfohlen.  
  
 **In diesem Thema:**  
  
-   [Beispiel für eine Einzel Server Bereitstellung](#bkmk_singleserver)  
  
-   [Setup Konten](#bkmk_setupaccounts)  
  
-   [Schritt 1: Installieren von Reporting Services Berichts Server im SharePoint-Modus @ no__t-0  
  
-   [Schritt 2: Registrieren und Starten des Reporting Services SharePoint-Dienstanbieter @ no__t-0  
  
-   [Schritt 3: Erstellen einer Reporting Services-Dienst Anwendung @ no__t-0  
  
-   [Schritt 4: Aktivieren Sie das Feature "Power View Website Sammlung". ](#bkmk_powerview)  
  
-   [Windows PowerShell-Skript für die Schritte 1-4](#bkmk_full_script)  
  
-   [Additional Configuration](#bkmk_additional_config) schließt die Bereitstellung für Abonnements und Warnungen, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Inhaltstypen und die Konfiguration von Excel Services für die Verwendung eines Analysis Services-Servers ein.  
  
-   [Überprüfen der Installation](#bkmk_verify_installation)  
  
##  <a name="bkmk_singleserver"></a> Beispiel für die Bereitstellung auf einem Server  
 Die Installation auf einem einzelnen Server ist für Entwicklungs- und Testszenarien geeignet, wird aber für Produktionsumgebungen nicht empfohlen. Eine Umgebung mit einem Server bezieht sich auf einen einzelnen Computer, für den SharePoint und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten auf demselben Computer installiert sind. Dieses Thema gilt nicht für horizontales Skalieren mit mehreren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Servern.  
  
 Das folgende Diagramm veranschaulicht die Komponenten, die Teil einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung auf einem einzelnen Server sind.  
  
|||  
|-|-|  
|**(1)**|Mit einer SQL Server-Installation installierter SharePoint-Dienst. Sie können eine oder mehrere [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen erstellen.|  
|**(2)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte stellt die Benutzeroberflächenkomponenten auf den SharePoint-Servern bereit.|  
|**(3)**|Die Excel Services-Anwendung wird von Power View und PowerPivot verwendet.|  
|**(4)**|PowerPivot-Dienstanwendung.|  
  
 ![Bereitstellung eines einzelnen Servers im SSRS-SharePoint-Modus](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint Mode Single Server Deployment")  
  
> [!TIP]  
>  Komplexere Bereitstellungsbeispiele finden Sie unter [Bereitstellungstopologien für SQL Server-BI-Funktionen in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
##  <a name="bkmk_setupaccounts"></a> Setupkonten  
 In diesem Abschnitt werden die Konten und Berechtigungen beschrieben, die für die wesentlichen Schritte zur Bereitstellung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus verwendet werden.  
  
 **Installieren und Registrieren des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Diensts:**  
  
-   Das aktuelle Konto während der Installation (als "Setup-Konto" bezeichnet) von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus muss über Administratorrechte auf dem lokalen Computer verfügen. Wenn Sie nach der Installation von SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installieren und das Setup Konto ebenfalls Mitglied der Gruppe der SharePoint-Farm Administratoren ist, wird der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst von der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation für Sie registriert. Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installieren, bevor SharePoint installiert ist, oder wenn das Setup Konto kein Mitglied der Gruppe "Farm Administratoren" ist, registrieren Sie den Dienst manuell. Weitere Informationen finden Sie im Abschnitt [step 2: Registrieren und starten Sie den Reporting Services SharePoint-Dienst @ no__t-0.  
  
 **Erstellen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen**  
  
-   Nach der Installation und Registrierung des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Diensts erstellen Sie mindestens eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung. Das „Dienstkonto der SharePoint-Farm“ muss vorübergehend Mitglied der lokalen Administratorgruppe sein, damit die Reporting Services-Dienstanwendung erstellt werden kann. Weitere Informationen zu SharePoint 2013-Konto Berechtigungen finden Sie unter [Konto Berechtigungen und Sicherheitseinstellungen in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx).  
  
     Eine bewährte Sicherheitsmethode besteht darin, die Administratorkonten der SharePoint-Farm nicht gleichzeitig als Administratorkonten des lokalen Betriebssystems festzulegen. Wenn Sie der lokalen Administratorgruppe während der Installation ein Farmadministratorkonto hinzufügen, wird empfohlen, das Konto nach Ende der Installation aus der lokalen Administratorgruppe zu entfernen.  
  
##  <a name="bkmk_install_SSRS"></a>Schritt 1: Installieren von Reporting Services Berichts Server im SharePoint-Modus  
 In diesem Schritt werden ein [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver im SharePoint-Modus und das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte installiert. Abhängig von bereits auf dem Computer installierten Komponenten werden einige der in den folgenden Schritten beschriebenen Installationsseiten u. U. nicht angezeigt.  
  
1.  Führen Sie den Installations-Assistenten für SQL Server (Setup.exe) aus.  
  
2.  Klicken Sie links im Assistenten auf **Installation** , und klicken Sie anschließend auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
3.  Klicken Sie auf **OK** auf der Seite **Setupunterstützungsregeln** , in der Annahme, dass alle Regeln den Status Bestanden aufweisen.  
  
4.  Klicken Sie auf der Seite **Setupunterstützungsdateien** auf **Installieren** . Abhängig von den bereits auf dem Computer installierten Komponenten kann folgende Meldung angezeigt werden:  
  
    -   „Für mindestens eine betroffene Datei stehen Vorgänge aus. Sie müssen den Computer nach Abschluss des Setupvorgangs neu starten.“  
  
    -   Klicken Sie auf **OK**.  
  
5.  Klicken Sie auf **Weiter** , nachdem die Unterstützungsdateien installiert wurden und auf den Seiten mit **Unterstützungsregeln** der Status **Erfolgreich**angezeigt wird. Überprüfen Sie alle Warnungen oder Probleme, die eine Blockierung verursachen.  
  
6.  Klicken Sie auf der Seite **Installationstyp** auf **Funktionen zu einer vorhandenen SQL Server 2014-Instanz hinzufügen**. Wählen Sie die richtige Instanz aus der Dropdownliste aus, und klicken Sie auf **Weiter**.  
  
7.  Falls die Seite **Product Key** angezeigt wird, geben Sie Ihren Product Key ein, oder übernehmen Sie den Standardwert der Enterprise Evaluation Edition.  
  
     Klicken Sie auf **Weiter**.  
  
8.  Lesen Sie die Seite mit den Lizenzbedingungen, falls diese angezeigt wird, und akzeptieren Sie die Bedingungen. Microsoft ist Ihnen dankbar, wenn Sie durch Klicken bestätigen, dass Sie damit einverstanden sind, Daten zur Funktionsverwendung zu senden, damit wir Produktfunktionen und -support verbessern können.  
  
     Klicken Sie auf **Weiter**.  
  
9. Wenn die Seite **Setuprolle** angezeigt wird, wählen Sie **SQL Server-Funktionsinstallation**aus.  
  
     Klicken Sie auf **Weiter**.  
  
     ![SQL Server-Funktionsinstallation für Setuprolle](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")  
  
10. Wählen Sie Folgendes auf der Seite **Funktionsauswahl** aus:  
  
    -   **Reporting Services – SharePoint**  
  
    -   **Reporting Services-Add-In für SharePoint-Produkte**.  
  
         ![Hinweis](../../../2014/reporting-services/media/rs-fyinote.png "Hinweis") Die Option Installations-Assistent für die Installation des Add-Ins ist neu [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in der-Version.  
  
    -   Wenn Sie noch keine Instanz von SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]haben, können Sie auch **Datenbank-Engine-Dienste** und **Verwaltungstools - Vollständig** für eine vollständige Umgebung auswählen.  
  
     Klicken Sie auf **Weiter**.  
  
     ![SSRS-Funktionsauswahl für den SharePoint-Modus](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS-Funktionsauswahl für den SharePoint-Modus")  
  
11. Möglicherweise wird die Seite **Installationsregeln** angezeigt. Überprüfen Sie alle Warnungen oder Probleme, die eine Blockierung verursachen. Klicken Sie dann auf **Weiter**.  
  
12. Wenn Sie Datenbank-Engine-Dienste ausgewählt haben, akzeptieren Sie die Standardinstanz von **MSSQLSERVER** auf der Seite **Instanzkonfiguration** , und klicken Sie auf **Weiter**.  
  
     ![Hinweis](../../../2014/reporting-services/media/rs-fyinote.png "note")Die Architektur des Reporting Services SharePoint-Dienstes basiert nicht auf einer SQL Server-„Instanz“, wie es bei der vorherigen Reporting Services-Architektur der Fall war.  
  
13. Prüfen Sie die Seite **Erforderlicher Speicherplatz** , und klicken Sie auf **Weiter**.  
  
14. Wenn die Seite **Serverkonfiguration** angezeigt wird, geben Sie die entsprechenden Anmeldeinformationen ein. Wenn Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenwarn- oder Abonnementfunktionen verwenden möchten, müssen Sie den **Starttyp** für den SQL Server-Agent auf **Automatisch**ändern. Abhängig von den bereits auf dem Computer installierten Komponenten wird die Seite **Serverkonfiguration** möglicherweise nicht angezeigt.  
  
     Klicken Sie auf **Weiter**.  
  
15. Wenn Sie Datenbank-Engine-Dienste auswählten, wird die Seite **Datenbank-Engine-Konfiguration** angezeigt, auf der Sie entsprechende Konten der Liste der SQL-Administratoren hinzufügen können. Klicken Sie anschließend auf **Weiter**.  
  
16. Auf der Seite **Reporting Services-Konfiguration** sollten Sie sehen, dass die Option **Nur Installieren** aktiviert ist. Mit dieser Option werden die Berichtsserverdateien installiert. Die SharePoint-Umgebung für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]wird damit nicht konfiguriert.  
  
    > [!NOTE]  
    >  Nachdem die SQL Server-Installation abgeschlossen wurde, befolgen Sie die Anweisungen in den weiteren Abschnitten dieses Themas, um die SharePoint-Umgebung zu konfigurieren. Dies schließt die Installation des gemeinsamen Diensts von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und das Erstellen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen ein.  
  
     ![SQL Server Setup-Assistent: Seite ' SSRS-Konfiguration](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server Setup-Assistent-Seite SSRS-Konfiguration")  
  
17. Helfen Sie Microsoft bei der Verbesserung der SQL Server-Funktionen und -Dienste, indem Sie das Kontrollkästchen aktivieren und somit Fehlerberichte auf der Seite **Fehlerberichterstellung** weiterleiten.  
  
     Klicken Sie auf **Weiter**.  
  
18. Überprüfen Sie alle Warnungen, und klicken Sie anschließend auf der Seite **Installationskonfigurationsregeln** auf **Weiter** .  
  
19. Lesen Sie auf der Seite **Installationsbereit** die Installationszusammenfassung, und klicken Sie anschließend auf **Weiter**. Die Zusammenfassung enthält einen untergeordneten Knoten **SharePoint-Modus für Reporting Services** , für den der Wert **SharePointFilesOnlyMode**angezeigt wird. Klicken Sie auf **Installieren**.  
  
20. Die Installation dauert mehrere Minuten. Die Seite **Abgeschlossen** wird mit einer Liste der Funktionen und dem Status der einzelnen Funktionen angezeigt. Möglicherweise werden Sie in einem Informationsdialogfeld darauf hingewiesen, dass der Computer neu gestartet werden muss.  
  
##  <a name="bkmk_install_SSRS_sharedservice"></a>Schritt 2: Reporting Services SharePoint-Dienst registrieren und starten  
 ![PowerShell-Inhalt](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content")  
  
> [!NOTE]  
>  Wenn Sie in eine vorhandene SharePoint-Farm installieren, müssen Sie die Schritte in diesem Abschnitt nicht ausführen. Der SharePoint-Dienst für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wurde installiert und gestartet, als Sie entsprechend den Anweisungen im vorherigen Abschnitt dieses Dokuments den Installations-Assistenten für SQL Server ausgeführt haben.  
  
 Die folgenden Hauptgründe erfordern die manuelle Registrierung des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Diensts.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus wurde vor SharePoint installiert.  
  
-   Das Konto, das zur Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus verwendet wurde, war nicht Mitglied der Administratorgruppe der SharePoint-Farm. Weitere Informationen finden Sie im Abschnitt [Setup accounts](#bkmk_setupaccounts).  
  
 Die notwendigen Dateien wurden als Teil des SQL Server-Installations-Assistenten installiert, die Dienste müssen jedoch in der SharePoint-Farm registriert werden. Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version führt PowerShell-Unterstützung für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus ein.  
  
 Die unten stehenden Schritte zeigen Ihnen, wie die SharePoint-Verwaltungsshell geöffnet und Cmdlets ausgeführt werden:  
  
1.  Klicken Sie auf die Schaltfläche **Start** .  
  
2.  Klicken Sie auf die Gruppe **Microsoft SharePoint 2013-Produkte** .  
  
3.  Klicken Sie mit der rechten Maustaste auf **SharePoint 2013-Verwaltungsshell** , und klicken Sie anschließend auf **Als Administrator ausführen**. HINWEIS: Die SharePoint-Befehle werden im Windows PowerShell-Standardfenster nicht erkannt. Verwenden Sie die **SharePoint 2013-Verwaltungsshell**.  
  
4.  Führen Sie den folgenden PowerShell-Befehl aus, um den SharePoint Service zu installieren. Ein erfolgreicher Abschluss des Befehls zeigt eine neue Zeile in der Verwaltungsshell an. Wurde der Befehl erfolgreich ausgeführt, wird**keine Meldung** an die Verwaltungsshell zurückgegeben:  
  
    ```  
    Install-SPRSService  
    ```  
  
    > [!IMPORTANT]  
    >  Angenommen, eine Fehlermeldung mit etwa folgendem Wortlaut wird ausgegeben:  
    >   
    >  Install-sprsservice: Der Begriff "Install-sprsservice" **wird nicht** als  
    > Name eines Cmdlets, einer Funktion, einer Skriptdatei oder eines ausführbaren Programms erkannt. Überprüfen Sie die  
    > Schreibweise des Namens, oder ob der Pfad korrekt ist (sofern enthalten),  
    > und wiederholen Sie den Vorgang.  
  
5.  Führen Sie den folgenden PowerShell-Befehl aus, um den Dienstproxy zu installieren. Ein erfolgreicher Abschluss des Befehls zeigt eine neue Zeile in der Verwaltungsshell an. Wurde der Befehl erfolgreich ausgeführt, wird**keine Meldung** an die Verwaltungsshell zurückgegeben:  
  
    ```  
    Install-SPRSServiceProxy  
    ```  
  
6.  Führen Sie den folgenden PowerShell-Befehl aus, um den Dienst zu starten, oder starten Sie den Dienst von der SharePoint-Zentraladministration anhand der unten stehenden Anweisungen:  
  
    ```  
    get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 Entweder Sie befinden sich in Windows PowerShell anstatt in der SharePoint-Verwaltungsshell, oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist nicht im SharePoint-Modus installiert. Weitere Informationen zu [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und PowerShell finden Sie unter [PowerShell-Cmdlets für SharePoint-Modus von Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
 Sie können den Dienst auch von der SharePoint-Zentraladministration starten anstatt den dritten PowerShell-Befehl auszuführen. Die folgenden Schritte sind auch nützlich, um sicherzustellen, dass der Dienst gestartet wurde.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Systemeinstellungen** auf **Dienste auf dem Server verwalten** .  
  
2.  Suchen Sie den **SQL Server Reporting Services-Dienst** , und klicken Sie in der Spalte Aktion auf **Starten** .  
  
3.  Der Status des Reporting Services-Diensts ändert sich von **Beendet** auf **Gestartet**. Installieren Sie den Reporting Services-Dienst mit PowerShell, wenn sich dieser nicht in der Liste befindet.  
  
    > [!NOTE]  
    >  Wenn der Reporting Services-Dienst im Status **Wird gestartet** bleibt und sich nicht in **Gestartet** ändert, stellen Sie sicher, dass der Dienst der SharePoint 2013-Administration im Windows Server-Manager gestartet wurde.  
  
##  <a name="bkmk_create_serrviceapplication"></a>Schritt 3: Erstellen einer Reporting Services-Dienst Anwendung  
 Dieser Abschnitt enthält die Schritte zum Erstellen einer Dienstanwendung und eine Beschreibung der Eigenschaften, wenn Sie eine vorhandene Dienstanwendung überprüfen.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Anwendungsverwaltung** auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie im SharePoint-Menüband auf die Schaltfläche **Neu** .  
  
3.  Klicken Sie im Menü Neu auf **SQL Server Reporting Services-Dienstanwendung**.  
  
    > [!IMPORTANT]  
    >  Wenn die Option "[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]" nicht in der Liste angezeigt wird, ist dies ein Hinweis darauf, **dass der gemeinsame Dienst "[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]" nicht installiert ist**. Lesen Sie den vorherigen Abschnitt, in dem das Installieren des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Diensts mithilfe von PowerShell-Cmdlets beschrieben wird.  
  
4.  Geben Sie auf der Seite **SQL Server Reporting Services-Dienstanwendung erstellen** einen Namen für die Anwendung ein. Wenn Sie mehrere Reporting Services-Dienstanwendungen erstellen, hilft ein aussagekräftiger Name oder eine Benennungskonvention bei der Organisation von Administrations- und Verwaltungsvorgängen.  
  
5.  Erstellen Sie im Abschnitt **Anwendungspool** einen neuen Anwendungspool für die Anwendung (empfohlen). Die Verwendung des gleichen Namens für den Anwendungspool und die Dienstanwendung kann Ihre laufenden Verwaltungsaufgaben vereinfachen. Die Wahl des Namens kann allerdings auch davon abhängen, wie viele Dienstanwendungen Sie erstellen und ob mehrere Anwendungen in einem einzelnen Anwendungspool verwendet werden müssen. Informieren Sie sich in der SharePoint Server-Dokumentation über Empfehlungen und Best Practices zur Verwaltung von Anwendungspools.  
  
     Wählen Sie ein Sicherheitskonto für den Anwendungspool aus, oder erstellen Sie es. Sie müssen ein Domänenbenutzerkonto angeben. Ein Domänenbenutzerkonto ermöglicht die Verwendung der in SharePoint verfügbaren Funktion "Verwaltetes Konto", mit der Sie Kennwörter und Kontoinformationen zentral aktualisieren können. Domänenkonten sind auch erforderlich, wenn Sie beabsichtigen, die Bereitstellung auf zusätzlichen Dienstinstanzen, die unter der gleichen Identität ausgeführt werden, zu skalieren.  
  
6.  Im **Datenbankserver**können Sie den aktuellen Server verwenden oder einen anderen SQL Server auswählen.  
  
7.  Der Standardwert von **Datenbankname** ist `ReportingService_<guid>`. Dies ist ein eindeutiger Datenbankname. Wenn Sie einen neuen Wert eingeben, geben Sie einen eindeutigen Wert ein. Dies ist die neue Datenbank, die speziell für die Dienstanwendung erstellt werden soll.  
  
8.  Der Standardwert unter **Datenbankauthentifizierung**lautet Windows-Authentifizierung. Wenn Sie **SQL-Authentifizierung**auswählen, finden Sie in der SharePoint-Dokumentation bewährte Methoden zur Verwendung dieses Authentifizierungstyps in einer SharePoint-Bereitstellung.  
  
9. Wählen Sie im Abschnitt **Webanwendungszuordnungen** die Webanwendung aus, die für Zugriff von der aktuellen Reporting Services-Dienstanwendung bereitgestellt werden soll. Sie können einer Webanwendung eine Reporting Services-Dienstanwendung zuordnen. Wenn alle aktuellen Webanwendungen bereits einer Reporting Services-Dienstanwendung zugeordnet sind, wird eine Warnmeldung angezeigt.  
  
10. Klicken Sie auf **OK**.  
  
11. Der Dienstanwendungserstellungsprozess dauert möglicherweise mehrere Minuten. Wenn es vollständig ist, sehen Sie eine Bestätigungsmeldung und einen Link zu einer Seite **Abonnements und Warnungen bereitstellen** . Führen Sie den Bereitstellungsschritt aus, wenn Sie die Datenwarnungs- oder Abonnementfunktion von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwenden möchten. Weitere Informationen finden Sie unter [Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
 ![PowerShell-Inhalt](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell Related Content") Informationen zur Verwendung von PowerShell zum Erstellen einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst Anwendung finden Sie unter:  
  
-   Weitere Informationen finden Sie im Abschnitt [Windows PowerShell-Skript für die Schritte 1 bis 4](#bkmk_full_script).  
  
-   Thema [So erstellen Sie eine Reporting Services-Dienstanwendung mit PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)  
  
##  <a name="bkmk_powerview"></a> Schritt 4: Aktivieren Sie die Power View Website Sammlungs Funktion.  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] ist eine Funktion des [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-Ins für [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint-Produkte und stellt eine Websitesammlungsfunktion dar. Die Funktion wird für Stammwebsitesammlungen und Websitesammlungen automatisch aktiviert, die nach der Installation des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins erstellt wurden. Wenn Sie die Verwendung von [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]planen, sollten Sie sicherstellen, dass die Funktion aktiviert ist.  
  
 Wenn Sie nach der Installation des SharePoint-Servers das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte installieren, werden die Berichtsserver-Integrationsfunktion und die Power View-Integrationsfunktion nur für Stammwebsitesammlungen aktiviert. Für andere Websitesammlungen müssen Sie die Funktionen manuell aktivieren.  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a>So aktivieren oder überprüfen Sie die Power View-Websitesammlungsfunktion  
  
1.  Bei folgenden Schritten wird davon ausgegangen, dass die SharePoint-Website für eine Umgebung mit **Version 2013**konfiguriert ist.  
  
     Öffnen Sie die gewünschte SharePoint-Website in Ihrem Browser. Zum Beispiel: http://\<servername>/sites/bi  
  
2.  Klicken Sie auf **Einstellungen**![SharePoint-Einstellungen](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint-Einstellungen").  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe **Websitesammlungsverwaltung** auf **Websitesammlungs-Funktionen**.  
  
5.  Suchen Sie **Power View-Integrationsfunktion** in der Liste.  
  
6.  Klicken Sie auf **Aktivieren**. Der Funktionsstatus ändert sich in **Aktiv**.  
  
 Diese Prozedur wird pro Websitesammlung abgeschlossen. Weitere Informationen finden Sie unter [Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md).  
  
##  <a name="bkmk_full_script"></a>Windows PowerShell-Skript für die Schritte 1-4  
 Das PowerShell-Skript in diesem Abschnitt entspricht dem Abschluss der Schritte 1 bis 4 in den vorangegangenen Schritten. Das Skript führt folgende Schritte aus:  
  
-   Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst und -Dienstproxy werden installiert, und der Dienst wird gestartet.  
  
-   Ein neuer Proxy namens „Reporting Services“ wird erstellt.  
  
-   Erstellt eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst Anwendung mit dem Namen "Reporting Services-Anwendung".  
  
-   Die [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Funktion für eine Websitesammlung wird aktiviert.  
  
 Parameter  
  
-   Aktualisieren Sie den Parameter **-Account** für den Dienstproxy. Dabei muss es sich um ein verwaltetes Dienstkonto in der SharePoint-Farm handeln. Weitere Informationen finden Sie im SharePoint-Thema [Planen von Administrator- und Dienstkonten in SharePoint 2013](https://technet.microsoft.com/library/cc263445.aspx).  
  
-   Aktualisieren Sie den **-DatabaseServer**-Parameter für die Dienstanwendung. Dieser Parameter entspricht der Instanz der Datenbank-Engine.  
  
-   Aktualisieren Sie den **-url**-Parameter der Website, für die die [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]-Funktion aktiviert werden soll.  
  
 **So verwenden Sie das Skript**  
  
1.  Öffnen Sie Windows PowerShell mit Administratorrechten.  
  
2.  Kopieren Sie folgenden Code in das Skriptfenster.  
  
3.  Aktualisieren Sie die drei im vorherigen Abschnitt beschriebenen Parameter, und führen Sie dann das Skript aus.  
  
```  
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
write-host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
write-host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy  
  
```  
  
##  <a name="bkmk_additional_config"></a> Zusätzliche Konfiguration  
 In diesem Abschnitt werden zusätzliche Konfigurationsschritte beschrieben, die in den meisten SharePoint-Bereitstellungen wichtig sind.  
  
###  <a name="bkmk_configure_ECS"></a>Konfigurieren von Excel Services und Power Pivot  
 Wenn Sie Power View-Berichte von [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] in einer Excel 2013-Arbeitsmappe in SharePoint anzeigen möchten, muss eine Excel Services-Anwendung in der Farm für die Verwendung eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Servers im SharePoint-Modus konfiguriert werden. Darüber hinaus muss das von der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung verwendete Sicherheitskonto für den Anwendungspool auf dem Analysis Services-Server Administratorrechte aufweisen. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   Der Abschnitt "Konfigurieren von Excel Services für Analysis Services Integration" in [PowerPivot für SharePoint 2013-Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).  
  
-   [Verwalten von Einstellungen für das Excel Services-Datenmodell (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).  
  
###  <a name="bkmk_provision_agent"></a> Abonnements und Warnungen bereitstellen  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Abonnements und -Datenwarnungen erfordern möglicherweise die Konfiguration von SQL Server-Agent-Berechtigungen. Wenn eine Fehlermeldung darauf hinweist, dass SQL Server-Agent erforderlich ist, Sie jedoch sichergestellt haben, dass SQL Server-Agent gestartet wurde, müssen Sie die Berechtigungen aktualisieren. Sie können auf der Seite mit der Erfolgsmeldung nach der Dienstanwendungserstellung auf den Link **Abonnements und Warnmeldungen bereitstellen** klicken, um eine andere Seite für die SQL Server-Agent-Bereitstellung aufzurufen. Der Bereitstellungsschritt ist erforderlich, wenn die Bereitstellung über mehrere Computer erfolgt (wenn sich z. B. die SQL Server-Datenbankinstanz auf einem anderen Computer befindet). Weitere Informationen finden Sie unter [Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a>Konfigurieren von E-Mail-Einstellungen für SSRS-Dienstanwendungen  
 Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenwarnungsfunktion sendet Warnungen in E-Mail-Nachrichten. Um E-Mails übermitteln zu können, kann es notwendig sein, dass Sie Ihre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung konfigurieren und die E-Mail-Übermittlungserweiterung für die Dienstanwendung ändern müssen. Die E-Mail-Einstellungen sind erforderlich, wenn Sie beabsichtigen, die E-Mail-Übermittlungserweiterung für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Abonnementfunktion zu verwenden. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a>Hinzufügen von Reporting Services-Inhaltstypen zu Inhaltsbibliotheken  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt vordefinierte Inhaltstypen bereit, die zum Verwalten freigegebener Datenquellendateien (RSDS), Berichtsmodelldateien (SMDL) und Berichts-Generator-Berichtsdefinitionsdateien (RDL) verwendet werden können. Wenn einer Bibliothek ein Inhaltstyp ( **Berichts-Generator-Bericht**, **Berichtsmodell**und **Berichtsdatenquelle** ) hinzugefügt wird, wird der Befehl **Neu** aktiviert, sodass Sie neue Dokumente des betreffenden Typs erstellen können. Weitere Informationen finden Sie unter [Hinzufügen von Berichts Server-Inhaltstypen &#40;zu einer Bibliothek Reporting Services im integrierten&#41;SharePoint-Modus](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
### <a name="activate-the-report-server-file-sync-feature"></a>Aktivieren des Features zur Berichtsserver-Dateisynchronisierung  
 Wenn Benutzer häufig veröffentlichte Berichtselemente direkt in SharePoint-Dokumentbibliotheken hochladen, ist das Feature zur **Berichtsserver-Dateisynchronisierung** auf Websiteebene hilfreich. Die Dateisynchronisierungsfunktion synchronisiert den Berichtsserverkatalog regelmäßiger mit Elementen in Dokumentbibliotheken. Weitere Informationen finden Sie unter [Aktivieren des Features zur Berichtsserver-Dateisynchronisierung in der SharePoint-Zentraladministration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).  
  
##  <a name="bkmk_verify_installation"></a> Überprüfen der Installation  
 Im Folgenden werden Schritte und Verfahren vorgeschlagen, um die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung im SharePoint-Modus zu überprüfen.  
  
-   Weitere Informationen finden Sie im SharePoint-Abschnitt im Thema zur Bereitstellung [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).  
  
-   Erstellen Sie in einer SharePoint-Dokumentbibliothek einen grundlegenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bericht, der nur ein Textfeld enthält, z. B. einen Titel. Der Bericht enthält keine Datenquellen oder Datasets. Ziel ist es, zu überprüfen, ob Sie den Berichts-Generator öffnen und einen grundlegenden Bericht erstellen und in der Vorschau anzeigen können.  
  
     Speichern Sie den Bericht in der Dokumentbibliothek, und führen Sie den Bericht dann aus der Bibliothek heraus aus. Weitere Informationen zum Erstellen von Berichten mit dem Berichts-Generator finden Sie unter [Starten des Berichts-Generators (Berichts-Generator)](https://technet.microsoft.com/library/ms159221.aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [PowerShell-Cmdlets für SharePoint-Modus von Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
 [Aktualisieren und Migrieren von Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 Roadmap für [content: Einrichten und Konfigurieren von SharePoint Server und SQL Server BI @ no__t-0 @ no__t-1  
 [Funktionen, die von den Editionen von SQL Server 2012   unterstützt werden](https://go.microsoft.com/fwlink/?linkid=232473)  
 [Reporting Services-SharePoint-Dienst und -Dienstanwendungen](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
  
  
