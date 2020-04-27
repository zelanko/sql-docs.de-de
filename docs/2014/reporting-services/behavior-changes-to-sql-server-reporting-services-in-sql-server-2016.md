---
title: Verhaltensänderungen in SQL Server Reporting Services in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91fa7a66981f3e36c7e25babffbf73dc2519a0c2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109938"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>Verhaltensänderungen in SQL Server Reporting Services in SQL Server 2014
  In diesem Thema werden Änderungen im Verhalten von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]beschrieben. Ein verändertes Programmverhalten beeinflusst die Funktionsweise und das Interagieren von Funktionen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] im Vergleich zu früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Inhalte dieses Themas:  
  
-   [SQL Server 2014 Reporting Services Verhaltensänderungen](#bkmk_sql14)  
  
-   [Verändertes Programmverhalten von SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Verändertes Programmverhalten von SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-behavior-changes"></a><a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services Verhaltensänderungen  
 Das Verhalten von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] wurde in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]nicht geändert.  
  
##  <a name="sssql11-reporting-services-behavior-changes"></a><a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services Verhaltensänderungen  
 In diesem Abschnitt wird das veränderte Programmverhalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben.  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>Mit der Berechtigung "Elemente anzeigen" können keine freigegebenen Datasets (SharePoint-Modus) heruntergeladen werden  
 **Neues Verhalten:** Benutzer mit der SharePoint-Berechtigung "Elemente anzeigen" können den Inhalt von Reporting Services freigegebenen Datasets nicht mehr herunterladen. Diese Behavior Change ist nun mit den Berechtigungen "Elemente anzeigen" für Berichte, Datenquellen und Modelle konsistent. Benutzer mit der Berechtigung Elemente anzeigen können Berichte, Datenquellen und Modelle anzeigen und ausführen, aber Sie können ihren Inhalt nicht herunterladen.  
  
 **Vorheriges Verhalten:** Benutzer mit der SharePoint-Berechtigung "Elemente anzeigen" können den Inhalt von Reporting Services freigegebenen Datasets herunterladen.  
  
 Weitere Informationen zu den SharePoint-Berechtigungsstufen finden Sie unter [Benutzerberechtigungen und Berechtigungsstufen](https://technet.microsoft.com/library/cc721640.aspx)  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>Berichtsserver-Ablaufverfolgungsprotokolle befinden sich an einem neuen Speicherort für den SharePoint-Modus  
 **Neues Verhalten:** Die Berichtsserver-Ablaufverfolgungsprotokolle für einen im SharePoint-Modus installierten Berichtsserver werden unter %Programme%\Gemeinsame Dateien\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles gespeichert.  
  
 **Vorheriges Verhalten:** Berichts Server-Ablauf Verfolgungs Protokolle wurden unter einem Pfad gefunden, der dem folgenden ähnelt:%ProgramFilesDir%\Microsoft SQL Server\\<RS_instance> \Reporting Services\LogFiles  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>GetServerConfigInfo SOAP-API wird nicht mehr unterstützt (SharePoint-Modus)  
 **Neues Verhalten**: Verwenden Sie das PowerShell-Cmdlet "Get-sprsserviceapplicationservers".  
  
 **Vorheriges Verhalten:** Kunden konnten SOAP-Clientcode für die direkte Kommunikation mit dem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Endpunkt entwickeln und "GetReportServerConfigInfo()" aufrufen.  
  
### <a name="report-server-configuration-and-management-tools"></a>Berichtsserverkonfiguration und Verwaltungstools  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>Der Konfigurations-Manager wird nicht für den SharePoint-Modus verwendet  
 **Neues Verhalten:** Der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Konfigurations-Manager unterstützt Berichtsserver im SharePoint-Modus nicht mehr. Der SharePoint-Modus von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] kann jetzt mit der SharePoint-Zentraladministration konfiguriert werden. Aus diesem Grund unterstützt der Konfigurations-Manager von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] den SharePoint-Modus nicht mehr. Der Konfigurations-Manager wird nur noch für Berichtsserver im einheitlichen Modus verwendet.  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>Sie können den Modus des Servers nicht in einen anderen ändern  
 **Neues Verhalten:** Sie können keine Servermodi ändern. Wenn Sie einen Berichtsserver im einheitlichen Modus installieren, können Sie ihn nicht in den SharePoint-Modus ändern oder für den SharePoint-Modus neu konfigurieren. Wenn Sie den Berichtsserver im SharePoint-Modus installieren, können Sie ihn in den einheitlichen Modus ändern.  
  
 **Vorheriges Verhalten:** Der Kunde installiert einen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver im SharePoint-Modus. Wenn der Berichtsserver in den einheitlichen Modus geändert werden soll, kann der Kunde den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Konfigurations-Manager öffnen und zum einheitlichen Modus wechseln, indem er eine neue Datenbank im einheitlichen Modus erstellt oder eine Verbindung mit einer vorhandenen Datenbank im einheitlichen Modus herstellt. Eine weitere Möglichkeit besteht darin, mit dem Konfigurations-Manager für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] vom SharePoint-Modus in den einheitlichen Modus zu wechseln.  
  
##  <a name="sql-server-2008-r2-reporting-services-behavior-changes"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services Verhaltensänderungen  
 In diesem Abschnitt werden Verhaltensänderungen [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]in beschrieben.  
  
> [!NOTE]  
>  Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>SecureConnectionLevel-Eigenschaft in der WMI-Anbieterbibliothek von Reporting Services  
 In der WMI-Anbieter Bibliothek [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]für lässt die **SecureConnectionLevel** - `0``1``2``3` `0` `3` `1` Eigenschaft Werte von,,, zu. Dies bedeutet, dass Secure Socket Layer (SSL) für keine der Webdienst Methoden erforderlich ist, gibt an, dass SSL für alle Webdienst Methoden erforderlich ist, `2` und und gibt Teilmengen von Webdienst Methoden an, die SSL erfordern. In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]haben diese Werte nur zwei mögliche Bedeutungen:  
  
-   `0` gibt an, dass SSL für keine der Webdienstmethoden erforderlich ist.  
  
-   Eine positive ganze Zahl gibt an, dass SSL für alle Webdienstmethoden erforderlich ist.  
  
 Diese Änderung wirkt sich darauf aus, wie der Berichtsserver auf Webdienstaufrufe reagiert. Gibt z. <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> b. jetzt nichts zurück, wenn **SecureConnectionLevel** auf 0 festgelegt ist, <xref:ReportService2005.ReportingService2005> und alle Methoden in, wenn **SecureConnectionLevel** auf `1`, `2`oder `3`festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Als veraltet markierte Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Nicht mehr unterstützte Funktionen zum SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Aktuelle Änderungen in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
