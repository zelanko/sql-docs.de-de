---
title: Analysis Services Instanzverwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0455fa4f-b92d-4a8b-a8f0-f2a268a5c84e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac0c6637dd08dc2ea8927853b7a6bf8dccca454d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080348"
---
# <a name="analysis-services-instance-management"></a>Analysis Services-Instanzverwaltung
  Eine Instanz von Analysis Services ist eine Kopie der ausführbaren Datei `msmdsrv.exe`, die als Betriebssystemdienst ausgeführt wird. Jede Instanz ist völlig unabhängig von anderen Instanzen auf dem gleichen Server. Sie hat ihre eigenen Konfigurationseinstellungen, Berechtigungen, Anschlüsse, Startkonten, Dateispeicher und Servermoduseigenschaften.  
  
 Jede Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] wird im Sicherheitskontext eines definierten Anmeldekontos als Windows-Dienst Msmdsrv.exe ausgeführt.  
  
-   Der Dienstname der Standardinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lautet MSSQLServerOLAPService.  
  
-   Der Dienstname der einzelnen benannten Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lautet MSOLAP$InstanceName.  
  
> [!NOTE]  
>  Wenn Sie mehrere Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installiert haben, installiert Setup auch einen Redirectordienst, der in den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst integriert ist. Der Redirectordienst ist für das Umleiten von Clients an die entsprechende benannte Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zuständig. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst wird immer im Sicherheitskontext des lokalen Dienstkontos ausgeführt, ein Standardbenutzerkonto, das Windows für Systemdienste verwendet, die nicht auf Ressourcen außerhalb des lokalen Computers zugreifen.  
  
 Mehrere Instanzen bedeuten, dass Sie skalieren können, indem Sie mehrere Serverinstanzen auf der gleichen Hardware installieren. Besonders für Analysis Services bedeutet dies auch, dass Sie verschiedene Servermodi unterstützen können, indem Sie mehrere Instanzen auf dem gleichen Server haben, von denen jede für die Ausführung in einem bestimmten Modus konfiguriert ist.  
  
 Der Servermodus ist eine Servereigenschaft, die bestimmt, welche Speicher- und Arbeitsspeicherarchitektur für diese Instanz verwendet wird. Ein Server, der im mehrdimensionalen Modus ausgeführt wird, verwendet die Ressourcenmanagementebene, die für mehrdimensionale Cubedatenbanken und Data Mining-Modelle erstellt wurde. Im Gegensatz dazu werden im tabellarischen Servermodus mithilfe der xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) und der Datenkomprimierung wie angefordert Daten aggregiert.  
  
 Unterschiede in der Speicher- und Arbeitsspeicherarchitektur bedeuten, dass eine einzelne Instanz von Analysis Services entweder Tabellendatenbanken oder mehrdimensionale Datenbanken ausführt, aber nicht beide. Die Servermoduseigenschaft bestimmt, welcher Datenbanktyp auf der Instanz ausgeführt wird.  
  
 Der Servermodus wird während der Installation festgelegt, wenn Sie den Datenbanktyp angeben, der auf dem Server ausgeführt wird. Um alle verfügbaren Modi zu unterstützen, können Sie mehrere Instanzen von Analysis Services installieren und jeweils in einem Servermodus bereitstellen, der den von Ihnen erstellten Projekten entspricht.  
  
 Im Allgemeinen sind die meisten administrativen Aufgaben, die Sie ausführen müssen, in den einzelnen Modi dieselben. Als Analysis Services-Systemadministrator können Sie unabhängig von der Installationsart die gleichen Prozeduren und Skripte für das Verwalten aller Analysis Services-Instanzen im Netzwerk verwenden.  
  
> [!NOTE]  
>  Eine Ausnahme hiervon stellt PowerPivot für SharePoint dar. Die Serververwaltung einer PowerPivot-Bereitstellung findet immer innerhalb des Kontexts einer SharePoint-Farm statt. PowerPivot unterscheidet sich von anderen Servermodi darin, dass es sich immer um eine Einzelinstanz handelt, die immer über die SharePoint-Zentraladministration oder das PowerPivot-Konfigurationstool verwaltet wird. Obwohl es möglich ist, in SQL Server Management Studio oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]eine Verbindung mit PowerPivot für SharePoint herzustellen, ist dies nicht zu empfehlen. Eine SharePoint-Farm enthält Infrastrukturen, die den Serverstatus synchronisieren und die Serververfügbarkeit überwachen. Die Verwendung anderer Tools kann diese Vorgänge beeinträchtigen. Weitere Informationen zur Power Pivot-Serververwaltung finden Sie unter [PowerPivot für SharePoint &#40;SSAS&#41;](../power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Link|Taskbeschreibung|  
|----------|----------------------|  
|[Konfiguration nach der Installation &#40;Analysis Services&#41;](post-install-configuration-analysis-services.md)|Beschreibt die erforderlichen und optionalen Aufgaben, durch die eine Analysis Services-Installation abgeschlossen oder geändert wird.|  
|[Verbindung mit Analysis Services herstellen](connect-to-analysis-services.md)|Beschreibt Verbindungszeichenfolgen-Eigenschaften, Clientbibliotheken, Authentifizierungsmethoden und Schritte zum Herstellen oder Löschen von Verbindungen.|  
|[Überwachen einer Instanz von Analysis Services](monitor-an-analysis-services-instance.md)|Beschreibt Tools und Techniken zum Überwachen einer Serverinstanz, einschließlich der Verwendung von Systemmonitor und SQL Server Profiler.|  
|[Skriptverwaltungsaufgaben in Analysis Services](../script-administrative-tasks-in-analysis-services.md)|Erklärt, wie viele administrative Aufgaben automatisiert werden, einschließlich der Verarbeitung.|  
|[Globalisierungsszenarien für Analysis Services Multidimensional](../globalization-scenarios-for-analysis-services-multiidimensional.md)|Erläutert die Unterstützung von Sprache und Sortierung, die Schritte zum Ändern der Eigenschaften und Tipps zum Festlegen und Testen von Sprache und Sortierungsverhalten.|  
|[Protokollvorgänge in Analysis Services](log-operations-in-analysis-services.md)|Beschreibt die Protokolle und erklärt, wie Sie diese konfigurieren.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichen von tabellarischen und mehrdimensionalen Lösungen &#40;SSAS-&#41;](../comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Power Pivot-Konfigurationstools](../power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [Power Pivot-Server Verwaltung und-Konfiguration in der zentral Administration](../power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
