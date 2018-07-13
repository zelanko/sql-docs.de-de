---
title: Installieren von SQL Server-BI-Funktionen mit SharePoint (PowerPivot und Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 85ded5847bbb2bc1c32336e999b3579925a4e930
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325540"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>Installieren der BI-Funktionen von SQL Server mit SharePoint (PowerPivot und Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] kann in einer Microsoft SharePoint-Farm zu Business Intelligence (BI)-Funktionen in SharePoint integriert werden. Zu den Features zählen [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] Dient zum [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Datenzugriff in einer SharePoint-Farm. 
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ist die Daten-Engine für Arbeitsmappen, die in [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel erstellt werden und auf die über eine SharePoint-Bibliothek zugegriffen wird. Nach dem Speichern einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe in SharePoint können Sie sie als Datenquelle für [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Berichte.  
  
 Einige der Installations- und Konfigurationsschritte, die für SharePoint 2010 erforderlich sind, unterscheiden sich von den Schritten, die für SharePoint 2013 erforderlich sind. Einige der Themen in diesem Abschnitt gelten für beide Versionen von SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 ![Beachten Sie](../../../2014/reporting-services/media/rs-fyinote.png "Hinweis") die aktuellen versionsanmerkungen finden Sie unter [Versionsanmerkungen für SQL Server 2014](http://go.microsoft.com/fwlink/?LinkID=296445).  
  
##  <a name="bkmk_top"></a> In diesem Thema  
  
-   [Szenarien für SQL Server BI und SharePoint 2013](#bkmk_bi_scenarios)  
  
-   [Übersicht über die Installation](#bkmk_install_sharepoint2013_overview)  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Zusätzlich zu den Informationen in diesem Thema werden die folgenden verwandten Themen behandelt.  
  
 [Bereitstellungstopologien für SQL Server-BI-Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)  
  
 [Leitfaden zum Verwenden von SQL Server BI-Features in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
 [Prüflisten zum Installieren von BI-Features mit SharePoint](../../../2014/sql-server/install/checklists-for-installing-bi-features-with-sharepoint.md)  
  
 [Installation von SharePoint-Modus von Reporting Services &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  
  
 [PowerPivot für SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
##  <a name="bkmk_bi_scenarios"></a> Szenarien für SQL Server BI und SharePoint 2013  
 In diesem Abschnitt sind die unterschiedlichen Ebenen von BI-Funktionen zusammengefasst, die zur Installation und Konfiguration verfügbar sind.  
  
 Excel Services in SharePoint 2013 umfasst Funktionen für Datenmodelle, die die Interaktion mit einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe im Browser ermöglichen. Für grundlegende Data Model-Funktionen nicht müssen Sie zum Bereitstellen der [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013-add-in in der Farm. Es ist lediglich erforderlich, einen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus zu installieren und den Server in Excel Services in den Einstellungen unter **Datenmodell** zu registrieren.  
  
 Bereitstellen der [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013-add-in können Sie zusätzliche Funktionalität und Funktionen in der SharePoint-Farm. Die zusätzlichen Funktionen gehören [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Katalog, planmäßige Datenaktualisierung und das PowerPivot-Management-Dashboard. Weitere Informationen finden Sie in der Tabelle.  
  
||Ebene|Funktionen|Installieren oder konfigurieren|  
|-|-----------|--------------|--------------------------|  
|1|Nur SharePoint|Systemeigene Excel Services-Funktionen|Excel Services und andere in SharePoint Server 2013 enthaltene Dienste.|  
|**2**|SharePoint mit Analysis Services im SharePoint-Modus|Interaktive PowerPivot-Arbeitsmappen im Browser|Installieren Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus.<br /><br /> Registrieren Sie den Analysis Services-Server in Excel Services.|  
|**3**|SharePoint mit Reporting Services im SharePoint-Modus|Power View|Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus.<br /><br /> Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -add-in **(rsSharePoint.msi)** für SharePoint. Weitere Informationen finden Sie unter [installieren oder deinstallieren Sie das Reporting Services-Add-in für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|  
|**4**|Alle PowerPivot-Funktionen|Zugriff auf Arbeitsmappen als Datenquelle von außerhalb der Farm<br /><br /> Planmäßige Datenaktualisierung<br /><br /> PowerPivot-Katalog<br /><br /> Management-Dashboard.<br /><br /> Inhaltstyp der BISM-Linkdatei|Stellen Sie das PowerPivot für SharePoint 2013-Add-In **(spPowerPivot.msi)** bereit. Weitere Informationen finden Sie unter den folgenden Links:<br /><br /> [Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)<br /><br /> Informationen zum Herunterladen von **spPowerPivot.msi**finden Sie unter [Herunterladen von SQL Server 2014 PowerPivot für SharePoint](http://go.microsoft.com/fwlink/?LinkID=296473).|  
  
 Weitere Informationen zum Aktivieren der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Features finden Sie [The SQL Server BI Light-Up-Story für SharePoint 2013](http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) (http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx).  
  
##  <a name="bkmk_install_sharepoint2013_overview"></a> Übersicht über die Installation  
 Wenn Sie beide verwenden möchten [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], SQL Server-Installations-Assistenten zweimal ausführen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sind separate Optionen auf der **Setuprolle** auf der Seite des SQL Server-Setup-Assistenten.  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] unterstützt sowohl SharePoint 2010 und SharePoint 2013; jedoch wird ein anderer Prozess von Architekturen und Installationsvorgänge abhängig von der Version von SharePoint verwendet.  
  
 Im Folgenden sind die Installationsschritte zur Bereitstellung der BI-Funktionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf einem einzelnen Server zusammengefasst.  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013**  
  
 Für **SharePoint 2013**, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] zur Installation auf einen Server, der keine SharePoint-Produkt installiert werden. Die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Architektur für SharePoint 2013 ausgeführt wird **außerhalb** der SharePoint-Farm und kann entweder auf einem Server, die ebenfalls auf eine SharePoint-Installation enthält installiert werden, oder es kann sein installiert einen Server nicht enthält, wird eine SharePoint-Installation.  
  
1.  Installieren Sie SharePoint Server 2013, und aktivieren Sie Excel Services.  
  
2.  Installieren Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus, und gewähren Sie der SharePoint-Farm und den Dienstkonten Serveradministratorberechtigungen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Für beide Versionen von SharePoint die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Installationsprozess wird gestartet, durch Auswahl der setuprolle **SQL Server PowerPivot für SharePoint** in der SQL Server-Installations-Assistenten oder die Verwendung einer SQL Server-Eingabeaufforderung die Installation.  
  
     ![Setuprolle](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Setuprolle")  
  
3.  Sie können für SharePoint 2013 erweitern die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Funktionsumfang. Herunterladen und ausführen **spPowerPivot.msi** um serverseitige datenaktualisierung Verarbeitung, Zusammenarbeit und verwaltungsunterstützung für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Arbeitsmappe. Weitere Informationen finden Sie unter [Microsoft SQL Server 2014 PowerPivot für Microsoft® SharePoint](http://go.microsoft.com/fwlink/?LinkID=324854).  
  
     Führen Sie die [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013-Installationspaket **spPowerPivot.msi** auf jedem Server in der SharePoint-Farm, um sicherzustellen, dass die richtige Version der Daten-Anbieter installiert werden.  
  
4.  So konfigurieren Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint 2013 verwenden **PowerPivot für SharePoint 2013-Konfigurationstool** Tool.  
  
     Die SQL Server-Installations-Assistent installiert zwei [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Konfigurationstools. Eines der Konfigurationstools unterstützt SharePoint 2013 und das andere unterstützt SharePoint 2010.  
  
     ![zwei powerpivot-konfigurationstools](../../../2014/analysis-services/media/as-powerpivot-configtools-bothicons.gif "two powerpivot configuration tools")  
  
5.  Konfigurieren Sie Excel Services in SharePoint Server 2013, um die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz zu verwenden. Weitere Informationen finden Sie im Abschnitt "Konfigurieren einer grundlegenden Analysis Services SharePoint Integration" in [PowerPivot für SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)und [Verwalten von Excel Services-datenmodelleinstellungen (SharePoint Server 2013)](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx).  
  
6.  Weitere Informationen finden Sie unter [PowerPivot für SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010**  
  
 Für SharePoint 2010 ist es erforderlich, dass die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Installation auf einem Server ausgeführt wird, auf dem SharePoint 2010 bereits installiert ist oder installiert werden soll. Die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Architektur für SharePoint 2010 ausgeführt wird **in** der Farm und erfordert SharePoint auf dem Server, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint installiert ist.  
  
1.  Installieren Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus, und gewähren Sie der SharePoint-Farm und den Dienstkonten Serveradministratorberechtigungen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     **spPowerPivot.msi** wird von einer SharePoint 2010-Bereitstellung nicht unterstützt, und die MSI-Datei ist in SharePoint 2010 nicht erforderlich.  
  
     Für beide Versionen von SharePoint die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Installationsprozess wird gestartet, durch Auswahl der setuprolle **SQL Server PowerPivot für SharePoint** in der SQL Server-Installations-Assistenten oder die Verwendung einer SQL Server-Eingabeaufforderung die Installation.  
  
2.  Die SQL Server-Installations-Assistent installiert zwei [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Konfigurationstools. Eines der Konfigurationstools unterstützt SharePoint 2013 und das andere unterstützt SharePoint 2010.  
  
     So konfigurieren Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint 2010 verwendet die **PowerPivot-Konfigurationstool** .  
  
3.  Weitere Informationen finden Sie unter [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  für SharePoint 2010 und 2013  
  
1.  Die Installation für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus von der vorherigen Version unverändert ist.  
  
     Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Installationsschritte für SharePoint 2010 und SharePoint 2013 sind sehr ähnlich. Wichtige Anmerkungen zu SharePoint-Versionen:  
  
    -   Die folgenden Kombinationen werden unterstützt:  
  
        -   Die Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
        -   Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint-Produkte.  
  
        -   Die Version des SharePoint-Produkts.  
  
         [Unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in &#40;SQLServer 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
    -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für SharePoint 2010 erfordert das SharePoint 2010 ServicePack 2 (SP2).  
  
    1.  Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus. [Installation von SharePoint-Modus von Reporting Services &#40;SharePoint 2010 und SharePoint 2013&#41; ](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) und [Installieren des Reporting Services im SharePoint-Modus für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
    2.  Installieren Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint-Produkte (rsSharePoint.msi). Finden Sie unter [installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Für die aktuelle Version der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in für SharePoint, finden Sie unter [, wo Sie das Reporting Services-add-in für SharePoint-Produkte finden](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
    3.  Konfigurieren der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Dienst und mindestens eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -dienstanwendung. Weitere Informationen finden Sie im Abschnitt "Erstellen einer Reporting Services-Dienstanwendung" in [installieren Sie Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
  
##  <a name="bkm_database_attach"></a> Übersicht über die mit Anfügen der Datenbanken Upgrade und SharePoint 2013  
 SharePoint 2013 unterstützt keine direkten Upgrades. Allerdings wird das **Upgrade mit Anfügen der Datenbanken unterstützt**.  
  
 Wenn Sie über eine vorhandene in SharePoint 2010 integrierte PowerPivot-Installation verfügen, können Sie kein direktes Upgrade des SharePoint-Servers ausführen.  Sie können die folgenden Schritte jedoch als Teil eines SharePoint-Upgrades mit Anfügen der Datenbanken ausführen:  
  
1.  Installieren Sie eine neue SharePoint Server 2013-Farm.  
  
2.  Führen Sie ein vollständiges SharePoint-Upgrade mit Anfügen der Datenbanken aus, und migrieren Sie die auf PowerPivot bezogenen Inhaltsdatenbanken zur SharePoint 2013-Farm.  
  
3.  Installieren Sie eine Instanz von SQL Server Analysis Services im SharePoint-Modus, und weisen Sie der SharePoint-Farm und den Dienstkonten, Server über Administratorrechte in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
4.  Installieren Sie das Installationspaket für PowerPivot für SharePoint 2013 **spPowerPivot.msi** auf jedem Server in der SharePoint-Farm.  
  
5.  Konfigurieren Sie Excel Services in der SharePoint 2013-Zentraladministration für die Verwendung des in Schritt 3 erstellten, im SharePoint-Modus ausgeführten Analysis Services-Servers.  
  
     Um Aktualisierungszeitpläne zu migrieren, konfigurieren Sie die PowerPivot-Dienstanwendung.  
  
> [!NOTE]  
>  Weitere Informationen zu PowerPivot und dem SharePoint-Upgrade mit Anfügen der Datenbanken finden Sie unter:  
  
-   [Migrieren von PowerPivot zu SharePoint 2013](../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)  
  
-   [Übersicht über die Verfahren beim Upgrade auf SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Vorbereitende Bereinigung vor einem Upgrade auf SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Aktualisieren von Datenbanken von SharePoint 2010 auf SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in &#40;SQLServer 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)   
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
