---
title: PowerPivot für SharePoint (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 733842d4119c83835feff7c71b63f28d419593ab
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53365822"
---
# <a name="powerpivot-for-sharepoint-ssas"></a>PowerPivot für SharePoint (SSAS)
  PowerPivot für SharePoint ist ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Server, der im SharePoint-Modus ausgeführt wird. PowerPivot für SharePoint stellt Serverhosting der PowerPivot-Daten in einer SharePoint-Farm bereit. PowerPivot-Daten sind ein analytisches Datenmodell, das Sie erstellen mithilfe einer der folgenden:  
  
-   Mit dem PowerPivot für Excel 2010-Add-in  
  
-   Excel 2013  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010  
  
 Für das Serverhosting dieser Daten sind SharePoint, Excel Services und eine Installation von PowerPivot für SharePoint erforderlich. Die Daten werden auf PowerPivot für SharePoint-Instanzen geladen, wo sie mit der PowerPivot-Datenaktualisierungsfunktion nach einem Zeitplan aktualisiert werden können; diese Funktion stellt der Server für Excel 2010-Arbeitsmappen bzw. die SharePoint 2013 Excel Services für Excel 2013-Arbeitsmappen bereit.  
  
## <a name="powerpivot-for-sharepoint-2013"></a>PowerPivot für SharePoint 2013  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] unterstützt die Verwendung von Excel-Arbeitsmappen mit Datenmodellen und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Power View-Berichten durch [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 2013 Excel Services.  
  
 Excel Services in SharePoint 2013 umfasst eine Funktionalität für Datenmodelle, die die Interaktion mit einer PowerPivot-Arbeitsmappe im Browser ermöglicht. Sie müssen kein PowerPivot für SharePoint 2013-Add-In für die Farm bereitstellen. Es ist lediglich erforderlich, einen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus zu installieren und den Server in Excel Services in den Einstellungen unter **Datenmodell** zu registrieren.  
  
 Die Bereitstellung des PowerPivot für SharePoint 2013-Add-Ins macht einen zusätzlichen Funktionsumfang in der SharePoint-Farm verfügbar. Zu den zusätzlichen Funktionen gehören: PowerPivot-Katalog, planmäßige Datenaktualisierung und das PowerPivot-Management-Dashboard.  
  
 ![SSAS PowerPivot-Modus-2-Serverbereitstellung](../media/as-powerpivot-mode-2server-deployment.gif "SSAS, PowerPivot-Modus 2 Server-Bereitstellung")  
  
## <a name="powerpivot-for-sharepoint-2010"></a>PowerPivot für SharePoint 2010  
 PowerPivot für SharePoint 2010 stellt Serverhosting der PowerPivot-Daten in einer SharePoint 2010-Farm bereit. PowerPivot-Daten sind ein analytisches Datenmodell, das Sie in Excel anhand des PowerPivot für Excel-Add-In erstellen. Für das Serverhosting dieser Daten sind SharePoint 2010, Excel Services und eine Installation von PowerPivot für SharePoint erforderlich. Daten werden auf PowerPivot für SharePoint-Instanzen in der Farm geladen, wo sie in geplanten Abständen anhand der auf dem Server bereitgestellten PowerPivot-Datenaktualisierungsfunktion aktualisiert werden.  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a>Komponenten von PowerPivot für SharePoint 2010  
 PowerPivot für SharePoint wird als gemeinsamer Dienst implementiert. Das bedeutet, dass die integrierten Funktionen und die Infrastruktur zum Verwalten, Sichern und Verwenden einer PowerPivot-Dienstanwendung eingesetzt werden können. Die gesamte Ermittlung, Umleitung und Verbindung für Server und Datenbank wird auf Farmebene verwaltet. Die Zentraladministration stellt die Verwaltungsoberfläche für die Dienste bereit, die zum Verwalten der Serveridentität, des Serverstatus und der Konfigurationseigenschaften verwendet werden.  
  
 Eine vollständige Bereitstellung von PowerPivot für SharePoint umfasst Client- und Serverkomponenten, die mit Excel und Excel Services in einer SharePoint-Farm integriert werden. Die PowerPivot-Daten in einer Excel-Arbeitsmappe sind eine Analysis Services-Datenbank, die eine Analysis Services VertiPaq-Engine (xVelocity-Engine für Datenanalyse im Arbeitsspeicher) erfordert, um die Daten zu laden und abzufragen. Auf einer Clientarbeitsstation wird die xVelocity-Engine innerhalb von Excel prozessintern ausgeführt. In einer SharePoint-Farm wird Analysis Services auf einem Anwendungsserver ausgeführt und dort den entsprechenden Diensten zugeordnet, die PowerPivot-Daten anfordern. Das folgende Diagramm stellt die PowerPivot-Client- und -Serverkomponenten dar:  
  
 ![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")  
  
 Der PowerPivot-Webdienst wird auf einem Webanwendungsserver ausgeführt. Er leitet Anforderungen von der Webanwendung an eine PowerPivot-Systemdienstinstanz in der Farm um.  
  
 Der PowerPivot-Systemdienst gibt Ladeanforderungen an den Analysis Services-Server aus und verwaltet laufende Verbindungen zu Daten, die bereits in den Arbeitsspeicher geladen sind, speichert Daten zwischen oder entlädt Daten, wenn sie nicht mehr verwendet werden oder wenn ein Systemressourcenkonflikt auftritt. Er verfolgt auch Benutzeraktivität nach. Serverzustandsdaten und andere Verwendungsdaten werden gesammelt und in Berichten dargestellt, um den Leistungszustand des Systems anzugeben.  
  
 Eine Analysis Services-Serverinstanz im integrierten SharePoint-Modus schließt die Bereitstellung ab. Sie lädt Daten, fragt sie ab und entlädt sie. Sie verarbeitet auch Daten, wenn die Arbeitsmappe für PowerPivot-Datenaktualisierung konfiguriert ist.  Jede Instanz ist eng mit dem lokalen PowerPivot-Systemdienst gekoppelt, der Teil der gleichen Installation ist.  
  
##  <a name="bkmk_RelatedContent"></a> In diesem Abschnitt  
 [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [PowerPivot-Konfiguration mit Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [PowerPivot-Konfigurationstools](power-pivot-configuration-tools.md)  
  
 [PowerPivot-Authentifizierung und -Autorisierung](power-pivot-authentication-and-authorization.md)  
  
 [PowerPivot-Integritätsregeln − konfigurieren](configure-power-pivot-health-rules.md)  
  
 [PowerPivot-Management-Dashboard und -Verwendungsdaten](power-pivot-management-dashboard-and-usage-data.md)  
  
 [PowerPivot-Katalog](../../2014-toc/books-online-for-sql-server-2014.md)  
  
 [PowerPivot-Datenzugriff](power-pivot-data-access.md)  
  
 [PowerPivot-Datenaktualisierung](power-pivot-data-refresh.md)  
  
 [PowerPivot-Datenfeeds](power-pivot-data-feeds.md)  
  
 [PowerPivot BI-Semantikmodellverbindung &#40;bism-Datei&#41;](power-pivot-bi-semantic-model-connection-bism.md)  
  
 **Weitere Abschnitte**  
  
## <a name="additional-topics"></a>Weitere Themen  
 [Upgraden von PowerPivot für SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [PowerPivot für SharePoint 2013 Installation](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [PowerShell-Referenz für PowerPivot für SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [Beispiellizenztopologien und-Kosten für SQL Server 2014 Self-Service-Business Intelligence](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Planung und Bereitstellung](https://go.microsoft.com/fwlink/?linkID=220972)   
 [Notfallwiederherstellung für PowerPivot für SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
