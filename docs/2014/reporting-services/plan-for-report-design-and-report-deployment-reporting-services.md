---
title: Planen des Berichtsentwurfs und der Berichts Bereitstellung (Reporting Services 2014) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1c1e265e-52a2-4de3-96fd-ca4abae01c02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6104bfc97d2f66652ffa9b16e9ff0ae8f9b0550
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108052"
---
# <a name="plan-for-report-design-and-report-deployment-reporting-services-2014"></a>Planen von Berichtsentwurf und -bereitstellung (Reporting Services 2014)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] bietet verschiedene Vorgehensweisen zum Erstellen und Bereitstellen von Berichten. Dieses Thema soll Sie bei der Planung für eine Berichterstellungsumgebung und einen Berichtsserver unterstützen, die reibungslos zusammenarbeiten. Dieses Thema bietet eine Übersicht über die Unterstützung der Berichtsdefinition durch [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Komponenten. Eine Berichtsdefinition ist eine XML-Datei, die in der Berichtsdefinitionssprache (Report Definition Language, RDL) oder in der Berichtsdefinitionssprache für Clients (Report Definition Language for Clients, RDLC) geschrieben ist. Jede Berichtsdefinition entspricht einer bestimmten Schemaversion, die am Anfang der Datei aufgelistet ist.  
  
 RDL-Dateien werden im Berichts-Designer in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] -Projekten erstellt, sowie im Berichts-Generator 3.0. RDLC-Dateien werden mit den ReportViewer-Steuerelementen erstellt, die in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]enthalten sind.  
  
 Inhalte dieses Themas:  
  
-   [RDL-Schema Versionen](#bkmk_rdl_schema_versions)  
  
-   [Unterstützung von Berichts Servern und RDL-Schemas](#bkmk_report_server_rdl_schema_support)  
  
-   [Berichterstellung und Bereitstellungs Unterstützung](#bkmk_report_authoring_and_deployment)  
  
-   [Report Viewer-Steuerelemente](#bkmk_reportviewer)  
  
##  <a name="bkmk_rdl_schema_versions"></a>RDL-Schema Versionen  
 In der folgenden Tabelle sind alle verfügbaren Schemaversionen und die in diesem Thema verwendeten Abkürzungen der Schemaversionen aufgeführt:  
  
|Abkürzung|Schemaversion|  
|------------------|--------------------|  
|2010 RDL|https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition|  
|2008 RDL|https://schemas.microsoft.com/sqlserver/reporting/2008/01/reportdefinition|  
|2005 RDL<br /><br /> 2005 RDLC|https://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition|  
|2000 RDL|https://schemas.microsoft.com/sqlserver/reporting/2003/10/reportdefinition|  
  
 Weitere Informationen zu RDL und RDL-Schemas finden Sie in den folgenden Themen:  
  
-   [Microsoft SQL Server von XML-Schemas](https://go.microsoft.com/fwlink/?LinkId=31850)  
  
-   [Spezifikationen der Berichts Definitions Sprache](https://go.microsoft.com/fwlink/?linkid=116865)  
  
-   [Berichtsdefinitionssprache (SSRS)](reports/report-definition-language-ssrs.md)  
  
 Weitere Informationen zu ReportViewer-Steuerelementen finden Sie unter [ReportViewer-Steuerelemente (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx).  
  
##  <a name="bkmk_report_server_rdl_schema_support"></a>Unterstützung von Berichts Servern und RDL-Schemas  
 Eine Berichtsdefinitionsdatei kann wie folgt auf einem [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] -Berichtsserver bereitgestellt werden:  
  
-   **Berichts-Designer:** Stellen Sie einen Bericht aus Berichts-Designer [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)]in bereit.  
  
-   **Berichts-Generator:** Speichern Sie einen Bericht aus Berichts-Generator auf dem Berichts Server.  
  
-   **Berichts-Manager:** Laden Sie einen Bericht aus Berichts-Manager in einen Berichts Server im einheitlichen Modus hoch.  
  
-   **SharePoint:** Laden Sie einen Bericht auf eine SharePoint-Website hoch, die mit einem Berichts Server im SharePoint-Modus konfiguriert ist.  
  
-   **Programm gesteuert:** Programm gesteuertes Veröffentlichen eines Berichts mithilfe der SOAP-API-Schnittstellen auf einem Berichts Server. Weitere Informationen finden Sie unter [Report Server Web Service](report-server-web-service/report-server-web-service.md).  
  
 In der folgenden Tabelle werden die unterstützten RDL-Schemaversionen nach Versionen des Berichtsservers aufgelistet.  
  
|Berichtsserverversion|RDL-Schemaversion|  
|---------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> oder<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> oder<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|2010 RDL<br /><br /> 2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]|2005 RDL<br /><br /> 2000 RDL|  
  
 Wenn Sie eine Berichtsdefinition auf den Berichtsserver hochladen oder ein Upgrade eines Berichtsservers ausführen, auf dem Berichte vorhanden sind, wird auf dem Berichtsserver die Berichtsdefinition im ursprünglichen Format beibehalten. **Bei der ersten Verwendung**aktualisiert der Berichts Server den Bericht in der Berichts Server-Datenbank auf ein binäres Format, das für nachfolgende Sichten beibehalten wird. Die Berichtsdefinition (.rdl) selbst wird nicht aktualisiert.  
  
 Sie können vom Berichtsserver eine schreibgeschützte Kopie der Berichtsdefinitionsdatei (.rdl) extrahieren. Navigieren Sie auf einem Berichtsserver im einheitlichen Modus zum Berichts-Manager, wählen Sie den Bericht aus, und klicken auf **Herunterladen**. Wechseln Sie in einer Bereitstellung im SharePoint-Modus zur Dokumentbibliothek, wählen Sie den Bericht aus, und klicken Sie auf **Kopie herunterladen**.  
  
 Um die Berichtsdefinition zu aktualisieren, müssen Sie den Bericht in einer Berichterstellungsumgebung öffnen und speichern.  
  
 Weitere Informationen über Berichtsupgrades und die unterstützten Schemaversionen finden Sie unter [Aktualisieren von Berichten](install-windows/upgrade-reports.md).  
  
##  <a name="bkmk_report_authoring_and_deployment"></a>Berichterstellung und Bereitstellungs Unterstützung  
 Berichterstellungsumgebungen sind der Berichts-Designer in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] -Projekten sowie der Berichts-Generator. Berichterstellungsumgebungen bieten viele Arten der Unterstützung für Berichtsupgrades, den Berichtsentwurf, die Berichtsvorschau im lokalen Modus, die Berichtsvorschau auf dem Berichtsserver sowie die Berichtsbereitstellung.  
  
 In der folgenden Tabelle wird die Unterstützung für das Erstellen und Bereitstellen von Berichtsdefinitionen für unterschiedliche Schemaversionen zusammengefasst:  
  
|Berichterstellungsumgebung|Erstellte RDL-Version|Bereitstellen der RDL-Version|Bereitstellen für Berichtsserverversionen|  
|---------------------------|--------------------------|------------------------|--------------------------------------|  
|Berichts-Designer in SQL Server 2014 Data Tools – Business Intelligence für Microsoft Visual Studio 2012 im Microsoft Download Center.<br /><br /> oder<br /><br /> Berichts-Designer in SQL Server 2012 Data Tools – Business Intelligence für Microsoft Visual Studio 2012 im Microsoft Download Center.<br /><br /> oder<br /><br /> Berichts-Designer in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Data Tools, enthalten in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].|Autoren 2010 RDL. Beim Öffnen von vorhandenem RDL:<br /><br /> 2000 RDL, aktualisiert auf 2010 RDL<br /><br /> 2005 RDL, aktualisiert auf 2010 RDL<br /><br /> 2008 RDL, aktualisiert auf 2010 RDL|2008 RDL<br /><br /> 2010 RDL|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|Berichts-Designer in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Business Intelligence Development Studio|Autoren 2010 RDL. Beim Öffnen von vorhandenem RDL:<br /><br /> 2000 RDL, aktualisiert auf 2010 RDL<br /><br /> 2005 RDL, aktualisiert auf 2010 RDL<br /><br /> 2008 RDL, aktualisiert auf 2010 RDL|2008 RDL<br /><br /> 2010 RDL|[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|Berichts-Designer in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Business Intelligence Development Studio|Autoren 2008 RDL. Beim Öffnen von vorhandenem RDL:<br /><br /> 2000 RDL, aktualisiert auf 2008 RDL<br /><br /> 2005 RDL, aktualisiert auf 2008 RDL|2008 RDL|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]Berichts-Generator|Autoren 2010 RDL. Beim Öffnen von vorhandenem RDL:<br /><br /> 2000 RDL, aktualisiert auf 2010 RDL<br /><br /> 2005 RDL, aktualisiert auf 2010 RDL<br /><br /> 2008 RDL, aktualisiert auf 2010 RDL|2010 RDL|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|  
|Visual Studio RDLC-Berichts-Designer – Berichts-Designer|2005 RDLC|–|–|  
  
 Weitere Informationen zu [!INCLUDE[ss_dtbi_vs2013](../includes/ss-dtbi-vs2013-md.md)]finden Sie in folgenden Themen:  
  
-   [Bereitstellung und Versions Unterstützung in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
-   [Microsoft SQL Server Data Tools-Business Intelligence für Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843).  
  
##  <a name="bkmk_reportviewer"></a>Report Viewer-Steuerelemente  
 Ein [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ReportViewer-Steuerelement kann einen RDLC-Bericht im lokalen Vorschaumodus oder im Remotemodus anzeigen; das Steuerelement kann eine RDL-Datei anzeigen, die auf einem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver gehostet wird. In der folgenden Tabelle sind die RDL-Versionen aufgelistet, die von den ReportViewer-Steuerelementen für die lokale Verarbeitung (.rdlc) unterstützt werden. Informationen zur serverseitigen RDL-Unterstützung finden Sie im Abschnitt [Unterstützung von Berichtsservern und RDL-Schemas](#bkmk_report_server_rdl_schema_support).  
  
|ReportViewer-Steuerelement im Produkt|RDL-Version für lokale Vorschau|  
|-------------------------------------|--------------------------------------|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]2013<br /><br /> oder<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]2012<br /><br /> oder<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]|2008 RDL|  
|[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]<br /><br /> oder<br /><br /> [!INCLUDE[vsOrcas](../includes/vsorcas-md.md)]|2005 RDL|  
  
 Weitere Informationen finden Sie unter  
  
-   [Umrechnen von RDLC-Dateien in RDL-Dateien](https://msdn.microsoft.com/library/ms252109.aspx)  
  
-   [Report Viewer-Steuerelemente (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx)  
  
-   [Hinzufügen und Konfigurieren der Report Viewer-Steuerelemente](https://msdn.microsoft.com/library/ms252104.aspx)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichte, Berichtsteile und Berichtsdefinitionen &#40;Berichts-Generator und SSRS&#41;](report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Reporting Services-Tools](tools/reporting-services-tools.md)   
 [Berichtsdefinitionssprache (SSRS)](reports/report-definition-language-ssrs.md)  
  
  
