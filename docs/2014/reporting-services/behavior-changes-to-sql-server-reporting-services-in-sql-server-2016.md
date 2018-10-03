---
title: Verhaltensänderungen in SQL Server Reporting Services in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a8533552a48acd695ca7216ba6881b33369d5b1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116373"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>Verhaltensänderungen in SQL Server Reporting Services in SQL Server 2014
  In diesem Thema werden Änderungen im Verhalten von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]beschrieben. Ein verändertes Programmverhalten beeinflusst die Funktionsweise und das Interagieren von Funktionen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] im Vergleich zu früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 In diesem Thema:  
  
-   [Verändertes Programmverhalten von SQL Server 2014 Reporting Services](#bkmk_sql14)  
  
-   [Verändertes Programmverhalten von SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Verändertes Programmverhalten in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services – Verhaltensänderungen  
 Es gibt keine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] verhaltensänderungen [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services – Verhaltensänderungen  
 In diesem Abschnitt wird das veränderte Programmverhalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben.  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>Mit der Berechtigung "Elemente anzeigen" können keine freigegebenen Datasets (SharePoint-Modus) heruntergeladen werden  
 **Neues Verhalten:** Benutzer mit der SharePoint-Berechtigung Elemente anzeigen können den Inhalt von freigegebenen Reporting Services-Datasets nicht mehr herunterladen. Dieses geänderte Verhalten ist jetzt mit der Berechtigung Elemente anzeigen für Berichte, Datenquellen und Modelle konsistent. Benutzer mit der Berechtigung Elemente anzeigen können Berichte, Datenquellen und Modelle anzeigen und ausführen, aber sie können den Inhalt nicht herunterladen.  
  
 **Vorheriges Verhalten:** Benutzer mit der SharePoint-Berechtigung Elemente anzeigen konnten den Inhalt von freigegebenen Reporting Services-Datasets herunterladen.  
  
 Weitere Informationen zu den SharePoint-Berechtigungsstufen finden Sie unter [Benutzerberechtigungen und Berechtigungsstufen](http://technet.microsoft.com/library/cc721640.aspx)  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>Berichtsserver-Ablaufverfolgungsprotokolle befinden sich an einem neuen Speicherort für den SharePoint-Modus  
 **Neues Verhalten:** Die Berichtsserver-Ablaufverfolgungsprotokolle für einen im SharePoint-Modus installierten Berichtsserver werden unter %Programme%\Gemeinsame Dateien\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles gespeichert.  
  
 **Vorheriges Verhalten:** Berichtsserver-Ablaufverfolgungsprotokolle wurden finden Sie unter einem ähnlichen Pfad wie dem folgenden: %Programfilesdir%\Microsoft SQL Server\\< RS_instance > \reporting  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>GetServerConfigInfo SOAP-API wird nicht mehr unterstützt (SharePoint-Modus)  
 **Neues Verhalten**: Verwenden Sie den PowerShell-Cmdlet "Get-SPRSServiceApplicationServers".  
  
 **Vorheriges Verhalten:** Kunden konnten SOAP-Clientcode zur direkten Kommunikation mit entwickeln die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Endpunkt und getreportserverconfiginfo()".  
  
### <a name="report-server-configuration-and-management-tools"></a>Berichtsserverkonfiguration und Verwaltungstools  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>Der Konfigurations-Manager wird nicht für den SharePoint-Modus verwendet  
 **Neues Verhalten:** der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager nicht mehr unterstützt Berichtsserver im SharePoint-Modus. Konfiguration der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus kann jetzt mithilfe von SharePoint-Zentraladministration abgeschlossen werden und daher [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager unterstützt die SharePoint-Modus nicht mehr. Der Konfigurations-Manager wird nur noch für Berichtsserver im einheitlichen Modus verwendet.  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>Sie können den Modus des Servers nicht in einen anderen ändern  
 **Neues Verhalten:** Sie können keine Servermodi ändern. Wenn Sie einen Berichtsserver im einheitlichen Modus installieren, können Sie ihn nicht in den SharePoint-Modus ändern oder für den SharePoint-Modus neu konfigurieren. Wenn Sie den Berichtsserver im SharePoint-Modus installieren, können Sie ihn in den einheitlichen Modus ändern.  
  
 **Vorheriges Verhalten:** Kunde installiert einen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichtsserver im SharePoint-Modus. Wenn der Berichtsserver in den einheitlichen Modus geändert werden soll, kann der Kunde den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Konfigurations-Manager öffnen und zum einheitlichen Modus wechseln, indem er eine neue Datenbank im einheitlichen Modus erstellt oder eine Verbindung mit einer vorhandenen Datenbank im einheitlichen Modus herstellt. Kunden können auch [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager, um die vom SharePoint-Modus zum einheitlichen Modus zu wechseln.  
  
##  <a name="bkmk_kj"></a> Verändertes Programmverhalten in SQL Server 2008 R2 Reporting Services  
 In diesem Abschnitt wird beschrieben, Änderungen im Verhalten [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>SecureConnectionLevel-Eigenschaft in der WMI-Anbieterbibliothek von Reporting Services  
 In der WMI-Anbieterbibliothek für [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], **SecureConnectionLevel** Eigenschaft ermöglicht die Werte eines `0`,`1`,`2`,`3`, mit `0` Gibt an, dass Secure Socket Layer (SSL) nicht für alle von der Webdienstmethoden erforderlich ist `3` gibt an, dass SSL für alle Webdienstmethoden erforderlich ist und `1` und `2` geben Teilmengen von Webdienstmethoden die SSL erfordern. In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], diese Werte werden nur zwei mögliche Bedeutungen haben:  
  
-   `0` gibt an, dass SSL für keine der Webdienstmethoden erforderlich ist.  
  
-   Eine positive ganze Zahl gibt an, dass SSL für alle Webdienstmethoden erforderlich ist.  
  
 Diese Änderung wirkt sich darauf aus, wie der Berichtsserver auf Webdienstaufrufe reagiert. Z. B. <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> jetzt gibt nichts zurück Wenn **SecureConnectionLevel** ist auf 0 festgelegt sowie alle Methoden in <xref:ReportService2005.ReportingService2005> Wenn **SecureConnectionLevel** nastaven NA hodnotu `1`, `2`, oder `3`.  
  
## <a name="see-also"></a>Siehe auch  
 [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Als veraltet markierte Funktionen in SQL Server Reporting Services in SQLServer 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQLServer 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
