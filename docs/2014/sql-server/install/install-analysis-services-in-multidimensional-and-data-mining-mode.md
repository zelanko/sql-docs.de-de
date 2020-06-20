---
title: Installieren von Analysis Services im mehrdimensionalen und Data Mining-Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
author: heidisteen
ms.author: heidist
ms.openlocfilehash: afb5c9d4d6272608249e095c694e0a9c48b37feb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054776"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a>Installieren von Analysis Services im mehrdimensionalen Modus und im Data Mining-Modus
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bietet OLAP- (Online Analytical Processing, Analytische Onlineverarbeitung) und Data Mining-Funktionalität für Business Intelligence-Anwendungen. In dieser Version ist die Unterstützung für OLAP-Datenbanken und Data Mining Modelle verfügbar, wenn Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im mehr *dimensionalen Modus*installieren. Der multidimensionale Modus ist einer von drei Servermodi, in denen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ausgeführt werden kann. Es handelt sich hierbei um den Standardmodus. Wenn Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mit den Standardwerten installieren, erhalten Sie eine Instanz, die multidimensionale Datenbanken und Data Mining-Modelle ausführt.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist eine Mehrfachinstanz-Funktion, d. h. Sie können mehrere Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf einem einzigen Computer installieren oder eine neue Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] parallel zu einer älteren Version ausführen. Der Servermodus ist für eine Instanz spezifisch. Um andere Modi zu verwenden, müssen Sie weitere Instanzen des Servers installieren.  
  
 Sie können [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] separat oder mit anderen Komponenten installieren. Wenn Sie nur installieren [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , werden die folgenden Funktionen installiert, wenn Sie auf der Seite Funktionsauswahl des Installations-Assistenten **Analysis Services** auswählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Server zum Ausführen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken und Data Mining-Modellen  
  
-   Für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenzugriff auf Quelldatenbanken verwendete Datenanbieter  
  
-   SQL Server-Konfigurations-Manager  
  
## <a name="choosing-additional-features"></a>Auswählen von zusätzlichen Funktionen  
 Für viele OLAP- und Data Warehouse-Lösungen von Analysis Services ist die Installation zusätzlicher [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten erforderlich, damit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken entwickelt, bereitgestellt und verwaltet werden können. In vielen typischen Benutzerszenarien sind die folgenden zusätzlichen Funktionen als Optionen verfügbar:  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] zum Erstellen und Anzeigen von Analysis Services-Datenstrukturen und Data Mining-Modellen.  
  
-   Komponenten für die Konnektivität der Clienttools, die für die Kommunikation zwischen Clients und Servern, einschließlich Netzwerkbibliotheken für DB-Library, ODBC und OLE DB verwendet werden  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ein Satz grafischer und programmierbarer Objekte zum Verschieben, Kopieren und Transformieren von Daten  
  
-   Verwaltungstools, einschließlich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] und Replikationsmonitor  
  
## <a name="installation-tasks"></a>Installationsaufgaben  
 Zur Installation gehören die folgenden Aufgaben:  
  
|Links|Aufgaben|  
|-----------|-----------|  
|[Hardware-und Software Anforderungen für die Installation von SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) und [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).|Überprüfen Sie vor der Ausführung des Setups die erforderlichen Komponenten für die Installation von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], und legen Sie das Konto fest, das Sie für die Bereitstellung des Servers verwenden möchten.|  
|[Installieren Sie SQL Server 2014 aus dem Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).|Führen Sie das SQL Server-Setup aus, um die Software zu installieren.|  
|[Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|Konfigurieren Sie nach dem Setup die Firewalleinstellungen, um Remoteverbindungen mit dem Server zuzulassen.|  
|[Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services)|Benutzer, die auf Analysis Services-Datenbanken zugreifen, müssen über Leseberechtigung für mindestens eine Datenbank auf dem Server verfügen.|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Weitere Informationen zum Setup finden Sie in den folgenden Themen:  
  
 [Installieren von Analysis Services im Tabellenmodus](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)  
  
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [Bestimmen des Servermodus einer Analysis Services-Instanz](https://docs.microsoft.com/analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance)  
  
 [SQL Server Data Mining-Add-ins](https://www.microsoft.com/download/details.aspx?id=35578)  
  
 Standardmäßig werden Beispieldatenbanken, Beispielcode und Add-Ins für die Clientanwendung nicht als Teil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups installiert. Informationen zur Installation von Beispieldatenbanken und Beispielcode finden Sie auf der [CodePlex-Website](https://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von den-Editionen unterstützte Funktionen SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)   
 [Sprachen und Sortierungen &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md)   
 [Aktualisieren von Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
