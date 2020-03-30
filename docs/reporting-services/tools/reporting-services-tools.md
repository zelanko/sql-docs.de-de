---
title: Reporting Services-Tools | Microsoft-Dokumentation
ms.date: 06/06/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
helpviewer_keywords:
- SSRS, tools
- Reporting Services, tools
- components [Reporting Services]
- components [Reporting Services], about components
- Reporting Services, components
- SSRS, components
- reports [Reporting Services], tools
- SQL Server Reporting Services, components
- SQL Server Reporting Services, tools
- architecture [Reporting Services]
ms.assetid: 23d616e3-eb90-43fb-9b7a-869bd7e22e7b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8e5a060e58019d79b44d42feeb396854807c19f8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "66826916"
---
# <a name="reporting-services-tools"></a>Reporting Services-Tools
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält mehrere grafische Tools und Skripterstellungstools, die die Entwicklung und Verwendung ausführlicher Berichte in einer verwalteten Umgebung unterstützen. Darin enthalten sind Entwicklungstools, Konfigurations- und Administrationstools sowie Tools zur Berichtsanzeige. Dieser Artikel enthält eine kurze Übersicht zu jedem Tool in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und wie darauf zugegriffen werden kann.  
  
 Um sofort ein Tool zu finden, sehen Sie sich [Tutorial: So suchen und starten Sie Reporting Services-Tools (SSRS)](../../reporting-services/tools/tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md) an.  
  
## <a name="tools-for-report-authoring"></a>Tools zur Berichtserstellung  
 In der folgenden Tabelle werden die verfügbaren Berichterstellungs-Tools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aufgeführt.  
  
|Tool|BESCHREIBUNG|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|[!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]|Mit [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] können Sie mobile Berichte erstellen, deren Inhalt dynamisch an den jeweiligen Bildschirm bzw. das Browserfenster angepasst wird und sich so jeder Bildschirmgröße anpassen.<br /><br /> Das Tool bietet eine Entwurfsoberfläche mit anpassbaren Rasterzeilen und -spalten und flexiblen Elementen für mobile Berichte.<br /><br /> Weitere Informationen finden Sie unter [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md).|Download des [Publishers für mobile Berichte von SQL Server](https://go.microsoft.com/fwlink/?LinkId=733527)|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|Dieses Tool ermöglicht die interaktive Durchsuchung und visuelle Darstellung von Daten und lässt Sie Berichte erstellen und mit Berichten basierend auf tabellarischen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Modellen interagieren.|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint-Modus. Browser mit Silverlight.|  
|Berichts-Designer|Verwenden Sie dieses Tool zum Entwerfen von Berichten. Es umfasst die folgenden Funktionen:<br /><br /> Bereitstellung auf einem Berichtsserver im einheitlichen Modus oder im SharePoint-Modus.<br /><br /> Gehostet in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<br /><br /> Berichtsdatenbereich, um im Bericht verwendete Daten zu organisieren<br /><br /> Sichten im Registerformat für Entwurf und Vorschau zum interaktiven Berichtsentwurf<br /><br /> Mithilfe von Abfrage-Designern kann festgelegt werden, welche Daten aus Datenquellen abgerufen werden sollen, und die Datenquellentypen in der [RSReportDesigner-Konfigurationsdatei](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)zugeordnet sind.<br /><br /> Ausdrucks-Editor mit IntelliSense, um [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Ausdrücke zu erstellen, mit denen Berichtsinhalte und -darstellung angepasst werden können.<br /><br /> Unterstützt benutzerdefinierte Berichtselemente und Abfrage-Designer<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md).|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|Berichts-Generator|Verwenden Sie dieses Tool zum Entwerfen von Berichten. Es umfasst die folgenden Funktionen:<br /><br /> Bereitstellung auf einem Berichtsserver im einheitlichen Modus oder im SharePoint-Modus.<br /><br /> [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office-ähnliche Erstellungsumgebung[!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]<br /><br /> Fähigkeit, Berichtselemente als Berichtsteile zu speichern<br /><br /> Ein Assistent zum Erstellen von Karten<br /><br /> Aggregate von Aggregaten<br /><br /> Verbesserte Unterstützung für Ausdrücke<br /><br /> Mithilfe von Abfrage-Designern kann festgelegt werden, welche Daten aus einer Auswahl von integrierten Datenquellentypen abgerufen werden sollen.<br /><br /> Weitere Informationen finden Sie unter [Berichts-Generator in SQL Server](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md).|Download der [eigenständigen Version des Berichts-Generators](https://go.microsoft.com/fwlink/?LinkID=219138)<br /><br /> Alternativ können Sie das Tool über das Webportal oder über SharePoint aufrufen.|  
  
## <a name="tools-for-report-server-administration"></a>SQL Server-Tools für Berichtsserververwaltung  
 Dabei handelt es sich um grafische Tools und Skripterstellungstools, die für die Verwaltung des Berichtsservers in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zur Verfügung gestellt werden. Welche Tools Sie verwenden hängt vom Bereitstellungsmodus Ihres Berichtsservers ab.  
  
### <a name="native-mode"></a>Einheitlicher Modus  
 In der folgenden Tabelle sind die verfügbaren Tools zum Verwalten des Berichtsservers, der im einheitlichen Modus bereitgestellt wird, aufgeführt.  
  
|Tool|BESCHREIBUNG|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|Reporting Services-Konfigurations-Manager|Verwenden Sie dieses Tool, um eine Reporting Services-Installation zu konfigurieren. Zu den verfügbare Tasks gehören:<br /><br />  Konfigurieren des Berichtsserver-Dienstkontos<br /><br /> Erstellen und Konfigurieren von einer oder mehrerer Webdienst-URL<br /><br /> Konfigurieren der URL für das Webportal<br /><br /> Erstellen und Konfigurieren der Berichtsserver-Datenbank<br /><br /> Konfigurieren einer Bereitstellung für horizontales Skalieren<br /><br /> Sichern, Wiederherstellen oder Ersetzen des symmetrischen Schlüssels, der verwendet wird, um gespeicherte Verbindungszeichenfolgen und Anmeldeinformationen zu verschlüsseln.<br /><br /> Konfigurieren des Kontos für die unbeaufsichtigte Ausführung<br /><br /> Konfigurieren der Abonnementeinstellungen<br /><br /> Konfigurieren eines SMTP-Servers zur E-Mail-Übermittlung<br /><br /> Konfigurieren des Power BI-Diensts (Cloud)<br /><br /> Hinweis: Mit dem Reporting Services-Konfigurations-Manager können Sie keine Berichtsserverinhalte verwalten, zusätzliche Funktionen aktivieren oder Zugriff auf den Server gewähren.<br /><br /> Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).|Startmenü|  
|SQL Server Management Studio|Verwenden Sie dieses Tool, um eine oder mehrere Berichtsserverinstanzen in einer einzigen Umgebung zu verwalten, einschließlich:<br /><br /> Verwalten von Berichtsserverinstanzen (lokal und remote)<br /><br /> Festlegen von Berichtsservereigenschaften<br /><br /> Ändern von Rollendefinitionen<br /><br /> Deaktivieren von nicht verwendeten Berichtsserverfunktionen<br /><br /> Verwalten von Aufträgen<br /><br /> Verwalten von freigegebenen Zeitplänen|Startmenü|   
|Rsconfig-Hilfsprogramm|Verwenden Sie dieses Tool, um eine Berichtsserververbindung zur Berichtsserver-Datenbank zu konfigurieren und zu verwalten. Darüber hinaus können Sie damit ein Benutzerkonto für die unbeaufsichtigte Berichtsverarbeitung angeben.<br /><br /> Weitere Informationen finden Sie unter [Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md).|Eingabeaufforderung|  
|Hilfsprogramm rskeymgmt|Verwenden Sie dieses Tool, um Folgendes zu tun:<br /><br /> Extrahieren, Wiederherstellen, Erstellen und Löschen des symmetrischen Schlüssels, der zur Verschlüsselung der Berichtsserverdaten verwendet wird<br /><br /> Verknüpfen von Berichtsserverinstanzen in einer Bereitstellung für horizontales Skalieren<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md).|Eingabeaufforderung|  
|WMI-Klassen (Windows Management Instrumentation, Windows-Verwaltungsinstrumentation)|Verwenden Sie diese Klassen, um die Konfigurationstasks in Reporting Services-Konfigurations-Manager zu automatisieren, ohne dabei die grafische Benutzeroberfläche verwenden zu müssen.<br /><br /> Weitere Informationen finden Sie unter [Programmgesteuerter Zugriff auf den WMI-Anbieter](../../reporting-services/accessing-the-wmi-provider-programmatically.md).|Visual Basic-Skript|  
  
### <a name="sharepoint-integrated-mode"></a>Integrierter SharePoint-Modus  
 Im SharePoint-Modus ist Reporting Services eine Dienstanwendung in der SharePoint-Architektur und wird direkt durch SharePoint verwaltet  
  
|Tool|BESCHREIBUNG|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|SharePoint-Zentraladministration|Verwenden Sie SharePoint-Zentraladministration, um die freigegebenen Dienstanwendungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]zu erstellen, abzufragen und zu verwalten.<br /><br /> Weitere Informationen finden Sie unter [Konfiguration und Verwaltung eines Berichtsservers &#40;SharePoint-Modus von Reporting Services&#41;](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md).|Browser zur SharePoint-Website-URL für Zentraladministration|  
|PowerShell-Cmdlets|Verwenden Sie PowerShell-Cmdlets, um die freigegebenen Dienstanwendungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]zu erstellen, abzufragen und zu verwalten.<br /><br /> Weitere Informationen finden Sie unter [PowerShell-Cmdlets für SharePoint-Modus von Reporting Services](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|SharePoint 2010-Verwaltungsshell|  
  
## <a name="tools-for-report-content-management"></a>Tools für die Berichtsinhaltsverwaltung  
 Dabei handelt es sich um grafische Tools und Skripterstellungstools, die für die Verwaltung des Inhalts in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zur Verfügung gestellt werden. Welche Tools Sie verwenden hängt vom Bereitstellungsmodus Ihres Berichtsservers ab.  
  
|Tool|BESCHREIBUNG|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|URL des Report Server-Webdiensts|Verwenden Sie dieses Tool, um Inhalte im Berichtskatalog auf einer generischen Elementnavigationsseite zu durchsuchen.<br /><br /> Weitere Informationen finden Sie unter [Report Server Web Service](../../reporting-services/report-server-web-service/report-server-web-service.md).|Browser|  
|Webportal|**(Nur im einheitlichen Modus)** Verwenden Sie dieses Tool, um über einer HTTP-Verbindung eine einzelne Berichtsserverinstanz von einem Remotestandort zu verwalten. Sie können folgendermaßen vorgehen:<br /><br /> Anzeigen, Suchen, Drucken und Abonnieren von Berichten.<br /><br /> Erstellen, Sichern und Warten der Ordnerhierarchie zum Organisieren von Elementen auf dem Server.<br /><br /> Konfigurieren der rollenbasierten Sicherheit, die den Zugriff auf Elemente und Vorgänge bestimmt.<br /><br /> Konfigurieren von Berichtsausführungseigenschaften, dem Berichtsverlauf und Berichtsparameter.<br /><br /> Erstellen von Berichtsmodellen, die eine Verbindung zu einer Microsoft SQL Server Analysis Services-Datenquelle oder einer relationalen SQL Server-Datenquelle herstellen bzw. Daten daraus abrufen.<br /><br /> Festlegen der Modellelementsicherheit für den Zugriff auf bestimmte Entitäten im Modell bzw. Zuordnen von Entitäten zu vordefinierten Berichten mit Durchklicken, die Sie im Voraus erstellen.<br /><br /> Erstellen freigegebener Zeitpläne und Datenquellen für eine leichtere Verwaltung von Zeitplänen und Datenquellenverbindungen.<br /><br /> Erstellen datengesteuerter Abonnements, die Berichte an eine lange Empfängerliste verteilen.<br /><br /> Erstellen verknüpfter Berichte zur Wiederverwendung und Änderung des Zwecks eines vorhandenen Berichts auf verschiedene Weise.<br /><br /> Starten des Berichts-Generators zum Erstellen von Berichten, die Sie auf dem Berichtsserver speichern und ausführen können. Weitere Informationen finden Sie unter [Das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md).| Browser  
|RS-Hilfsprogramm|Dieses Tool ist ein Skripthost, den Sie zum Ausführen von Skriptvorgängen verwenden können. Führen Sie mit diesem Tool [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Skripts aus, die Daten zwischen Berichtsserver-Datenbanken kopieren, Berichte veröffentlichen, Elemente in einer Berichtsserver-Datenbank erstellen usw. Weitere Informationen finden Sie unter [Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md).|Eingabeaufforderung|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Berichtsserver](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)   
 [Konzepte von Reporting Services (SSRS)](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Was ist SQL Server Reporting Services (SSRS)?](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  