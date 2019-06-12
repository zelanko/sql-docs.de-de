---
title: Reporting Services-Konfigurationsdateien | Microsoft-Dokumentation
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], configuration files
- configuration options [Reporting Services]
- modifying configuration files
- configuration files [Reporting Services]
ms.assetid: 21e5c32f-ad67-4917-b55a-8e21bd64f5a6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25b695456bbac34e2c6ce8bf8c312c4108dd852e
ms.sourcegitcommit: 561cee96844b82ade6cf543a228028ad5c310768
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66506655"
---
# <a name="reporting-services-configuration-files"></a>Reporting Services-Konfigurationsdateien
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] speichert Komponenteninformationen in der Registrierung und in Konfigurationsdateien, die bei der Installation in das Dateisystem kopiert werden. Konfigurationsdateien enthalten eine Kombination aus nur intern verwendeten und benutzerdefinierten Werten. Werte werden vom Benutzer durch die Konfigurationstools, die Befehlszeilen-Hilfsprogramme und manuelles Bearbeiten der Konfigurationsdateien definiert.  
  
 Die Konfigurationsdateien müssen nur dann geändert werden, wenn Sie erweiterte Einstellungen hinzufügen oder konfigurieren. Konfigurationseinstellungen werden als XML-Elemente oder -Attribute angegeben. Wenn Sie sich mit XML und Konfigurationsdateien auskennen, können Sie mit einem Text- oder Code-Editor benutzerdefinierbare Einstellungen ändern. Weitere Informationen über die Vorgehensweise zur Änderung einer Konfigurationsdatei, oder darüber, wie der Berichtsserver neue und aktualisierte Konfigurationseinstellungen liest, finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei („RSreportserver.config“)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
> [!NOTE]  
> In früheren Versionen wies der Berichts-Manager seine eigene Konfigurationsdatei mit dem Namen RSWebApplication.config auf. Diese Datei ist jetzt veraltet. Haben Sie eine frühere Installation aktualisiert, wird diese Datei nicht gelöscht, der Berichtsserver kann jedoch keine Einstellungen aus dieser Datei lesen. Wenn die Datei auf dem Computer vorhanden ist, sollten Sie sie löschen. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen werden alle Berichts-Manager-Konfigurationseinstellungen in der Datei RSReportServer.config gespeichert und aus ihr gelesen. Eine Liste der Einstellungen, die gelöscht oder verschoben wurden, finden Sie unter [Aktuelle Änderungen in SQL Server Reporting Services in SQL Server 2016](../../reporting-services/breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
 Inhalt dieses Artikels  
  
-   [Überblick über Konfigurationsdateien (einheitlicher Modus)](#bkmk_config_file_Summary_native_mode)  
  
-   [Überblick über Konfigurationsdateien (SharePoint-Modus)](#bkmk_config_file_Summary_sharepoint_mode)  
  
##  <a name="bkmk_config_file_Summary_native_mode">Überblick über Konfigurationsdateien (einheitlicher Modus)</a>  
 Die nachstehende Tabelle enthält eine Beschreibung der Speicherorte von Konfigurationseinstellungen. Die meisten Konfigurationseinstellungen werden in Konfigurationsdateien gespeichert, die in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]enthalten sind. Standardmäßig wird folgendes Installationsverzeichnis verwendet:  
  
''' Pfade installieren  
C:\Program Files\Microsoft SQL Server\MSRSxx.MSSQLSERVER (wobei Xx der MS SQL-Versionsnummer ist) oder  
C:\Program Files\Microsoft SQL Server Reporting Services\SSRS  
  Abhängig von der SSRS-version
```  
  
|Stored in:|Description|Location|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Stores configuration settings for feature areas of the Report Server service: Report Manager or the web portal, the Report Server Web service, and background processing. For more information about each setting, see [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSSrvPolicy.config|Stores the code access security policies for the server extensions. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSMgrPolicy.config|Stores the code access security policies for the web portal. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportManager|  
|Web.config for the Report Server Web service|Includes only those settings that are required for ASP.NET.|\<Installation directory> \Reporting Services \ReportServer|  
|Web.config for Report Manager|Includes only those settings that are required for ASP.NET if applicable for the SSRS version.|\<Installation directory> \Reporting Services \ReportManager|  
|ReportingServicesService.exe.config|Stores configuration settings that specify the trace levels and logging options for the Report Server service. For more information about the elements in this file, see [ReportingServicesService Configuration File](../../reporting-services/report-server/reportingservicesservice-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer \Bin|  
|Registry settings|Stores configuration state and other settings used to uninstall Reporting Services. If you are troubleshooting an installation or configuration problem, you can view these settings to get information about how the report server is configured.<br /><br /> Do not modify these settings directly as this can invalidate your installation.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<InstanceID\> \Setup<br /><br /> **- And -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Services\ReportServer|  
|RSReportDesigner.config|Stores configuration settings for Report Designer. For more information, see [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<drive>:\Program Files \Microsoft Visual Studio 10 \Common7 \IDE \PrivateAssemblies.|  
|RSPreviewPolicy.config|Stores the code access security policies for the server extensions used during report preview. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssembliesr|  
  
##  <a name="bkmk_config_file_Summary_sharepoint_mode"></a> Summary of configuration Files (SharePoint mode)  
 The following table provides a description of configuration files used for a SharePoint mode report server. Most configuration settings are stored in SharePoint service application databases. For more information, see [Reporting Services SharePoint Service and Service Applications](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md).  
  
 By default, the installation directory for SharePoint mode is the following:  
  
```Install path
C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting  
```  
  
|Gespeichert in:|und Beschreibung|Speicherort|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Speichert Konfigurationseinstellungen für Funktionsbereiche des Berichtsserverdiensts: Berichts-Manager, Report Server-Webdienst und Hintergrundverarbeitung. Weitere Informationen zu den einzelnen Einstellungen finden Sie unter [RSReportServer.config-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Installationsverzeichnis>\Reporting Services\ReportServer|  
|RSSrvPolicy.config|Speichert die Codezugriffs-Sicherheitsrichtlinien für die Servererweiterungen. Weitere Informationen zu dieser Datei finden Sie unter [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installationsverzeichnis>\Reporting Services\ReportServer|  
|Web.config für den Report Server-Webdienst.|Enthält nur die Einstellungen, die ggf. für die SSRS-Version für ASP.NET erforderlich sind.|\<Installationsverzeichnis>\Reporting Services\ReportServer|  
|Registrierungseinstellungen|Speichert den Konfigurationsstatus und andere Einstellungen für die Deinstallation von Reporting Services. Speichert darüber hinaus auch Informationen zu jeder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung.<br /><br /> Ändern Sie diese Einstellungen nicht direkt, da dies die Installation ungültig machen kann.|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceID\>\Setup<br /><br /> Beispiel für eine Instanz-ID: MSSQL13.MSSQLSERVER<br /><br /> **- und -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Reporting Services\Service Applications|  
|RSReportDesigner.config|Speichert Konfigurationseinstellungen für den Berichts-Designer. Weitere Informationen finden Sie unter [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<Laufwerk>:\Programme\Microsoft Visual Studio 10\Common7\IDE\PrivateAssemblies.|  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Erweiterungen für Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)   
 [rsconfig-Hilfsprogramm (SSRS)](../../reporting-services/tools/rsconfig-utility-ssrs.md)   
 [Start and Stop the Report Server Service (Starten und Beenden des Berichtsserverdiensts)](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
