---
title: Leitfaden für die Verwendung von SQL Server BI-Funktionen in einer SharePoint 2010-Farm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 5f9a94c4-854b-4577-a8b1-7142f19904e3
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 08323d12fb787ea3989555070632d9716ad41152
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952260"
---
# <a name="guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm"></a>Leitfaden zum Verwenden von SQL Server BI-Funktionen in einer SharePoint 2010-Farm
  Dieses Thema fasst Funktionsverfügbarkeit auf Grundlage der von Ihnen verwendeten Versionen und Editionen der Software zusammen. Zusätzlich werden Installationsanforderungen für SharePoint 2010 zur Verwendung bestimmter SQL Server-Funktionen erläutert. Weitere Informationen zu SharePoint 2013 finden Sie unter [Deployment Topologien for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
 In diesem Thema:  
  
-   [Allgemeine SharePoint 2010-Anforderungen](#bkmk_generalsharepoint)  
  
-   [SharePoint 2010 Service Pack 1 (SP1)](#bkmk_sp1)  
  
-   [Unterstützung von SharePoint-Editionen und BI-Funktionen](#bkmk_vers)  
  
-   [Vorbereitungs Tool für SharePoint 2010-Produkte](#bkmk_prereq)  
  
-   [Anforderungen und Vorschläge für die Ausführung der SharePoint-Installation](#bkmk_install)  
  
##  <a name="bkmk_generalsharepoint"></a>Allgemeine SharePoint 2010-Anforderungen  
  
-   Es gibt SharePoint 2010-Produkte nur in der 64-Bit-Version. Wenn Sie eine 32-Bit-Installation einer früheren Version von SharePoint haben und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im integrierten SharePoint-Modus installiert ist, können Sie nicht auf SharePoint 2010 aktualisieren. Weitere Informationen finden Sie in der SharePoint-Dokumentation.  
  
-   Reporting Services schließen ein Add-In für SharePoint-Produkte ein. Unterstützte Konfigurationen für das Add-In und den Berichtsserver sind auf einer präziseren Ebene verfügbar als hier angegeben. Weitere Informationen finden [Sie unter Unterstützte Kombinationen von SharePoint und Reporting Services Server und Add &#40;-in&#41;SQL Server 2014](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   SharePoint-Entwicklertools unterstützen nur die eigenständige SharePoint-Konfiguration.  Weitere Informationen finden Sie in der SharePoint-Dokumentation: [Anforderungen für die Entwicklung von SharePoint-Lösungen](https://msdn.microsoft.com/library/ee231582.aspx).  
  
##  <a name="bkmk_vers"></a>Unterstützung von SharePoint-Editionen und BI-Funktionen  
 Einige [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Business Intelligence-Funktionen werden nur in bestimmten Editionen von SharePoint-Produkten unterstützt.  
  
|Unterstützte Funktionen|SharePoint-Produkt|  
|------------------------|------------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], eine Funktion des [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] @ no__t-2-Add-Ins für [!INCLUDE[msCoName](../../includes/msconame-md.md)] @ no__t-4 Enterprise Edition.<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Datenwarnungen.<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. installiert haben.|[!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.|  
|Allgemeine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichtsanzeige und Funktionsintegration in SharePoint.|[!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Standard und Enterprise Editionen.<br /><br /> [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]. installiert haben.|  
  
 Weitere Informationen finden Sie [unter von den Editionen von SQL Server 2012 unterstützte Funktionen](https://go.microsoft.com/fwlink/?linkid=232473).  
  
##  <a name="bkmk_sp1"></a>SharePoint 2010 Service Pack 1 (SP1)  
 Es wird empfohlen, dass Sie die SharePoint 2010-Installation auf SharePoint 2010 Service Pack 1 (SP1) aktualisieren. SharePoint SP1 ist in den folgenden Fällen erforderlich:  
  
-   Sie wollen die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Version der Datenbank-Engine für die SharePoint-Inhaltsdatenbanken oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Katalogdatenbanken verwenden.  
  
-   Sie wollen [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] und das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstool verwenden.  
  
 Einer der Hauptgründe für die Verwendung von SP1 für SharePoint-Installationen, die mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ausgeführt werden, ist die Datenbank-Engine-Funktion **sp_dboption**, die in einer früheren Version veraltet war, in der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Version nicht mehr unterstützt wird. Weitere Informationen finden Sie unter nicht mehr unterstützte [Datenbank-Engine Funktionen in SQL Server 2014](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)  
  
### <a name="sharepoint-2010-sp1-installation-guidance"></a>SharePoint 2010 SP1-Installationsleitfaden  
 [Laden Sie SharePoint Server 2010 SP1 herunter](https://go.microsoft.com/fwlink/?LinkID=219697) , und wenden Sie es auf alle Server in der Farm an.  
  
> [!NOTE]  
>  In einer vorhandenen Farm müssen Sie einen der folgenden **zusätzlichen** Schritte ausführen, um das SharePoint SP1-Upgrade abzuschließen. Weitere Informationen finden Sie unter [bekannte Probleme bei der Installation von Office 2010 SP1 und SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126) und [Beschreibung von SharePoint Server 2010 SP1](https://support.microsoft.com/kb/2460045):  
  
-   **Konfigurations-Assistent für SharePoint-Produkte:** Führen Sie den Assistenten aus, um das SP1-Upgrade und die Konfiguration abzuschließen.  
  
-   **Vervollständigen Sie das Upgrade mit Psconfig:** Führen Sie den Befehl `psconfig -upgrade` aus, um das SP1-Upgrade abzuschließen.  
  
 Weitere Informationen finden Sie im Abschnitt "Upgrade" von [(SharePoint Server 2010)](https://technet.microsoft.com/library/cc263093.aspx) und [resource Center: Updates für SharePoint 2010-Produkte @ no__t-0  
  
## <a name="sharepoint-installation-with-sql-server-bi-features"></a>SharePoint-Installation mit SQL Server BI-Funktionen  
  
###  <a name="bkmk_prereq"></a>Vorbereitungs Tool für SharePoint 2010-Produkte  
 Das Vorbereitungstool für SharePoint-Produkte aktiviert Serverrollen im Betriebssystem und installiert andere für eine SharePoint-Installation erforderliche Software. In der folgenden Tabelle werden zusätzliche Schritte identifiziert, um den Server für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zu konfigurieren.  
  
|Komponente|Aktion|  
|---------------|------------|  
|Reporting Services-Add-In|Das Vorbereitungstool für SharePoint 2010-Produkte installiert die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version des Reporting Services-Add-Ins. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] umfasst eine neuere Version des Add-Ins, das für Funktionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erforderlich ist. Das Add-In kann sowohl mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installations-Assistenten installiert als auch von MSDN heruntergeladen werden. Weitere Informationen zum Abrufen der aktuellen Version des Add-Ins und zur Installation finden Sie unter [wo finden Sie das Reporting Services-Add-in für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md) und [installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40; . SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).|  
|Analysis Services OLE DB-Anbieter (MSOLAP)|SharePoint 2010 installiert die SQL Server 2008-Version des OLE DB-Anbieters als Teil einer Excel Services-Bereitstellung. Diese Version unterstützt keinen [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Datenzugriff. Auf SharePoint-Servern, die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Datenverbindungen unterstützen, sollten Sie neuere Versionen des Anbieters installieren. Weitere Informationen finden Sie unter [install the Analysis Services OLE DB-Anbieter on SharePoint Servers](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)|  
|ADO.NET Services|SharePoint 2010 listet ADO.NET Services in der Liste der erforderlichen Komponenten auf, sie werden jedoch nicht vom Installationsprogramm für die erforderlichen Komponenten installiert. Um ADO.NET Services hinzuzufügen, müssen diese manuell installiert werden. Die Installation von ADO.NET Services ist erforderlich, wenn Sie SharePoint-Listen als Datenfeeds für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Arbeitsmappen oder Reporting Services-Berichte verwenden möchten. Anweisungen finden [Sie unter Install ADO.NET Data Services, um Datenfeed-Exporte von SharePoint-Listen zu unterstützen](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).|  
  
###  <a name="bkmk_install"></a>Anforderungen und Vorschläge für die Ausführung der SharePoint-Installation  
 Welche [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Funktionen Sie installieren und die Installationsreihenfolge bestimmen, welche Integrationsebenen mit SharePoint möglich sind. Während ein bestimmter Grad an Funktionsintegration durch Reporting Services auf einem SharePoint-Server, der eine integrierte Datenbank verwendet, möglich ist, erfordern die meisten Funktionsintegrationsszenarien eine Farminstallation von SharePoint, da nur eine Farminstallation die erforderliche Infrastruktur für einige BI-Funktionen bereitstellt.  
  
 Eine SharePoint-Farm kann aus einzelnen oder mehreren Servern bestehen. Was eine Farm von einer eigenständigen Installation unterscheidet, ist das Vorhandensein einer zusätzlichen Infrastruktur, wie z. B. der Claims to Windows Token Service.  
  
 Eine Farm wird aktiviert, wenn Sie die Option **Server Farm** in SharePoint-Setup auswählen. Sie benötigen eine Farminstallation, wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint oder [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] verwenden möchten. Die eigenständige SharePoint-Installation wird im Allgemeinen für Entwicklungsumgebungen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt. Eine SharePoint-Farminstallation wird jedoch für eine Produktionsumgebung empfohlen.  
  
 ![GMNI_SetupUI_SharePoint2010InstallType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010installtype.gif "GMNI_SetupUI_SharePoint2010InstallType")  
  
 Eine vollständige Serverinstallation ist auch für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint oder den gemeinsamen Dienst von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erforderlich.  
  
 ![GMNI_SetupUI_SharePoint2010ServerType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010servertype.gif "GMNI_SetupUI_SharePoint2010ServerType")  
  
 Die letzte Seite des Setup-Assistenten fordert Sie zur Konfiguration einer Farm auf und konfiguriert optional eine Standardwebanwendung und Stammwebsitesammlung. Die meisten Setupbenutzer folgen diesem Installationspfad. Wenn Sie die Farm aus irgendeinem Grund nicht konfigurieren, können Sie die Farmkonfigurationsoption im [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstool verwenden, um die Farm zu konfigurieren.  
  
 In vorherigen Versionen wurde empfohlen, die Farm bei der Installation von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nicht zu konfigurieren, da es Ihnen später Arbeitsschritte erspart hat, wenn Sie SQL Server-Installationsoptionen zur Installation von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint in einem einsatzbereiten Zustand verwendeten. In dieser Version ist es nicht mehr wichtig. Sie können mithilfe des [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstools eine vorhandene Farm optimieren, damit sie die für eine [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Installation empfohlenen Einstellungen verwendet.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] kann in eine vorhandene SharePoint-Farm installiert werden. Sie können [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder SharePoint in jeder Reihenfolge installieren, aber die Konfiguration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] hängt von der Reihenfolge ab. Weitere Informationen finden Sie unter [Hinzufügen eines zusätzlichen Berichts Servers zu einer &#40;Farm SSRS Scale-&#41; out](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) und [Installation Reporting Services SharePoint-Modus für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 ![GMNI_SetupUI_DoNotConfigureMOSS](../../../2014/sql-server/install/media/gmni-setupui-donotconfiguremoss.gif "GMNI_SetupUI_DoNotConfigureMOSS")  
  
## <a name="see-also"></a>Siehe auch  
 [Installation und Bereitstellung für SharePoint Server 2010](https://technet.microsoft.com/sharepoint/ee518643.aspx)   
 [Mehrere Server für eine dreistufige Farm (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834)  
  
  
