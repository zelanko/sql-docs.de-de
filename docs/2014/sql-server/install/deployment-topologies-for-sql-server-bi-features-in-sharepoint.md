---
title: Bereitstellungstopologien für SQL Server-BI-Funktionen in SharePoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 39f76bc7-94e6-4dbc-bfa5-d56f4430bb26
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7ef3ecf31c0539f3b3cb2cf5a4f04b044e625bd1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095597"
---
# <a name="deployment-topologies-for-sql-server-bi-features-in-sharepoint"></a>Bereitstellungstopologien für SQL Server-BI-Funktionen in SharePoint
  In diesem Thema werden allgemeine Topologien zum Installieren der SQL Server-Business Intelligence-Funktionen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] in der SharePoint 2010- und der SharePoint 2013-Umgebung beschrieben. Dazu gehören Installationen mit einem Einzelserver und Installationen mit drei Ebenen.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **In diesem Thema:**  
  
-   [Beispiel für Bereitstellungstopologien mit SharePoint 2013](#bkmk_example_deployments_2013)  
  
    -   [PowerPivot für SharePoint 2013 und Reporting Services-Bereitstellung auf drei Servern](#bkmk_bi_Sharepoint2013_3tier)  
  
    -   [PowerPivot für SharePoint 2013-Bereitstellung für einzelne Server](#bkmk_powerpivot_sharepoint2013_1server)  
  
    -   [PowerPivot für SharePoint 2013-Bereitstellung von zwei Servern](#bkmk_powerpivot_sharepoint2013_2server)  
  
    -   [PowerPivot für SharePoint 2013-Bereitstellung von drei Servern](#bkmk_powerpivot_sharepoint2013_3server)  
  
    -   [PowerPivot für SharePoint 2013 und Reporting Services-Einzelserver-Bereitstellung](#bkmk_powerpivot_ssrs_sharepoint2013_1server)  
  
    -   [PowerPivot für SharePoint 2013 und Reporting Services-Bereitstellung auf zwei Servern](#bkmk_powerpivot_ssrs_sharepoint2013_2server)  
  
-   [Beispiel für Bereitstellungstopologien mit SharePoint 2010](#bkmk_example_deployments_2010)  
  
    -   [Bereitstellungen mit einem Server](#bkmk_sharepoint2010_1server)  
  
    -   [2-Ebenen-Bereitstellung](#bkmk_sharepoint2010_2server)  
  
    -   [Bereitstellung mit drei Ebenen](#bkmk_sharepoint2010_3server)  
  
    -   [Drei Ebenen Horizontal skalierte Bereitstellung](#bkmk_sharepoint2010_scaleserver)  
  
##  <a name="bkmk_example_deployments_2013"></a> Beispiel für Bereitstellungstopologien mit SharePoint 2013  
 Die SQL Server-Setupoption **PowerPivot für SharePoint** ist völlig unabhängig von SharePoint. Zur Unterstützung der Integration werden weder das SharePoint-Objektmodell noch SharePoint-Schnittstellen verwendet. Daher kann [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf einem beliebigen Computer unter Windows Server 2008 R2 oder höher installiert werden. Dazu kann ein Anwendungsserver in einer SharePoint-Farm verwendet werden, was jedoch nicht zwingend erforderlich ist. In einem der Konfigurationsschritte muss in der Excel Services-Konfiguration auf den Server verwiesen werden, auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ausgeführt wird. Zur Unterstützung des Lastenausgleichs und der Fehlertoleranz wird empfohlen, mehrere im SharePoint-Modus ausgeführte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server zu installieren und zu registrieren.  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus** erfordert SharePoint Server 2013 und nutzt die Architektur des SharePoint-Dienstanwendung.  
  
 In den folgenden Abschnitten werden typische Bereitstellungstopologien veranschaulicht:  
  
###  <a name="bkmk_bi_Sharepoint2013_3tier"></a> PowerPivot für SharePoint 2013 und Reporting Services-Bereitstellung auf drei Servern  
 In der folgenden Bereitstellung auf drei Servern werden die SQL Server-Datenbank-Engine, der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus und SharePoint jeweils auf getrennten Servern ausgeführt. Das Installationspaket für [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] 2013 (**spPowerPivot.msi**) muss auf dem SharePoint-Server ausgeführt werden.  
  
 ![SSAS und SSRS-SharePoint-Modus 3 Serverbereitstellung](../../../2014/sql-server/install/media/as-and-rs-3server-deployment.gif "SSAS und SSRS-SharePoint-Modus 3 Server-Bereitstellung")  
  
|||  
|-|-|  
|**(1)**|Excel Service-Anwendung. Die Dienstanwendung wird als Teil der SharePoint-Installation erstellt.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Dienstanwendung zu erstellen. Der Standardname lautet **PowerPivot-Standarddienstanwendung**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung zu erstellen.|  
|**(4)**|Installieren Sie das Reporting Services-Add-In für SharePoint entweder von den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installationsmedien oder aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.|  
|**(5)**|Führen Sie **spPowerPivot.msi** aus, um Datenanbieter, das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Konfigurationstool und den [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Katalog zu installieren sowie Datenaktualisierungen zu planen.|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Server im SharePoint-Modus. Konfigurieren Sie die **Datenmodelleinstellungen** der Excel Services-Anwendung für die Verwendung dieses Servers.|  
|**(7)**|Inhalts-, Konfigurations- und Dienstanwendungs-Datenbanken von SharePoint.|  
  
 ![SharePoint-Einstellungen](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") [Senden von Feedback und Kontaktinformationen Informationen über Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
###  <a name="bkmk_powerpivot_sharepoint2013_1server"></a> PowerPivot für SharePoint 2013-Bereitstellung für einzelne Server  
 Eine Bereitstellung auf einem einzelnen Server ist für Testzwecke geeignet, wird aber nicht für Produktionsbereitstellungen empfohlen.  
  
 Das folgende Diagramm veranschaulicht die Komponenten, die Teil einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Bereitstellung auf einem einzelnen Server sind.  
  
 ![PowerPivot für SharePoint-Single Server-Bereitstellung](../../../2014/sql-server/install/media/as-powerpivot-mode-1server-deployment.gif "PowerPivot für SharePoint-Single Server-Bereitstellung")  
  
|||  
|-|-|  
|**(1)**|Excel Service-Anwendung. Die Dienstanwendung wird als Teil der SharePoint-Installation erstellt.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Dienstanwendung zu erstellen. Der Standardname lautet **PowerPivot-Standarddienstanwendung**.|  
|**(3)**|Inhalts-, Konfigurations- und Dienstanwendungs-Datenbanken von SharePoint.|  
|**(4)**|Ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus. Konfigurieren Sie die **Datenmodelleinstellungen** der Excel Services-Anwendung für die Verwendung dieses Servers.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_2server"></a> PowerPivot für SharePoint 2013-Bereitstellung von zwei Servern  
 In der folgenden Bereitstellung auf zwei Servern werden die SQL Server-Datenbank-Engine und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus auf einem anderen Server als SharePoint ausgeführt. Bei SharePoint 2013 wird das [!INCLUDE[ssGeminiLongvnext](../../includes/ssgeminilongvnext-md.md)] -Installationspaket (**spPowerPivot.msi**) auf dem SharePoint-Server installiert.  
  
 [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] Erweitert SharePoint Server 2013 um serverseitige Verarbeitung von datenaktualisierungen Datenanbieter, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Katalog und verwaltungsunterstützung für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] und Excel-Arbeitsmappen mit erweiterten Datenmodellen.  
  
 Das Installationspaket ist als Teil des [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Feature Packs verfügbar. Das FeaturePack kann heruntergeladen werden, aus der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Downloadcenter unter [Microsoft® SQL Server® 2014 PowerPivot® für Microsoft® SharePoint®](https://go.microsoft.com/fwlink/?LinkID=296473) (HYPERLINK "<https://go.microsoft.com/fwlink/?LinkID=296473>" \t "_blank" <https://go.microsoft.com/fwlink/?LinkID=296473>).  
  
 ![SSAS PowerPivot-Modus-2-Serverbereitstellung](../../../2014/analysis-services/media/as-powerpivot-mode-2server-deployment.gif "SSAS, PowerPivot-Modus 2 Server-Bereitstellung")  
  
|||  
|-|-|  
|**(1)**|Excel Service-Anwendung. Die Dienstanwendung wird als Teil der SharePoint-Installation erstellt.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Dienstanwendung zu erstellen. Der Standardname lautet **PowerPivot-Standarddienstanwendung**.|  
|**(3)**|FÜHREN Sie **spPowerPivot.msi** aus, um Datenanbieter, das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Konfigurationstool und den [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Katalog zu installieren sowie Datenaktualisierungen zu planen.|  
|**(4)**|Ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus. Konfigurieren Sie die **Datenmodelleinstellungen** der Excel Services-Anwendung für die Verwendung dieses Servers.|  
|**(5)**|Inhalts-, Konfigurations- und Dienstanwendungs-Datenbanken von SharePoint.|  
  
###  <a name="bkmk_powerpivot_sharepoint2013_3server"></a> PowerPivot für SharePoint 2013-Bereitstellung von drei Servern  
 In der folgenden Bereitstellung auf drei Servern werden die SQL Server-Datenbank-Engine, der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus und SharePoint jeweils auf getrennten Servern ausgeführt. Das Installationspaket für [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 (spPowerPivot.msi) muss auf dem SharePoint-Server installiert werden.  
  
 ![ALS PowerPivot-Mode3 Serverbereitstellung](../../../2014/sql-server/install/media/as-powerpivot-mode-3server-deployment.gif "als Mode3 für PowerPivot-Server-Bereitstellung")  
  
|||  
|-|-|  
|**(1)**|Excel Service-Anwendung. Die Dienstanwendung wird als Teil der SharePoint-Installation erstellt.|  
|**(2)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Dienstanwendung zu erstellen. Der Standardname lautet **PowerPivot-Standarddienstanwendung**.|  
|**(3)**|FÜHREN Sie spPowerPivot.msi [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] aus, um Datenanbieter, das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Konfigurationstool und den -Katalog zu installieren sowie Datenaktualisierungen zu planen.|  
|**(4)**|Ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus. Konfigurieren Sie die **Datenmodelleinstellungen** der Excel Services-Anwendung für die Verwendung dieses Servers.|  
|**(5)**|Inhalts-, Konfigurations- und Dienstanwendungs-Datenbanken von SharePoint.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_1server"></a> PowerPivot für SharePoint 2013 und Reporting Services-Einzelserver-Bereitstellung  
 Eine Bereitstellung auf einem einzelnen Server ist für Testzwecke geeignet, wird aber nicht für Produktionsbereitstellungen empfohlen.  
  
 ![SSAS und SSRS-SharePoint-Modus 1 Serverbereitstellung](../../../2014/sql-server/install/media/as-and-rs-1server-deployment.gif "SSAS und SSRS-SharePoint-Modus 1 Server-Bereitstellung")  
  
|||  
|-|-|  
|**(1)**|Excel Service-Anwendung. Die Dienstanwendung wird als Teil der SharePoint-Installation erstellt.|  
|**(2)**|PowerPivot-Dienstanwendung. Der Standardname lautet **PowerPivot-Standarddienstanwendung**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung zu erstellen.|  
|**(4)**|Installieren Sie das Reporting Services-Add-In für SharePoint entweder von den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installationsmedien oder aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.|  
|**(5)**|Inhalts-, Konfigurations- und Dienstanwendungs-Datenbanken von SharePoint.|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Server im SharePoint-Modus. Konfigurieren Sie die **Datenmodelleinstellungen** der Excel Services-Anwendung für die Verwendung dieses Servers.|  
  
###  <a name="bkmk_powerpivot_ssrs_sharepoint2013_2server"></a> PowerPivot für SharePoint 2013 und Reporting Services-Bereitstellung auf zwei Servern  
 In der folgenden Bereitstellung auf zwei Servern werden die SQL Server-Datenbank-Engine und der Analysis Services-Server im SharePoint-Modus auf einem anderen Server als SharePoint ausgeführt. Das Installationspaket für PowerPivot für SharePoint 2013 ( **spPowerPivot.msi** ) muss auf dem SharePoint-Server installiert werden.  
  
 ![SSAS und SSRS SharePoint-Modus-2-Serverbereitstellung](../../../2014/sql-server/install/media/as-and-rs-2server-deployment.gif "SSAS und SSRS SharePoint-Modus-2-Serverbereitstellung")  
  
|||  
|-|-|  
|**(1)**|Excel Service-Anwendung. Die Dienstanwendung wird als Teil der SharePoint-Installation erstellt.|  
|**(2)**|PowerPivot-Dienstanwendung. Der Standardname lautet **PowerPivot-Standarddienstanwendung**.|  
|**(3)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung zu erstellen.|  
|**(4)**|Installieren Sie das Reporting Services-Add-In für SharePoint entweder von den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installationsmedien oder aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.|  
|**(5)**|FÜHREN Sie die Datei **spPowerPivot.msi** AUS, um Datenanbieter, das PowerPivot-Konfigurationstool, den PowerPivot-Katalog und das Planen der Datenaktualisierung zu installieren.|  
|**(6)**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Server im SharePoint-Modus. Konfigurieren Sie die **Datenmodelleinstellungen** der Excel Services-Anwendung für die Verwendung dieses Servers.|  
|**(7)**|Inhalts-, Konfigurations- und Dienstanwendungs-Datenbanken von SharePoint.|  
  
##  <a name="bkmk_example_deployments_2010"></a> Beispiel für Bereitstellungstopologien mit SharePoint 2010  
 Das folgende Diagramm zeigt, welche Dienste und Anbieter auf jeder Ebene ausgeführt wurden. Beachten Sie, dass das Diagramm mehrere integrierte Dienste einschließt; diese Dienste sind für einige SQL Server BI-Szenarien erforderlich. Excel Services, Secure Store Services und der Claims to Windows Token Service sind für eine PowerPivot für SharePoint- oder Reporting Services-Bereitstellung in SharePoint erforderlich oder empfohlen. Darüber hinaus sind die MSOLAP OLE DB-Anbieter und ADO.NET Services für einige PowerPivot-Datenzugriffsszenarien erforderlich. Optional können Sie Analysis Services auf der Datenebene installieren, wenn Sie [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichte auf Grundlage von Tabellenmodelldatenbanken erstellen, die außerhalb SharePoint gehostet werden.  
  
 ![Logisches Architekturdiagramm](../../../2014/sql-server/install/media/sql11bisetup.gif "logisches Architekturdiagramm")  
  
##  <a name="bkmk_sharepoint2010_1server"></a> Bereitstellungen mit einem Server  
 Sie können alle Serverkomponenten einschließlich der Datenebene auf einem einzelnen Computer installieren. Diese Bereitstellungskonfiguration ist sinnvoll, wenn Sie die Software auswerten oder benutzerdefinierte Anwendungen entwickeln, die Reporting Services im integrierten SharePoint-Modus umfassen. Diese Bereitstellung ist die am einfachsten zu konfigurierende. Da alle Komponenten auf demselben Computer installiert werden, verwendet sie auch am wenigsten Lizenzen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] und der [!INCLUDE[ssDE](../../includes/ssde-md.md)] sind als eine einzige lizenzierte Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert.  
  
 Um alle Funktionen auf einem einzelnen Server zu installieren, installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sequenziell auf dem gleichen physischen Server. Anweisungen in einer eigenständigen Serverkonfiguration finden Sie [Checkliste für die Bereitstellung: Reporting Services, Power View und PowerPivot für SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
##  <a name="bkmk_sharepoint2010_2server"></a> 2-Ebenen-Bereitstellung  
 Bei einer 2-Ebenen-Bereitstellung befindet sich SharePoint Server 2010 in der Regel auf einem Computer und die SQL Server-Datenbank-Engine auf einem zweiten Computer. Die Verlagerung der Datenebene auf einen dedizierten Server stellt die allgemeinste Konfiguration für eine 2-Computer-Farm dar. In einer 2-Ebenen-Farm installieren Sie sowohl [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] als auch [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf dem SharePoint-Server. Alle Webdienste auf dem Front-End und gemeinsame Dienste auf der Anwendungsebene werden auf dem gleichen physischen Server ausgeführt. Die Installationsschritte bei einer 2-Ebenen-Bereitstellung sind einer eigenständigen Bereitstellung sehr ähnlich, da Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sequenziell auf dem gleichen physischen Server installieren.  
  
##  <a name="bkmk_sharepoint2010_3server"></a> Bereitstellung mit drei Ebenen  
 Bei einer 3-Ebenen-Bereitstellung werden Web-Front-End-Dienste in der Regel von der Verarbeitung oder von speicherintensiven Anwendungen getrennt. Bei dieser Topologie installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] nur auf dem Anwendungsserver. Webdienste, die auf dem Web-Front-End ausgeführt werden, werden über Lösungen installiert, die während der Serverkonfiguration als Tasks nach der Installation in Anwendungen in der Farm bereitgestellt werden. Das folgende Diagramm veranschaulicht eine 3-Ebenen-Bereitstellung.  
  
 ![3-Server-Topologie mit](../../../2014/sql-server/install/media/sql11bisetup-3server.gif "3-Server-Topologie mit")  
  
##  <a name="bkmk_sharepoint2010_scaleserver"></a> Drei Ebenen Horizontal skalierte Bereitstellung  
 Diese Topologie veranschaulicht eine Bereitstellung für horizontales Skalieren, die den gleichen gemeinsamen Dienst auf mehreren Servern ausführt, und somit ein größeres Volumen von Anforderungen bearbeitet und eine höhere Rechenleistung für PowerPivot-Daten oder Reporting Services-Berichte bereitstellt. Im untenstehenden Diagramm gibt es drei Anwendungsservercluster, die alle eine andere Kombination gemeinsamer Dienste ausführen. In einer SharePoint-Umgebung werden Dienstermittlung und -verfügbarkeit in die Farm eingebaut. Lastenausgleich über mehrere physische Server, die die gleiche freigegebene Dienstanwendung ausführen, ist Teil der Architektur des gemeinsamen Diensts.  
  
 Wenn Sie eine multiserverfarm bereitstellen, achten Sie darauf, dass Sie die Anweisungen in diesem SharePoint-Artikel befolgen: [Mehrere Server für eine dreistufige Farm (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkID=219834).  
  
 ![5-Server-Topologie mit](../../../2014/sql-server/install/media/sql11bisetup-5server.gif "5-Server-Topologie mit")  
  
## <a name="see-also"></a>Siehe auch  
 [Installation von SharePoint-Modus von Reporting Services &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [PowerPivot für SharePoint 2013-Installation](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)   
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
