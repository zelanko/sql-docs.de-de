---
title: Leitfaden zum Verwenden von SQL Server BI-Funktionen in einer SharePoint 2010-Farm | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f9a94c4-854b-4577-a8b1-7142f19904e3
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 42502473536215297cb047d4e5e563433b66c67b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151293"
---
# <a name="guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm"></a>Leitfaden zum Verwenden von SQL Server BI-Funktionen in einer SharePoint 2010-Farm
  Dieses Thema fasst Funktionsverfügbarkeit auf Grundlage der von Ihnen verwendeten Versionen und Editionen der Software zusammen. Zusätzlich werden Installationsanforderungen für SharePoint 2010 zur Verwendung bestimmter SQL Server-Funktionen erläutert. Informationen im Zusammenhang mit SharePoint 2013 finden Sie unter [Bereitstellungstopologien für SQL Server BI-Funktionen in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
 In diesem Thema:  
  
-   [Allgemeine SharePoint 2010-Anforderungen](#bkmk_generalsharepoint)  
  
-   [SharePoint 2010 Service Pack 1 (SP1)](#bkmk_sp1)  
  
-   [Unterstützung für SharePoint-Editionen und BI-Funktion](#bkmk_vers)  
  
-   [Vorbereitungstool für SharePoint 2010-Produkte](#bkmk_prereq)  
  
-   [Anforderungen und Vorschläge zum Ausführen der SharePoint-Installations](#bkmk_install)  
  
##  <a name="bkmk_generalsharepoint"></a> Allgemeine SharePoint 2010-Anforderungen  
  
-   Es gibt SharePoint 2010-Produkte nur in der 64-Bit-Version. Wenn Sie eine 32-Bit-Installation einer früheren Version von SharePoint haben und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im integrierten SharePoint-Modus installiert ist, können Sie nicht auf SharePoint 2010 aktualisieren. Weitere Informationen finden Sie in der SharePoint-Dokumentation.  
  
-   Reporting Services schließen ein Add-In für SharePoint-Produkte ein. Unterstützte Konfigurationen für das Add-In und den Berichtsserver sind auf einer präziseren Ebene verfügbar als hier angegeben. Weitere Informationen finden Sie unter [unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   SharePoint-Entwicklertools unterstützen nur die eigenständige SharePoint-Konfiguration.  Weitere Informationen finden Sie in der SharePoint-Dokumentation: [Anforderungen für die Entwicklung von SharePoint-Lösungen](http://msdn.microsoft.com/library/ee231582.aspx).  
  
##  <a name="bkmk_vers"></a> Unterstützung für SharePoint-Editionen und BI-Funktion  
 Einige [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Business Intelligence-Funktionen werden nur in bestimmten Editionen von SharePoint-Produkten unterstützt.  
  
|Unterstützte Funktionen|SharePoint-Produkt|  
|------------------------|------------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], ein Feature von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Datenwarnungen.<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]installiert haben.|[!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.|  
|Allgemeine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichtsanzeige und Funktionsintegration in SharePoint.|[!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Standard und Enterprise Editionen.<br /><br /> [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]installiert haben.|  
  
 Weitere Informationen finden Sie unter [von den SQL Server 2012-Editionen unterstützte Funktionen](http://go.microsoft.com/fwlink/?linkid=232473).  
  
##  <a name="bkmk_sp1"></a> SharePoint 2010 Service Pack 1 (SP1)  
 Es wird empfohlen, dass Sie die SharePoint 2010-Installation auf SharePoint 2010 Service Pack 1 (SP1) aktualisieren. SharePoint SP1 ist in den folgenden Fällen erforderlich:  
  
-   Sie wollen die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Version der Datenbank-Engine für die SharePoint-Inhaltsdatenbanken oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Katalogdatenbanken verwenden.  
  
-   Sie wollen [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] und das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstool verwenden.  
  
 Einer der Hauptgründe SP1 ist erforderlich für SharePoint-Installationen mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ist die datenbankmodulfunktion **Sp_dboption**, die in einer früheren Version als veraltet markiert wurde, wird nicht mehr unterstützt, der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Version. Weitere Informationen finden Sie unter [nicht mehr unterstützte Datenbankmodul-Funktionalität in SQL Server 2014](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)  
  
### <a name="sharepoint-2010-sp1-installation-guidance"></a>SharePoint 2010 SP1-Installationsleitfaden  
 [Herunterladen von SharePoint Server 2010 SP1](http://go.microsoft.com/fwlink/?LinkID=219697) und wenden Sie es auf allen Servern in der Farm.  
  
> [!NOTE]  
>  Auf einer vorhandenen Farm müssen Sie mithilfe eines der folgenden **zusätzliche** Schritte zum Abschließen von SharePoint SP1 aktualisieren. Weitere Informationen finden Sie unter [bekannte Probleme bei der Installation von Office 2010 SP1 und SharePoint 2010 SP1](http://support.microsoft.com/kb/2532126) und [Beschreibung von SharePoint Server 2010 SP1](http://support.microsoft.com/kb/2460045):  
  
-   **Konfigurations-Assistenten für SharePoint-Produkte:** führen Sie den Assistenten, um das SP1-Upgrade und Konfiguration abzuschließen.  
  
-   **Abschließen des Upgrades mit Psconfig:** führen Sie den Befehl `psconfig –upgrade` um das SP1-Upgrade abzuschließen  
  
 Weitere Informationen finden Sie im Abschnitt "upgrade" der [(SharePoint Server 2010)](http://technet.microsoft.com/library/cc263093.aspx) und [-Ressourcencenter: Updates für SharePoint 2010-Produkte](http://technet.microsoft.com/sharepoint/ff800847.aspx)  
  
## <a name="sharepoint-installation-with-sql-server-bi-features"></a>SharePoint-Installation mit SQL Server BI-Funktionen  
  
###  <a name="bkmk_prereq"></a> Vorbereitungstool für SharePoint 2010-Produkte  
 Das Vorbereitungstool für SharePoint-Produkte aktiviert Serverrollen im Betriebssystem und installiert andere für eine SharePoint-Installation erforderliche Software. In der folgenden Tabelle werden zusätzliche Schritte identifiziert, um den Server für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zu konfigurieren.  
  
|Komponente|Aktion|  
|---------------|------------|  
|Reporting Services-Add-In|Das Vorbereitungstool für SharePoint 2010-Produkte installiert die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Version des Reporting Services-Add-Ins. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] umfasst eine neuere Version des Add-Ins, das für Funktionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erforderlich ist. Das Add-In kann sowohl mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installations-Assistenten installiert als auch von MSDN heruntergeladen werden. Weitere Informationen, wo Sie die aktuelle Version des Add-Ins zu erhalten und wie Sie sie installieren, finden Sie unter [, wo Sie das Reporting Services-Add-in für SharePoint-Produkte finden](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md) und [installieren oder Deinstallieren von Reporting Services Add-in für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).|  
|Analysis Services OLE DB-Anbieter (MSOLAP)|SharePoint 2010 installiert die SQL Server 2008-Version des OLE DB-Anbieters als Teil einer Excel Services-Bereitstellung. Diese Version unterstützt keinen [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Datenzugriff. Auf SharePoint-Servern, die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Datenverbindungen unterstützen, sollten Sie neuere Versionen des Anbieters installieren. Weitere Informationen finden Sie unter [installieren Sie die Analysis Services-OLE DB-Anbieter auf SharePoint-Servern](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)|  
|ADO.NET Services|SharePoint 2010 listet ADO.NET Services in der Liste der erforderlichen Komponenten auf, sie werden jedoch nicht vom Installationsprogramm für die erforderlichen Komponenten installiert. Um ADO.NET Services hinzuzufügen, müssen diese manuell installiert werden. Die Installation von ADO.NET Services ist erforderlich, wenn Sie SharePoint-Listen als Datenfeeds für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Arbeitsmappen oder Reporting Services-Berichte verwenden möchten. Anweisungen hierzu finden Sie unter [ADO.NET Data Services installieren, um Daten zu unterstützen datenfeedexporte von SharePoint-Listen](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).|  
  
###  <a name="bkmk_install"></a> Anforderungen und Vorschläge zum Ausführen der SharePoint-Installations  
 Welche [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Funktionen Sie installieren und die Installationsreihenfolge bestimmen, welche Integrationsebenen mit SharePoint möglich sind. Während ein bestimmter Grad an Funktionsintegration durch Reporting Services auf einem SharePoint-Server, der eine integrierte Datenbank verwendet, möglich ist, erfordern die meisten Funktionsintegrationsszenarien eine Farminstallation von SharePoint, da nur eine Farminstallation die erforderliche Infrastruktur für einige BI-Funktionen bereitstellt.  
  
 Eine SharePoint-Farm kann aus einzelnen oder mehreren Servern bestehen. Was eine Farm von einer eigenständigen Installation unterscheidet, ist das Vorhandensein einer zusätzlichen Infrastruktur, wie z. B. der Claims to Windows Token Service.  
  
 Eine Farm wird aktiviert, bei der Auswahl der **Serverfarm** Option im SharePoint-Setup. Sie benötigen eine Farminstallation, wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint oder [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] verwenden möchten. Die eigenständige SharePoint-Installation wird im Allgemeinen für Entwicklungsumgebungen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt. Eine SharePoint-Farminstallation wird jedoch für eine Produktionsumgebung empfohlen.  
  
 ![GMNI_SetupUI_SharePoint2010InstallType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010installtype.gif "GMNI_SetupUI_SharePoint2010InstallType")  
  
 Eine vollständige Serverinstallation ist auch für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint oder den gemeinsamen Dienst von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erforderlich.  
  
 ![GMNI_SetupUI_SharePoint2010ServerType](../../../2014/sql-server/install/media/gmni-setupui-sharepoint2010servertype.gif "GMNI_SetupUI_SharePoint2010ServerType")  
  
 Die letzte Seite des Setup-Assistenten fordert Sie zur Konfiguration einer Farm auf und konfiguriert optional eine Standardwebanwendung und Stammwebsitesammlung. Die meisten Setupbenutzer folgen diesem Installationspfad. Wenn Sie die Farm aus irgendeinem Grund nicht konfigurieren, können Sie die Farmkonfigurationsoption im [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstool verwenden, um die Farm zu konfigurieren.  
  
 In vorherigen Versionen wurde empfohlen, die Farm bei der Installation von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nicht zu konfigurieren, da es Ihnen später Arbeitsschritte erspart hat, wenn Sie SQL Server-Installationsoptionen zur Installation von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint in einem einsatzbereiten Zustand verwendeten. In dieser Version ist es nicht mehr wichtig. Sie können mithilfe des [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstools eine vorhandene Farm optimieren, damit sie die für eine [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Installation empfohlenen Einstellungen verwendet.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] kann in eine vorhandene SharePoint-Farm installiert werden. Sie können [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder SharePoint in jeder Reihenfolge installieren, aber die Konfiguration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] hängt von der Reihenfolge ab. Weitere Informationen finden Sie unter [Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm &#40;Horizontales Skalieren für SSRS&#41; ](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) und [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 ![GMNI_SetupUI_DoNotConfigureMOSS](../../../2014/sql-server/install/media/gmni-setupui-donotconfiguremoss.gif "GMNI_SetupUI_DoNotConfigureMOSS")  
  
## <a name="see-also"></a>Siehe auch  
 [Installation und Bereitstellung von SharePoint Server 2010](http://technet.microsoft.com/sharepoint/ee518643.aspx)   
 [Mehrere Server für eine dreistufige Farm (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?linkID=219834)  
  
  