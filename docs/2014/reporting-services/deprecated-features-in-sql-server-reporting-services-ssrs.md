---
title: Als veraltet markierte Features in SQL Server Reporting Services in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5cbef64cbed910018e7d2f8dae1844074aaa3f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109351"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>Als veraltet markierte Funktionen in SQL Server Reporting Services in SQL Server 2014
  In diesem Thema werden die veralteten [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen beschrieben. Die Funktionen sind immer noch in der Version verfügbar, in der sie veraltet sind. Es ist jedoch geplant, die Funktionen in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu entfernen. Als veraltet markierte Funktionen sollten in neuen Anwendungen nicht verwendet werden.  
  
 Inhalte dieses Themas:  
  
-   [Als veraltet markierte Funktionen in SQL Server 2014 Reporting Services](#bkmk_2014)  
  
-   [Als veraltet markierte Funktionen in SQL Server 2012 SP1 Reporting Services](#bkmk_2012sp1)  
  
-   [Als veraltet markierte Funktionen in SQL Server 2012 Reporting Services](#bkmk_2012)  
  
-   [Als veraltet markierte Funktionen in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a>SQL Server 2014 Reporting Services als veraltet markierte Funktionen  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Funktionen, die in der nächsten Version von SQL Server nicht unterstützt werden  
 Die folgenden [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen werden in der **nächsten** Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr unterstützt. Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, in denen diese Funktionen zurzeit verwendet werden.  
  
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
 Die[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -BIFF8-Renderingerweiterungen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] senden Berichte im binären Austauschdateiformat von [!INCLUDE[msCoName](../includes/msconame-md.md)] Word und [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]schließt Erweiterungen ein, die im [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML-Format Rendering.  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>Berichtsdefinitionssprache (RDL) 2005 und früher  
 Report Definition Language (RDL) 2005 und früher ist veraltet. Weitere Informationen zu RDL finden Sie unter [Berichts Definitions Sprache &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Weitere Informationen zum Aktualisieren von Berichten von Sie unter [Upgrade Reports](install-windows/upgrade-reports.md).  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 und frühere benutzerdefinierte Berichtselemente  
 Benutzerdefinierte Berichts Elemente (CRI), [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] die für 2005 und früher kompiliert wurden, sind veraltet.  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services Snapshots 2005 und früher  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 und früher gerenderte Momentaufnahmen sind veraltet.  
  
#### <a name="report-models"></a>Berichtsmodelle  
 Semantische Modellierungssprachberichtsmodelle (SMDL) sind veraltet. Obwohl Sie weiterhin vorhandene Berichts Modelle als Datenquellen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichten verwenden können, sollten Sie Ihre Berichte aktualisieren, um ihre Abhängigkeit von Berichts Modellen zu entfernen.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält keine Tools zum Erstellen oder Aktualisieren von Berichts Modellen. Weitere Informationen finden Sie unter [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Veraltete Methoden im Webdienstendpunkt  
 Die folgenden Vorgänge sind im <xref:ReportService2010.ReportingService2010>-Webdienstendpunkt als veraltet markiert:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>SharePoint-Webparts  
 Die für die Installation erforderliche CAB-Datei **RSWebParts.cab** und die SharePoint-Webparts, die aus der CAB-Datei extrahiert werden können, sind veraltet. Die veralteten Webparts sind Berichts-Explorer (**SPExplorer.dwp**) und Berichts-Viewer (**SPViewer.dwp**).  
  
 Weitere Informationen zu den veralteten Webparts finden Sie unter [Anzeigen und Durchsuchen von Berichten im einheitlichen Modus mithilfe von SharePoint-Webparts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Funktionen, die in einer zukünftigen Version von SQL Server nicht unterstützt werden  
 Die folgenden Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]noch unterstützt, aber in zukünftigen Versionen entfernt. Die betreffende Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurde noch nicht festgelegt.  
  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] wurden keine [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Funktionen als veraltet markiert.  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a>SQL Server 2012 SP1 Reporting Services als veraltet markierte Funktionen  
 In diesem Abschnitt werden als veraltet markierte [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]beschrieben. Die folgenden Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden in der nächsten Version von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]noch unterstützt, aber in zukünftigen Versionen entfernt. Die betreffende Version von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] wurde noch nicht festgelegt.  
  
### <a name="sharepoint-web-parts"></a>SharePoint-Webparts  
 Die für die Installation erforderliche CAB-Datei **RSWebParts.cab** und die SharePoint-Webparts, die aus der CAB-Datei extrahiert werden können, sind veraltet. Die veralteten Webparts sind Berichts-Explorer (**SPExplorer.dwp**) und Berichts-Viewer (**SPViewer.dwp**).  
  
 Weitere Informationen zu den veralteten Webparts finden Sie unter [Anzeigen und Durchsuchen von Berichten im einheitlichen Modus mithilfe von SharePoint-Webparts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a>SQL Server 2012 Reporting Services als veraltet markierte Funktionen  
 In diesem Abschnitt werden als veraltet markierte [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]beschrieben.  
  
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
 Die[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -BIFF8-Renderingerweiterungen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] senden Berichte im binären Austauschdateiformat von [!INCLUDE[msCoName](../includes/msconame-md.md)] Word und [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]schließt Erweiterungen ein, die im [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML-Format Rendering.  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>Berichtsdefinitionssprache (RDL) 2005 und früher  
 Report Definition Language (RDL) 2005 und früher ist veraltet. Weitere Informationen zu RDL finden Sie unter [Berichts Definitions Sprache &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Weitere Informationen zum Aktualisieren von Berichten von Sie unter [Upgrade Reports](install-windows/upgrade-reports.md).  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 und frühere benutzerdefinierte Berichtselemente  
 Benutzerdefinierte Berichts Elemente (CRI), [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] die für 2005 und früher kompiliert wurden, sind veraltet.  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services Snapshots 2005 und früher  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 und früher gerenderte Momentaufnahmen sind veraltet.  
  
### <a name="report-models"></a>Berichtsmodelle  
 Semantische Modellierungssprachberichtsmodelle (SMDL) sind veraltet. Obwohl Sie weiterhin vorhandene Berichts Modelle als Datenquellen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Berichten verwenden können, sollten Sie Ihre Berichte aktualisieren, um ihre Abhängigkeit von Berichts Modellen zu entfernen.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält keine Tools zum Erstellen oder Aktualisieren von Berichts Modellen. Weitere Informationen finden Sie unter [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Veraltete Methoden im Webdienstendpunkt  
 Die folgenden Vorgänge sind im <xref:ReportService2010.ReportingService2010>-Webdienstendpunkt als veraltet markiert:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services als veraltet markierte Funktionen  
  
> [!NOTE]  
>  Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.  
  
### <a name="report-server-web-service-endpoints"></a>Report Server-Webdienst-Endpunkte  
 Die Webdienste <xref:ReportService2005.ReportingService2005> und <xref:ReportService2006.ReportingService2006> wurden in dieser Version als veraltet markiert. Diese Endpunkte wurden durch einen neuen Endpunkt ersetzt: <xref:ReportService2010.ReportingService2010>.  
  
 Der neue Endpunkt enthält die gesamte Funktionalität der veralteten Endpunkte und die neuen Funktionen, die in SQL Server 2008 R2 eingeführt wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Abwärtskompatibilität](../getting-started/backward-compatibility.md)   
 [Verhaltensänderungen in SQL Server Reporting Services in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
