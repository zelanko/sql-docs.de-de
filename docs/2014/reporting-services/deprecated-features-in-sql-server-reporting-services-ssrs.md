---
title: Als veraltet markierte Funktionen in SQL Server Reporting Services in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
caps.latest.revision: 49
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6817f31ff83e1a502506893f66b5080399200fd8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305140"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>Als veraltet markierte Funktionen in SQL Server Reporting Services in SQL Server 2014
  In diesem Thema werden die veralteten [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen beschrieben. Die Funktionen sind immer noch in der Version verfügbar, in der sie veraltet sind. Es ist jedoch geplant, die Funktionen in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu entfernen. Als veraltet markierte Funktionen sollten in neuen Anwendungen nicht verwendet werden.  
  
 In diesem Thema:  
  
-   [Als veraltet markierte Funktionen in SQL Server 2014 Reporting Services](#bkmk_2014)  
  
-   [Als veraltet markierte Funktionen in SQL Server 2012 SP1 Reporting Services](#bkmk_2012sp1)  
  
-   [Als veraltet markierte Funktionen in SQL Server 2012 Reporting Services](#bkmk_2012)  
  
-   [Als veraltet markierte Funktionen in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_2014"></a> Als veraltet markierte Funktionen in SQL Server 2014 Reporting Services  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Funktionen, die in der nächsten Version von SQL Server nicht unterstützt werden  
 Die folgenden [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Funktionen werden nicht unterstützt werden, der **Weiter** Version [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, in denen diese Funktionen zurzeit verwendet werden.  
  
#### <a name="html-rendering-extension-device-information-settings"></a>HTML-Renderingerweiterung für Geräteinformationseinstellungen  
 Die Geräteinformationseinstellungen für die HTML-Renderingerweiterung sind veraltet.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Weitere Informationen über die HTML-Renderingerweiterung finden Sie unter [HTML Device Information Settings](html-device-information-settings.md)  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Rendern von Microsoft Word und Microsoft Excel 1997-2003  
 Die[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8-Renderingerweiterungen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] meldet die [!INCLUDE[msCoName](../includes/msconame-md.md)] Word und [!INCLUDE[msCoName](../includes/msconame-md.md)] binären Austauschdateiformat Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] umfasst Erweiterungen, die im Rendern der [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML-Format.  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>Berichtsdefinitionssprache (RDL) 2005 und früher  
 Report Definition Language (RDL) 2005 und früher ist veraltet. Weitere Informationen zu RDL finden Sie unter [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Weitere Informationen zum Aktualisieren von Berichten finden Sie unter [Aktualisieren von Berichten](install-windows/upgrade-reports.md).  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 und frühere benutzerdefinierte Berichtselemente  
 Benutzerdefinierte Berichtselemente (CRI) kompiliert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 und früher sind veraltet.  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services Snapshots 2005 und früher  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] kompiliert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 und früher sind veraltet.  
  
#### <a name="report-models"></a>Berichtsmodelle  
 Semantische Modellierungssprachberichtsmodelle (SMDL) sind veraltet. Obwohl Sie können Sie auch weiterhin verwenden Sie vorhandene Berichtsmodelle als Datenquellen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] meldet, sollten Sie erwägen, aktualisieren Ihren Berichten zu ihrer Abhängigkeit von Berichtsmodellen zu entfernen.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] schließt keine Tools zum Erstellen oder Aktualisieren von Berichtsmodellen ein. Weitere Informationen finden Sie unter [wichtige Änderungen in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Veraltete Methoden im Webdienstendpunkt  
 Die folgenden Vorgänge sind als veraltet markiert, der <xref:ReportService2010.ReportingService2010> Webdienst-Endpunkt:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>SharePoint-Webparts  
 Die für die Installation erforderliche CAB-Datei **RSWebParts.cab** und die SharePoint-Webparts, die aus der CAB-Datei extrahiert werden können, sind veraltet. Die veralteten Webparts sind Berichts-Explorer (**SPExplorer.dwp**) und Berichts-Viewer (**SPViewer.dwp**).  
  
 Weitere Informationen zu den veralteten Webparts finden Sie unter [Anzeigen und Durchsuchen von Berichten im einheitlichen Modus mithilfe von SharePoint-Webparts (SSRS)](http://msdn.microsoft.com/library/ms159772.aspx)  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Funktionen, die in einer zukünftigen Version von SQL Server nicht unterstützt werden  
 Die folgenden Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]noch unterstützt, aber in zukünftigen Versionen entfernt. Die betreffende Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurde noch nicht festgelegt.  
  
 Keine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] veraltete Features wurden [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
##  <a name="bkmk_2012sp1"></a> Als veraltet markierte Funktionen in SQL Server 2012 SP1 Reporting Services  
 In diesem Abschnitt wird beschrieben, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] veraltete Features in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]. Die folgenden Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden in der nächsten Version von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]noch unterstützt, aber in zukünftigen Versionen entfernt. Die betreffende Version von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] wurde noch nicht festgelegt.  
  
### <a name="sharepoint-web-parts"></a>SharePoint-Webparts  
 Die für die Installation erforderliche CAB-Datei **RSWebParts.cab** und die SharePoint-Webparts, die aus der CAB-Datei extrahiert werden können, sind veraltet. Die veralteten Webparts sind Berichts-Explorer (**SPExplorer.dwp**) und Berichts-Viewer (**SPViewer.dwp**).  
  
 Weitere Informationen zu den veralteten Webparts finden Sie unter [Anzeigen und Durchsuchen von Berichten im einheitlichen Modus mithilfe von SharePoint-Webparts (SSRS)](http://msdn.microsoft.com/library/ms159772.aspx)  
  
##  <a name="bkmk_2012"></a> Als veraltet markierte Funktionen in SQL Server 2012 Reporting Services  
 In diesem Abschnitt wird beschrieben, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] veraltete Features in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
### <a name="html-rendering-extension-device-information-settings"></a>HTML-Renderingerweiterung für Geräteinformationseinstellungen  
 Die Geräteinformationseinstellungen für die HTML-Renderingerweiterung sind veraltet.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Weitere Informationen über die HTML-Renderingerweiterung finden Sie unter [HTML Device Information Settings](html-device-information-settings.md)  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Rendern von Microsoft Word und Microsoft Excel 1997-2003  
 Die[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8-Renderingerweiterungen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] meldet die [!INCLUDE[msCoName](../includes/msconame-md.md)] Word und [!INCLUDE[msCoName](../includes/msconame-md.md)] binären Austauschdateiformat Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] umfasst Erweiterungen, die im Rendern der [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML-Format.  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>Berichtsdefinitionssprache (RDL) 2005 und früher  
 Report Definition Language (RDL) 2005 und früher ist veraltet. Weitere Informationen zu RDL finden Sie unter [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Weitere Informationen zum Aktualisieren von Berichten finden Sie unter [Aktualisieren von Berichten](install-windows/upgrade-reports.md).  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 und frühere benutzerdefinierte Berichtselemente  
 Benutzerdefinierte Berichtselemente (CRI) kompiliert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 und früher sind veraltet.  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services Snapshots 2005 und früher  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] kompiliert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 und früher sind veraltet.  
  
### <a name="report-models"></a>Berichtsmodelle  
 Semantische Modellierungssprachberichtsmodelle (SMDL) sind veraltet. Obwohl Sie können Sie auch weiterhin verwenden Sie vorhandene Berichtsmodelle als Datenquellen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] meldet, sollten Sie erwägen, aktualisieren Ihren Berichten zu ihrer Abhängigkeit von Berichtsmodellen zu entfernen.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] schließt keine Tools zum Erstellen oder Aktualisieren von Berichtsmodellen ein. Weitere Informationen finden Sie unter [wichtige Änderungen in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Veraltete Methoden im Webdienstendpunkt  
 Die folgenden Vorgänge sind als veraltet markiert, der <xref:ReportService2010.ReportingService2010> Webdienst-Endpunkt:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="bkmk_kj"></a> Als veraltet markierte Funktionen in SQL Server 2008 R2 Reporting Services  
  
> [!NOTE]  
>  Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.  
  
### <a name="report-server-web-service-endpoints"></a>Report Server-Webdienst-Endpunkte  
 Die Webdienste <xref:ReportService2005.ReportingService2005> und <xref:ReportService2006.ReportingService2006> sind in dieser Version veraltet. Diese Endpunkte wurden durch einen neuen Endpunkt ersetzt: <xref:ReportService2010.ReportingService2010>.  
  
 Der neue Endpunkt enthält die gesamte Funktionalität der veralteten Endpunkte und die neuen Funktionen, die in SQL Server 2008 R2 eingeführt wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Abwärtskompatibilität](../getting-started/backward-compatibility.md)   
 [Verhaltensänderungen in SQL Server Reporting Services in SQLServer 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
