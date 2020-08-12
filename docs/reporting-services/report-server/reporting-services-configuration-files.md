---
title: Reporting Services-Konfigurationsdateien | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie mehr über Konfigurationsdateien, in denen Reporting Services Informationen zu Komponenten speichert. Unter Umständen müssen Sie die Dateien ändern, um erweiterte Einstellungen hinzufügen oder konfigurieren zu können.
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
ms.openlocfilehash: c9a56dd5cb8e26c57f25f458eff96b467df16cf6
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541462"
---
# <a name="reporting-services-configuration-files"></a>Reporting Services-Konfigurationsdateien
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] speichert Komponenteninformationen in der Registrierung und in Konfigurationsdateien, die bei der Installation in das Dateisystem kopiert werden. Konfigurationsdateien enthalten eine Kombination aus nur intern verwendeten und benutzerdefinierten Werten. Werte werden vom Benutzer durch die Konfigurationstools, die Befehlszeilen-Hilfsprogramme und manuelles Bearbeiten der Konfigurationsdateien definiert.  
  
 Die Konfigurationsdateien müssen nur dann geändert werden, wenn Sie erweiterte Einstellungen hinzufügen oder konfigurieren. Konfigurationseinstellungen werden als XML-Elemente oder -Attribute angegeben. Wenn Sie sich mit XML und Konfigurationsdateien auskennen, können Sie mit einem Text- oder Code-Editor benutzerdefinierbare Einstellungen ändern. Weitere Informationen über die Vorgehensweise zur Änderung einer Konfigurationsdatei, oder darüber, wie der Berichtsserver neue und aktualisierte Konfigurationseinstellungen liest, finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei („RSreportserver.config“)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
> [!NOTE]  
> In früheren Versionen wies der Berichts-Manager seine eigene Konfigurationsdatei mit dem Namen RSWebApplication.config auf. Diese Datei ist jetzt veraltet. Haben Sie eine frühere Installation aktualisiert, wird diese Datei nicht gelöscht, der Berichtsserver kann jedoch keine Einstellungen aus dieser Datei lesen. Wenn die Datei auf dem Computer vorhanden ist, sollten Sie sie löschen. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen werden alle Konfigurationseinstellungen für Berichts-Manager und Webportal in der Datei „RSReportServer.config“ gespeichert und aus ihr gelesen. Eine Liste der Einstellungen, die gelöscht oder verschoben wurden, finden Sie unter [Aktuelle Änderungen in SQL Server Reporting Services in SQL Server 2016](../../reporting-services/breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
 Inhalt dieses Artikels:  
  
-   [Überblick über Konfigurationsdateien (einheitlicher Modus)](#bkmk_config_file_Summary_native_mode)  
  
-   [Überblick über Konfigurationsdateien (SharePoint-Modus)](#bkmk_config_file_Summary_sharepoint_mode)  
  
##  <a name="summary-of-configuration-files-native-mode"></a><a name="bkmk_config_file_Summary_native_mode"></a> Überblick über Konfigurationsdateien (einheitlicher Modus)  
 Die nachstehende Tabelle enthält eine Beschreibung der Speicherorte von Konfigurationseinstellungen. Die meisten Konfigurationseinstellungen werden in Konfigurationsdateien gespeichert, die in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]enthalten sind. Standardmäßig wird folgendes Installationsverzeichnis verwendet:  
  
```
Install Paths  
C:\Program Files\Microsoft SQL Server\MSRSxx.MSSQLSERVER  (where xx is the MS SQL version number)
  or  
C:\Program Files\Microsoft SQL Server Reporting Services\SSRS  
  depending on the SSRS version
```  
  
|Gespeichert in:|BESCHREIBUNG|Standort|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Speichert Konfigurationseinstellungen für Funktionsbereiche des Berichtsserverdiensts: Berichts-Manager oder Webportal, Report Server-Webdienst und Hintergrundverarbeitung. Weitere Informationen zu den einzelnen Einstellungen finden Sie unter [RSReportServer.config-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSSrvPolicy.config|Speichert die Codezugriffs-Sicherheitsrichtlinien für die Servererweiterungen. Weitere Informationen zu dieser Datei finden Sie unter [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSMgrPolicy.config|Speichert die Codezugriffssicherheitsrichtlinien für das Webportal. Weitere Informationen zu dieser Datei finden Sie unter [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportManager|  
|Web.config für den Report Server-Webdienst.|Enthält nur Einstellungen, die für ASP.NET erforderlich sind.|\<Installation directory> \Reporting Services \ReportServer|  
|Web.config für den Berichts-Manager.|Enthält nur Einstellungen, die für ASP.NET erforderlich und für die SSRS-Version verfügbar sind.|\<Installation directory> \Reporting Services \ReportManager|  
|ReportingServicesService.exe.config|Speichert Konfigurationseinstellungen, die die Ablaufverfolgungsebenen und Protokolloptionen für den Berichtsserverdienst angeben. Weitere Informationen zu den Elementen in dieser Datei finden Sie unter [ReportingServicesService Configuration File](../../reporting-services/report-server/reportingservicesservice-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer \Bin|  
|Registrierungseinstellungen|Speichert den Konfigurationsstatus und andere Einstellungen für die Deinstallation von Reporting Services. Wenn Sie ein Installations- oder Konfigurationsproblem beheben möchten, liefern diese Einstellungen Informationen darüber, wie der Berichtsserver konfiguriert ist.<br /><br /> Ändern Sie diese Einstellungen nicht direkt, da dies die Installation ungültig machen kann.|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceID\>\Setup<br /><br /> **- und -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Services\ReportServer|  
|RSReportDesigner.config|Speichert Konfigurationseinstellungen für den Berichts-Designer. Weitere Informationen finden Sie unter [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<drive>:\Programme \Microsoft Visual Studio 10 \Common7 \IDE \PrivateAssemblies.|  
|RSPreviewPolicy.config|Speichert die Codezugriffs-Sicherheitsrichtlinien für die Servererweiterungen, die während der Berichtsvorschau verwendet werden. Weitere Informationen zu dieser Datei finden Sie unter [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|C:\Programme\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssembliesr|  
  
##  <a name="summary-of-configuration-files-sharepoint-mode"></a><a name="bkmk_config_file_Summary_sharepoint_mode"></a> Überblick über Konfigurationsdateien (SharePoint-Modus)  
 Die folgende Tabelle enthält eine Beschreibung der Konfigurationsdateien, die für einen Berichtsserver im SharePoint-Modus verwendet werden. Die meisten Konfigurationseinstellungen werden in Datenbanken der SharePoint-Dienstanwendung gespeichert. Weitere Informationen finden Sie unter [Reporting Services-SharePoint-Dienst und -Dienstanwendungen](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md).  
  
 Standardmäßig wird das folgende Installationsverzeichnis für den SharePoint-Modus verwendet:  
  
```
Install path
C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting  
```  
  
|Gespeichert in:|BESCHREIBUNG|Standort|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Speichert Konfigurationseinstellungen für Funktionsbereiche des Berichtsserverdiensts: Berichts-Manager oder Webportal, Report Server-Webdienst und Hintergrundverarbeitung. Weitere Informationen zu den einzelnen Einstellungen finden Sie unter [RSReportServer.config-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSSrvPolicy.config|Speichert die Codezugriffs-Sicherheitsrichtlinien für die Servererweiterungen. Weitere Informationen zu dieser Datei finden Sie unter [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportServer|  
|Web.config für den Report Server-Webdienst.|Enthält nur Einstellungen, die für ASP.NET erforderlich und für die SSRS-Version verfügbar sind.|\<Installation directory> \Reporting Services \ReportServer|  
|Registrierungseinstellungen|Speichert den Konfigurationsstatus und andere Einstellungen für die Deinstallation von Reporting Services. Speichert darüber hinaus auch Informationen zu jeder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung.<br /><br /> Ändern Sie diese Einstellungen nicht direkt, da dies die Installation ungültig machen kann.|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceID\>\Setup<br /><br /> Beispielinstanz-ID: MSSQL13.MSSQLSERVER<br /><br /> **- und -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Reporting Services\Service Applications|  
|RSReportDesigner.config|Speichert Konfigurationseinstellungen für den Berichts-Designer. Weitere Informationen finden Sie unter [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<drive>:\Programme \Microsoft Visual Studio 10 \Common7 \IDE \PrivateAssemblies.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Erweiterungen für Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)   
 [rsconfig-Hilfsprogramm (SSRS)](../../reporting-services/tools/rsconfig-utility-ssrs.md)   
 [Start and Stop the Report Server Service (Starten und Beenden des Berichtsserverdiensts)](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
