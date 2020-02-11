---
title: Wichtige Änderungen in SQL Server Reporting Services in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d86c9bb07a52aba0cd93b006fc33edf4d1aa885
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109929"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2014"></a>Aktuelle Änderungen in SQL Server Reporting Services in SQL Server 2014
  In diesem Thema werden wichtige Änderungen in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade oder in benutzerdefinierten Skripts oder Berichten auftreten. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
 **In diesem Thema:**  
  
-   [SQL Server 2014 Reporting Services wichtige Änderungen](#bkmk_sql14)  
  
-   [Aktuelle Änderungen in SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Wichtige Änderungen in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services wichtige Änderungen  
 Es gibt keine wesentlichen Änderungen in Bezug auf [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services wichtige Änderungen  
  
### <a name="sharepoint-mode-server-references-require-the-sharepoint-site"></a>Serververweise im SharePoint-Modus erfordern die SharePoint-Website  
 Sie können nicht direkt über den Namen des virtuellen Verzeichnisses im URL-Pfad zum Berichtsserver navigieren oder auf diesen verweisen. Beispiel:  
  
 `http://<Server name>/ReportServer`  
  
 Stattdessen müssen Sie jetzt die SharePoint-Website in den URL-Pfad einschließen. Wenn Ihr Standort Name beispielsweise "`videos`" lautet und das Präfix "`sites`" verwendet, sieht die URL etwa wie folgt aus:  
  
 `http://<Server Name>/sites/videos/_vti_bin/ReportServer`  
  
### <a name="changes-to-sharepoint-mode-command-line-installation"></a>Änderungen an der SharePoint-Modus-Befehlszeileninstallation  
 Die Eingabeeinstellung **/RSINSTALLMODE** kann nur noch mit Installationen im einheitlichen Modus, jedoch nicht mit Installationen im SharePoint-Modus verwendet werden. Beispielsweise wird Folgendes in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]nicht unterstützt: **/RSINSTALLMODE = "defaultsharepointmode"**. Verwenden Sie statt dieser Eingabeeinstellung **/RSSHPINSTALLMODE="DefaultSharePointMode"**.  
  
 Die folgende Anweisung ist ein Beispiel für einen kompletten Installations Befehl und Parametersatz: **Setup/Action = install/Features = SQL, RS/instanceName = Denali_INST1..../RSSHPINSTALLMODE = "defaultsharepointmode"**  
  
 Weitere Informationen zu Befehlszeilen Installationen finden Sie unter [Installation von Reporting Services im SharePoint-Modus und](install-windows/install-reporting-services-at-the-command-prompt.md)im einheitlichen Modus.  
  
### <a name="the-reporting-services-wmi-provider-no-longer-supports-configuration-of-sharepoint-mode"></a>Die Konfiguration des SharePoint-Modus wird vom Reporting Services-WMI-Anbieter nicht mehr unterstützt  
 Die Konfiguration von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint erfolgt jetzt mit PowerShell-Cmdlets und der SharePoint-Zentraladministration. Die neue Architektur des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus nutzt die SharePoint Services-Architektur. SharePoint unterstützt keine WMI-Schnittstellen.  
  
 In der folgenden Liste sind die von diesen Änderungen betroffenen Komponenten und Workflows aufgeführt:  
  
-   Benutzerdefinierte Anwendungen, die den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -WMI-Anbieter für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus verwenden.  
  
-   Der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, rskeymgmt.exe und rsconfig.exe. Verwenden Sie statt diesen Hilfsprogrammen zur Konfiguration des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus die SharePoint-Zentraladministration und PowerShell.  
  
-   SQL Server Management Studio: Kunden können nicht auf einen Server mit einer ähnlichen Syntax wie <machine_name>/<instance_name> verweisen. Ab der [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] -Version war die empfohlene Methode, eine SharePoint-Website-URL zu verwenden. Beispiel: **http://<sharepoint_server>/<sharePoint_site>**. Ab [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]ist die einzige unterstützte Syntax eine SharePoint-Website-URL.  
  
### <a name="report-model-designer-is-not-available-in-sql-server-data-tools"></a>Der Berichtsmodell-Designer ist in SQL Server-Datentools nicht verfügbar  
 
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] unterstützt Berichtsmodellprojekte nicht mehr. Der Berichtsmodell-Designer steht in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]nicht zur Verfügung. Sie können keine neuen Berichtsmodellprojekte erstellen oder vorhandene Projekte in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] öffnen, und Sie können keine Berichtsmodelle erstellen oder aktualisieren. Um Berichtsmodelle zu aktualisieren, können Sie [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] oder frühere Tools verwenden. Sie können Berichtsmodelle weiterhin als Datenquellen in Berichten verwenden, die in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] -Tools, wie z. B. Berichts-Generator und Berichts-Designer, erstellt wurden. Der Abfrage-Designer, den Sie zum Erstellen von Abfragen zum Extrahieren von Berichtsdaten aus Berichts Modellen verwenden, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]ist weiterhin in verfügbar.  
  
##  <a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services wichtige Änderungen  
 In diesem Abschnitt werden neueste Änderungen in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]beschrieben.  
  
> [!NOTE]  
>  Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.  
  
### <a name="expanded-csv-data-renderer"></a>Erweiterter CSV-Datenrenderer  
 In [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]enthält die CSV-Datei Diagramm-und Messgeräte Daten. Anwendungen, die von einer vorherigen CSV-Datei-Struktur abhängen, funktionieren wegen der weiteren Spalten für Diagramme und Messgeräte nicht mehr.  
  
 Weitere Informationen finden Sie unter [Exportieren als CSV-Datei &#40;Berichts-Generator und SSRS&#41;](report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md)mit den Daten arbeiten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verhaltensänderungen in SQL Server Reporting Services in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Als veraltet markierte Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
