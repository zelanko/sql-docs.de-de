---
title: Wichtige Änderungen in SQL Server Reporting Services in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1bc91211f646129ca0686ae5d8bffe2371ba0a57
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076120"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2014"></a>Aktuelle Änderungen in SQL Server Reporting Services in SQL Server 2014
  In diesem Thema werden wichtige Änderungen in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade oder in benutzerdefinierten Skripts oder Berichten auftreten. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
 **In diesem Thema:**  
  
-   [Wichtige Änderungen in SQL Server 2014 Reporting Services](#bkmk_sql14)  
  
-   [Wichtige Änderungen in SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Wichtige Änderungen in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services, die wichtige Änderungen  
 Es gibt keine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] wichtige Änderungen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services, die wichtige Änderungen  
  
### <a name="sharepoint-mode-server-references-require-the-sharepoint-site"></a>Serververweise im SharePoint-Modus erfordern die SharePoint-Website  
 Sie können nicht direkt über den Namen des virtuellen Verzeichnisses im URL-Pfad zum Berichtsserver navigieren oder auf diesen verweisen. Zum Beispiel:  
  
 `http://<Server name>/ReportServer`  
  
 Stattdessen müssen Sie jetzt die SharePoint-Website in den URL-Pfad einschließen. Angenommen, der Name der Website lautet "`videos`", und die Website verwendet das Präfix "`sites`". Die URL sieht dann der folgenden ähnlich:  
  
 `http://<Server Name>/sites/videos/_vti_bin/ReportServer`  
  
### <a name="changes-to-sharepoint-mode-command-line-installation"></a>Änderungen an der SharePoint-Modus-Befehlszeileninstallation  
 Die Eingabeeinstellung **/RSINSTALLMODE** kann nur noch mit Installationen im einheitlichen Modus, jedoch nicht mit Installationen im SharePoint-Modus verwendet werden. Beispielsweise wird Folgendes nicht unterstützt [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]: **/rsinstallmode = "DefaultSharePointMode"**. Verwenden Sie statt dieser Eingabeeinstellung **/RSSHPINSTALLMODE="DefaultSharePointMode"**.  
  
 Die folgende Anweisung ist ein Beispiel für einen vollständigen Installationsbefehl und Parametersatz: **setup /ACTION=install /FEATURES=SQL,RS /InstanceName=Denali_INST1 …. /RSSHPINSTALLMODE="DefaultSharePointMode"**  
  
 Weitere Informationen zu Befehlszeileninstallationen, finden Sie unter [Command Prompt Installation von Reporting Services SharePoint-Modus und einheitlichen Modus](install-windows/install-reporting-services-at-the-command-prompt.md).  
  
### <a name="the-reporting-services-wmi-provider-no-longer-supports-configuration-of-sharepoint-mode"></a>Die Konfiguration des SharePoint-Modus wird vom Reporting Services-WMI-Anbieter nicht mehr unterstützt  
 Die Konfiguration von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint erfolgt jetzt mit PowerShell-Cmdlets und der SharePoint-Zentraladministration. Die neue Architektur des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus nutzt die SharePoint Services-Architektur. SharePoint unterstützt keine WMI-Schnittstellen.  
  
 In der folgenden Liste sind die von diesen Änderungen betroffenen Komponenten und Workflows aufgeführt:  
  
-   Benutzerdefinierte Anwendungen, mit denen die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI-Anbieter für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus.  
  
-   Der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Konfigurations-Manager, rskeymgmt.exe und rsconfig.exe. Statt diesen Hilfsprogrammen für die Konfiguration der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus verwenden SharePoint-Zentraladministration und PowerShell.  
  
-   SQL Server Management Studio: Kunden können auf keinen Server mit einer ähnlichen Syntax wie <machine_name>/<instance_name> verweisen. Ab der [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]-Version war die empfohlene Methode, eine SharePoint-Website-URL zu verwenden. Z. B. **http://<sharepoint_server>/<sharePoint_site&gt**. Beginnend mit [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], eine SharePoint-Website-URL ist die einzige unterstützte Syntax.  
  
### <a name="report-model-designer-is-not-available-in-sql-server-data-tools"></a>Der Berichtsmodell-Designer ist in SQL Server-Datentools nicht verfügbar  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] nicht mehr unterstützt berichtsmodellprojekte. Der Berichtsmodell-Designer steht in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] nicht zur Verfügung. Sie können keine neuen berichtsmodellprojekte erstellen oder öffnen Sie vorhandene Projekte in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und Sie nicht erstellen oder Aktualisieren von Berichtsmodellen. Um Berichtsmodelle zu aktualisieren, können Sie [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] oder frühere Tools. Sie können Berichtsmodelle weiterhin als Datenquellen in Berichten verwenden, die in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]-Tools, wie z. B. Berichts-Generator und Berichts-Designer, erstellt wurden. Der Abfrage-Designer, mit denen Sie Abfragen erstellen, um die Berichtsdaten aus Berichtsmodellen zu extrahieren weiterhin verfügbar in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
##  <a name="bkmk_kj"></a> Wichtige Änderungen in SQL Server 2008 R2 Reporting Services  
 Dieser Abschnitt beschreibt wichtige Änderungen in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.  
  
### <a name="expanded-csv-data-renderer"></a>Erweiterter CSV-Datenrenderer  
 In [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], die CSV-Datei enthält, Diagramm-und messgerätdaten. Anwendungen, die von einer vorherigen CSV-Datei-Struktur abhängen, funktionieren wegen der weiteren Spalten für Diagramme und Messgeräte nicht mehr.  
  
 Weitere Informationen finden Sie unter [Exportieren als CSV-Datei &#40;Berichts-Generator und SSRS&#41;](report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verhaltensänderungen in SQL Server Reporting Services in SQLServer 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Als veraltet markierte Funktionen in SQL Server Reporting Services in SQLServer 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
