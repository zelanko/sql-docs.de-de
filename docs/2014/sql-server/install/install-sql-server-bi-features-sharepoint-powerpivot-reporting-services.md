---
title: Installieren von SQL Server-BI-Funktionen mit SharePoint (PowerPivot und Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 436d90b75a5995ac8f455a52ebfffe662b1f9b7f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094463"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>Installieren der BI-Funktionen von SQL Server mit SharePoint (PowerPivot und Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] können in eine Microsoft SharePoint-Farm integriert werden, um Business Intelligence (BI)-Funktionen in SharePoint bereitzustellen. Die Funktionen umfassen [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] Dient zum [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Datenzugriff in einer SharePoint-Farm. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ist die Daten-Engine für Arbeitsmappen, die in [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel erstellt werden und auf die über eine SharePoint-Bibliothek zugegriffen wird. Nachdem Sie eine [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe in SharePoint gespeichert haben, können Sie sie als Datenquelle für [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichte verwenden.  
  
 Einige der Installations- und Konfigurationsschritte, die für SharePoint 2010 erforderlich sind, unterscheiden sich von den Schritten, die für SharePoint 2013 erforderlich sind. Einige der Themen in diesem Abschnitt gelten für beide Versionen von SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 ![Beachten Sie](../../../2014/reporting-services/media/rs-fyinote.png "Hinweis") die aktuellen versionsanmerkungen finden Sie unter [Versionsanmerkungen für SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
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
  
 Excel Services in SharePoint 2013 umfasst Funktionen für Datenmodelle, die die Interaktion mit einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe im Browser ermöglichen. Um grundlegende Datenmodellfunktionen zu ermöglichen, müssen Sie das [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013-Add-In nicht in der Farm bereitstellen. Es ist lediglich erforderlich, einen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus zu installieren und den Server in Excel Services in den Einstellungen unter **Datenmodell** zu registrieren.  
  
 Die Bereitstellung des [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013-Add-Ins macht einen zusätzlichen Funktionsumfang in der SharePoint-Farm verfügbar. Zu diesen Funktionen gehören der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Katalog, die planmäßige Datenaktualisierung und das PowerPivot-Management-Dashboard. Weitere Informationen finden Sie in der Tabelle.  
  
||Ebene|Features|Installieren oder konfigurieren|  
|-|-----------|--------------|--------------------------|  
|1|Nur SharePoint|Systemeigene Excel Services-Funktionen|Excel Services und andere in SharePoint Server 2013 enthaltene Dienste.|  
|**2**|SharePoint mit Analysis Services im SharePoint-Modus|Interaktive PowerPivot-Arbeitsmappen im Browser|Installieren Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus.<br /><br /> Registrieren Sie den Analysis Services-Server in Excel Services.|  
|**3**|SharePoint mit Reporting Services im SharePoint-Modus|Power View|Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus.<br /><br /> Installieren Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In **(rsSharePoint.msi)** für SharePoint. Weitere Informationen finden Sie unter [installieren oder deinstallieren Sie das Reporting Services-Add-in für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|  
|**4**|Alle PowerPivot-Funktionen|Zugriff auf Arbeitsmappen als Datenquelle von außerhalb der Farm<br /><br /> Planmäßige Datenaktualisierung<br /><br /> PowerPivot-Katalog<br /><br /> Management-Dashboard.<br /><br /> Inhaltstyp der BISM-Linkdatei|Stellen Sie das PowerPivot für SharePoint 2013-Add-In **(spPowerPivot.msi)** bereit. Weitere Informationen finden Sie unter den folgenden Links:<br /><br /> [Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)<br /><br /> Informationen zum Herunterladen von **spPowerPivot.msi**finden Sie unter [Herunterladen von SQL Server 2014 PowerPivot für SharePoint](https://go.microsoft.com/fwlink/?LinkID=296473).|  
  
 Weitere Informationen zum Aktivieren der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Features finden Sie [The SQL Server BI Light-Up-Story für SharePoint 2013](https://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) (https://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx).  
  
##  <a name="bkmk_install_sharepoint2013_overview"></a> Übersicht über die Installation  
 Wenn Sie sowohl [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] als auch [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]verwenden möchten, führen Sie den SQL Server-Installations-Assistenten zweimal aus. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sind separate Optionen auf der **Setuprolle** auf der Seite des SQL Server-Setup-Assistenten.  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] unterstützt sowohl SharePoint 2010 als auch SharePoint 2013, allerdings werden abhängig von der SharePoint-Version unterschiedliche Architekturen und Installationsvorgänge verwendet.  
  
 Im Folgenden sind die Installationsschritte zur Bereitstellung der BI-Funktionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf einem einzelnen Server zusammengefasst.  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013**  
  
 Für **SharePoint 2013**kann die [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Installation auf einem Server ausgeführt werden, auf dem kein SharePoint-Produkt installiert ist. Die für SharePoint 2013 verwendete [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Architektur wird **außerhalb** der SharePoint-Farm ausgeführt und kann entweder auf einem Server installiert werden, der auch eine SharePoint-Installation enthält, oder auf einem Server, der KEINE SharePoint-Installation enthält.  
  
1.  Installieren Sie SharePoint Server 2013, und aktivieren Sie Excel Services.  
  
2.  Installieren Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus, und gewähren Sie der SharePoint-Farm und den Dienstkonten Serveradministratorberechtigungen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Bei beiden SharePoint-Versionen wird der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Installationsvorgang gestartet, indem im Installations-Assistenten für SQL Server die Setuprolle **SQL Server PowerPivot für SharePoint** ausgewählt oder eine Installation über die SQL Server-Eingabeaufforderung ausgeführt wird.  
  
     ![Setuprolle](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Setuprolle")  
  
3.  Für SharePoint 2013 können Sie den [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Funktionsumfang erweitern. Laden Sie die Installationsdatei **spPowerPivot.msi** herunter, und führen Sie sie aus, um die serverseitige Datenaktualisierung, Zusammenarbeit und Verwaltungsunterstützung für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen hinzuzufügen. Weitere Informationen finden Sie unter [Microsoft SQL Server 2014 PowerPivot für Microsoft® SharePoint](https://go.microsoft.com/fwlink/?LinkID=324854).  
  
     Führen Sie das [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013-Installationspaket **spPowerPivot.msi** auf jedem Server in der SharePoint-Farm aus, um sicherzustellen, dass die richtige Version der Datenanbieter installiert wird.  
  
4.  Zum Konfigurieren von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint 2013 verwenden Sie das Tool **Konfiguration von PowerPivot für SharePoint 2013** .  
  
     Der Installations-Assistent für SQL Server installiert zwei [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Konfigurationstools. Eines der Konfigurationstools unterstützt SharePoint 2013 und das andere unterstützt SharePoint 2010.  
  
     ![zwei powerpivot-konfigurationstools](../../../2014/analysis-services/media/as-powerpivot-configtools-bothicons.gif "two powerpivot configuration tools")  
  
5.  Konfigurieren Sie Excel Services in SharePoint Server 2013, um die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz zu verwenden. Weitere Informationen finden Sie im Abschnitt "Konfigurieren einer grundlegenden Analysis Services SharePoint Integration" in [PowerPivot für SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)und [Verwalten von Excel Services-datenmodelleinstellungen (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx) (https://technet.microsoft.com/library/jj219780.aspx).  
  
6.  Weitere Informationen finden Sie unter [PowerPivot for SharePoint 2013 Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010**  
  
 Für SharePoint 2010 ist es erforderlich, dass die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Installation auf einem Server ausgeführt wird, auf dem SharePoint 2010 bereits installiert ist oder installiert werden soll. Die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Architektur für SharePoint 2010 wird **innerhalb** der Farm ausgeführt und erfordert, dass auf dem Server, auf dem [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint installiert wird, SharePoint installiert ist.  
  
1.  Installieren Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus, und gewähren Sie der SharePoint-Farm und den Dienstkonten Serveradministratorberechtigungen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     **spPowerPivot.msi** wird von einer SharePoint 2010-Bereitstellung nicht unterstützt, und die MSI-Datei ist in SharePoint 2010 nicht erforderlich.  
  
     Bei beiden SharePoint-Versionen wird der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Installationsvorgang gestartet, indem im Installations-Assistenten für SQL Server die Setuprolle **SQL Server PowerPivot für SharePoint** ausgewählt oder eine Installation über die SQL Server-Eingabeaufforderung ausgeführt wird.  
  
2.  Der Installations-Assistent für SQL Server installiert zwei [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Konfigurationstools. Eines der Konfigurationstools unterstützt SharePoint 2013 und das andere unterstützt SharePoint 2010.  
  
     Verwenden Sie zum Konfigurieren von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint 2010 das **PowerPivot-Konfigurationstool** .  
  
3.  Weitere Informationen finden Sie unter [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  für SharePoint 2010 und 2013  
  
1.  Die Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus ist seit der vorherigen Version unverändert.  
  
     Die Installationsschritte von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für SharePoint 2010 und SharePoint 2013 sind sehr ähnlich. Wichtige Anmerkungen zu SharePoint-Versionen:  
  
    -   Die folgenden Kombinationen werden unterstützt:  
  
        -   Die Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
        -   Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte.  
  
        -   Die Version des SharePoint-Produkts.  
  
         [Unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in &#40;SQLServer 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
    -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für SharePoint 2010 erfordert das SharePoint 2010 ServicePack 2 (SP2).  
  
    1.  Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus. [Installation von SharePoint-Modus von Reporting Services &#40;SharePoint 2010 und SharePoint 2013&#41; ](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) und [Installieren des Reporting Services im SharePoint-Modus für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
    2.  Installieren Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte (rsSharePoint.msi). Finden Sie unter [installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Für die aktuelle Version der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in für SharePoint, finden Sie unter [, wo Sie das Reporting Services-add-in für SharePoint-Produkte finden](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
    3.  Konfigurieren Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Dienst und mindestens eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung. Weitere Informationen finden Sie im Abschnitt "Erstellen einer Reporting Services-Dienstanwendung" in [installieren Sie Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
  
##  <a name="bkm_database_attach"></a> Übersicht über die mit Anfügen der Datenbanken Upgrade und SharePoint 2013  
 SharePoint 2013 unterstützt keine direkten Upgrades. Allerdings wird das **Upgrade mit Anfügen der Datenbanken unterstützt**.  
  
 Wenn Sie über eine vorhandene in SharePoint 2010 integrierte PowerPivot-Installation verfügen, können Sie kein direktes Upgrade des SharePoint-Servers ausführen.  Sie können die folgenden Schritte jedoch als Teil eines SharePoint-Upgrades mit Anfügen der Datenbanken ausführen:  
  
1.  Installieren Sie eine neue SharePoint Server 2013-Farm.  
  
2.  Führen Sie ein vollständiges SharePoint-Upgrade mit Anfügen der Datenbanken aus, und migrieren Sie die auf PowerPivot bezogenen Inhaltsdatenbanken zur SharePoint 2013-Farm.  
  
3.  Installieren Sie eine SQL Server Analysis Services-Instanz im SharePoint-Modus, und gewähren Sie der SharePoint-Farm und den Dienstkonten Serveradministratorrechte in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
4.  Installieren Sie das Installationspaket für PowerPivot für SharePoint 2013 **spPowerPivot.msi** auf jedem Server in der SharePoint-Farm.  
  
5.  Konfigurieren Sie Excel Services in der SharePoint 2013-Zentraladministration für die Verwendung des in Schritt 3 erstellten, im SharePoint-Modus ausgeführten Analysis Services-Servers.  
  
     Um Aktualisierungszeitpläne zu migrieren, konfigurieren Sie die PowerPivot-Dienstanwendung.  
  
> [!NOTE]  
>  Weitere Informationen zu PowerPivot und dem SharePoint-Upgrade mit Anfügen der Datenbanken finden Sie unter:  
  
-   [Migrieren von PowerPivot zu SharePoint 2013](../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)  
  
-   [Übersicht über die Verfahren beim Upgrade auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Vorbereitende Bereinigung vor einem Upgrade auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Aktualisieren von Datenbanken von SharePoint 2010 auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in &#40;SQLServer 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)   
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
