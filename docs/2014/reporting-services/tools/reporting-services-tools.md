---
title: Reporting Services-Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
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
manager: kfile
ms.openlocfilehash: 8cbe5a25ef6ca87c2ffa5fd83c8ff1ca0796fdae
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59939846"
---
# <a name="reporting-services-tools"></a>Reporting Services-Tools
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält einen Satz von grafischen Tools und Skriptingtools, die die Entwicklung und Verwendung ausführlicher Berichte in einer verwalteten Umgebung unterstützen. Darin enthalten sind Entwicklungstools, Konfigurations- und Administrationstools sowie Tools zur Berichtsanzeige. Dieses Thema enthält eine kurze Übersicht zu jedem Tool in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und wie darauf zugegriffen werden kann.  
  
 Ein Tool sofort finden Sie unter [Lernprogramm: So suchen und starten Sie den Reporting Services-Tools &#40;SSRS&#41;](tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md).  
  
## <a name="tools-for-report-authoring"></a>Tools zur Berichtserstellung  
 In der folgenden Tabelle sind die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]verfügbaren Tools zu Berichterstellung aufgeführt.  
  
|Tool|Description|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|Dieses Tool ermöglicht die interaktive Durchsuchung und visuelle Darstellung von Daten und lässt Sie Berichte erstellen und mit Berichten basierend auf tabellarischen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Modellen interagieren.<br /><br /> Hinweis: Erfordert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus.|Browser mit Silverlight.|  
|Berichts-Designer|Verwenden Sie dieses Tool, um Berichte zu entwerfen und diese auf einem Berichtsserver im einheitlichen Modus oder im SharePoint-Modus bereitzustellen.<br /><br /> Gehostet in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<br /><br /> Berichtsdatenbereich, um im Bericht verwendete Daten zu organisieren<br /><br /> Sichten im Registerformat für Entwurf und Vorschau zum interaktiven Berichtsentwurf<br /><br /> Mithilfe von Abfrage-Designern kann festgelegt werden, welche Daten aus Datenquellen abgerufen werden sollen, und die Datenquellentypen in der [RSReportDesigner-Konfigurationsdatei](../report-server/rsreportdesigner-configuration-file.md)zugeordnet sind.<br /><br /> Ausdrucks-Editor mit IntelliSense, um [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Ausdrücke zu erstellen, mit denen Berichtsinhalte und -darstellung angepasst werden können.<br /><br /> Unterstützt benutzerdefinierte Berichtselemente und Abfrage-Designer<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|Berichts-Generator|Verwenden Sie dieses Tool, um Berichte zu entwerfen und diese auf einem Berichtsserver im einheitlichen Modus oder im SharePoint-Modus bereitzustellen.<br /><br /> [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office-ähnliche Erstellungsumgebung<br /><br /> Fähigkeit, Berichtselemente als Berichtsteile zu speichern<br /><br /> Ein Assistent zum Erstellen von Karten<br /><br /> Aggregate von Aggregaten<br /><br /> Verbesserte Unterstützung für Ausdrücke<br /><br /> Mithilfe von Abfrage-Designern kann festgelegt werden, welche Daten aus einer Auswahl von integrierten Datenquellentypen abgerufen werden sollen.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Berichts-Generator &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md).|Herunterladen von MSI oder Öffnen vom Berichts-Manager/SharePoint|  
  
## <a name="tools-for-report-server-administration"></a>SQL Server-Tools für Berichtsserververwaltung  
 Zum Verwalten des Berichtsservers in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ist ein Satz von grafischen Tools und Skriptingtools verfügbar. Welche Tools Sie verwenden hängt vom Bereitstellungsmodus Ihres Berichtsservers ab.  
  
### <a name="native-mode"></a>im einheitlichen Modus  
 In der folgenden Tabelle sind die verfügbaren Tools zum Verwalten des Berichtsservers, der im einheitlichen Modus bereitgestellt wird, aufgeführt.  
  
|Tool|Description|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|Reporting Services-Konfigurations-Manager|Verwenden Sie dieses Tool, um eine Reporting Services-Installation zu konfigurieren. Beachten Sie, dass der Konfigurations-Manager für Reporting Services nicht berichtsserverinhalt verwalten hilfreich ist, zusätzliche Funktionen aktivieren oder Zugriff auf den Server gewähren. Zu den verfügbare Tasks gehören:<br /><br /> Konfigurieren von Berichtsserverinstanzen (lokal und remote)<br /><br /> Konfigurieren des Berichtsserver-Dienstkontos<br /><br /> Erstellen und Konfigurieren von einer oder mehrerer Webdienst-URL<br /><br /> Konfigurieren der Berichts-Manager-URL<br /><br /> Erstellen und Konfigurieren der Berichtsserver-Datenbank<br /><br /> Konfigurieren einer Bereitstellung für horizontales Skalieren<br /><br /> Sichern, Wiederherstellen oder Ersetzen des symmetrischen Schlüssels, der verwendet wird, um gespeicherte Verbindungszeichenfolgen und Anmeldeinformationen zu verschlüsseln.<br /><br /> Konfigurieren des Kontos für die unbeaufsichtigte Ausführung<br /><br /> Konfigurieren eines SMTP-Servers zur E-Mail-Übermittlung<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).|Startmenü|  
|SQL Server Management Studio|Verwenden Sie dieses Tool, um eine oder mehrere Berichtsserverinstanzen in einer einzigen Umgebung zu verwalten, einschließlich:<br /><br /> Verwalten von Berichtsserverinstanzen (lokal und remote)<br /><br /> Festlegen von Berichtsservereigenschaften<br /><br /> Ändern von Rollendefinitionen<br /><br /> Deaktivieren von nicht verwendeten Berichtsserverfunktionen<br /><br /> Verwalten von Aufträgen<br /><br /> Verwalten von freigegebenen Zeitplänen|Startmenü|  
|SQL Server-Konfigurations-Manager|Verwenden Sie dieses Tool, um Folgendes zu tun:<br /><br /> Installieren und starten Sie die gemeinsamen Dienste für Reporting Services.<br /><br /> Konfigurieren der Berichterstellung für Kundenfeedback, des Speicherverzeichnisorts und der Fehlerberichterstellung<br /><br /> <br /><br /> **\*\* Warnung \* \***  verwenden Sie dieses Tool nicht zum Konfigurieren des Dienstkontos. Verwenden Sie stattdessen das Reporting Services-Konfigurationstool.<br /><br /> Weitere Informationen finden Sie unter [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md).|Startmenü|  
|Rsconfig-Hilfsprogramm|Verwenden Sie dieses Tool, um eine Berichtsserververbindung zur Berichtsserver-Datenbank zu konfigurieren und zu verwalten. Darüber hinaus können Sie damit ein Benutzerkonto für die unbeaufsichtigte Berichtsverarbeitung angeben.<br /><br /> Weitere Informationen finden Sie unter [Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)](report-server-command-prompt-utilities-ssrs.md).|Eingabeaufforderung|  
|Hilfsprogramm rskeymgmt|Verwenden Sie dieses Tool, um Folgendes zu tun:<br /><br /> Extrahieren, Wiederherstellen, Erstellen und Löschen des symmetrischen Schlüssels, der zur Verschlüsselung der Berichtsserverdaten verwendet wird<br /><br /> Verknüpfen von Berichtsserverinstanzen in einer Bereitstellung für horizontales Skalieren<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)](report-server-command-prompt-utilities-ssrs.md).|Eingabeaufforderung|  
|WMI-Klassen (Windows Management Instrumentation, Windows-Verwaltungsinstrumentation)|Verwenden Sie diese Klassen, um die Konfigurationstasks in Reporting Services-Konfigurations-Manager zu automatisieren, ohne dabei die grafische Benutzeroberfläche verwenden zu müssen.<br /><br /> Weitere Informationen finden Sie unter [Programmgesteuerter Zugriff auf den WMI-Anbieter](../accessing-the-wmi-provider-programmatically.md).|Visual Basic-Skript|  
  
### <a name="sharepoint-integrated-mode"></a>Integrierter SharePoint-Modus  
 Im SharePoint-Modus ist Reporting Services eine Dienstanwendung in der SharePoint-Architektur und wird direkt durch SharePoint verwaltet  
  
|Tool|Description|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|SharePoint-Zentraladministration|Verwenden Sie SharePoint-Zentraladministration, um die freigegebenen Dienstanwendungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]zu erstellen, abzufragen und zu verwalten.<br /><br /> Weitere Informationen finden Sie unter [Konfiguration und Verwaltung eines Berichtsservers &#40;SharePoint-Modus von Reporting Services&#41;](../configure-administer-report-server-reporting-services-sharepoint-mode.md).|Browser zur SharePoint-Website-URL für Zentraladministration|  
|PowerShell-Cmdlets|Verwenden Sie PowerShell-Cmdlets, um die freigegebenen Dienstanwendungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]zu erstellen, abzufragen und zu verwalten.<br /><br /> Weitere Informationen finden Sie unter [PowerShell-Cmdlets für SharePoint-Modus von Reporting Services](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|SharePoint 2010-Verwaltungsshell|  
  
## <a name="tools-for-report-content-management"></a>Tools für die Berichtsinhaltsverwaltung  
 Zum Verwalten der Inhalte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ist ein Satz von grafischen Tools und Skriptingtools verfügbar. Welche Tools Sie verwenden hängt vom Bereitstellungsmodus Ihres Berichtsservers ab.  
  
|Tool|Description|So erfolgt der Zugriff|  
|----------|-----------------|-------------------|  
|URL des Report Server-Webdiensts|Verwenden Sie dieses Tool, um Inhalte im Berichtskatalog auf einer generischen Elementnavigationsseite zu durchsuchen.<br /><br /> Weitere Informationen finden Sie unter [Report Server Web Service](../report-server-web-service/report-server-web-service.md).|-Browser|  
|Berichts-Manager|**(Nur im einheitlichen Modus)** Verwenden Sie dieses Tool, um über einer HTTP-Verbindung eine einzelne Berichtsserverinstanz von einem Remotestandort zu verwalten. Sie können folgendermaßen vorgehen:<br /><br /> Anzeigen, Suchen, Drucken und Abonnieren von Berichten.<br /><br /> Erstellen, Sichern und Warten der Ordnerhierarchie zum Organisieren von Elementen auf dem Server.<br /><br /> Konfigurieren der rollenbasierten Sicherheit, die den Zugriff auf Elemente und Vorgänge bestimmt.<br /><br /> Konfigurieren von Berichtsausführungseigenschaften, dem Berichtsverlauf und Berichtsparameter.<br /><br /> Erstellen von Berichtsmodellen, die eine Verbindung zu einer Microsoft SQL Server Analysis Services-Datenquelle oder einer relationalen SQL Server-Datenquelle herstellen bzw. Daten daraus abrufen.<br /><br /> Festlegen der Modellelementsicherheit für den Zugriff auf bestimmte Entitäten im Modell bzw. Zuordnen von Entitäten zu vordefinierten Berichten mit Durchklicken, die Sie im Voraus erstellen.<br /><br /> Erstellen freigegebener Zeitpläne und Datenquellen für eine leichtere Verwaltung von Zeitplänen und Datenquellenverbindungen.<br /><br /> Erstellen datengesteuerter Abonnements, die Berichte an eine lange Empfängerliste verteilen.<br /><br /> Erstellen verknüpfter Berichte zur Wiederverwendung und Änderung des Zwecks eines vorhandenen Berichts auf verschiedene Weise.<br /><br /> Starten des Berichts-Generators zum Erstellen von Berichten, die Sie auf dem Berichtsserver speichern und ausführen können.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Berichts-Manager (einheitlicher SSRS-Modus)](../report-manager-ssrs-native-mode.md).||  
|RS-Hilfsprogramm|Dieses Tool ist ein Skripthost, den Sie zum Ausführen von Skriptvorgängen verwenden können. Führen Sie mit diesem Tool [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Skripts aus, die Daten zwischen Berichtsserver-Datenbanken kopieren, Berichte veröffentlichen, Elemente in einer Berichtsserver-Datenbank erstellen usw.<br /><br /> Weitere Informationen finden Sie unter [Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)](report-server-command-prompt-utilities-ssrs.md).|Eingabeaufforderung|  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Berichtsserver](../reporting-services-report-server.md)   
 [Konzepte von Reporting Services (SSRS)](../reporting-services-concepts-ssrs.md)   
 [Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
