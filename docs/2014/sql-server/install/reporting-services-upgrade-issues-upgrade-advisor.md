---
title: Upgradeprobleme bei (Upgrade Advisor) Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: de69a25d1689883fdcbce8796d3cdcd30374a8f3
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092580"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Upgradeprobleme bei Reporting Services (Upgrade Advisor)
  Die folgenden Themen beschreiben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Probleme, die das Upgrade auf auswirken [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Die Themen beschreiben die Aktionen, die Sie ergreifen können, um die Auswirkungen dieser Änderungen auf Ihre Umgebung zu minimieren.  
  
 Der Updateratgeber analysiert eine Berichtsserverinstallation. Wenn nur Clientkomponenten installiert sind (wenn z. B. der Berichts-Designer als einzige [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Komponente auf dem Computer installiert ist), werden keine Probleme gemeldet.  
  
 Abhängig von der Konfiguration der Installation können weitere Probleme auftreten, die vom Updateratgeber nicht gemeldet werden. Diese Probleme lassen ein [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Update nicht scheitern, sie können sich aber auf die Ausführung von Berichten und Anwendungen nach Abschluss des Updates auswirken. Informationen zu diesen Problemen finden Sie unter "Abwärtskompatibilität von Reporting Services" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Wenn Sie nicht das Setup zum Upgrade der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation verwenden können, können Sie eine neue Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installieren und die bestehende Installation zur neuen Instanz migrieren. Weitere Informationen finden Sie unter "Aktualisieren und Migrieren von Reporting Services" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online, [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 In den folgenden Themen werden bekannte Probleme beschrieben, die vom Updateratgeber gemeldet werden. Außerdem wird erläutert, wie Sie die vorhandene Installation ändern können, um ein Upgrade zuzulassen.  
  
> [!IMPORTANT]  
>  Upgrade Advisor muss auf dem Berichtsserver installiert werden, um eine Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zu analysieren. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt keine Remoteanalyse.  
>   
>  Weitere Informationen finden Sie unter [Installation von Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Clientzertifikate auf den Berichtsserver-Website &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [Auf dem Berichtsserver wurden benutzerdefinierte Erweiterungen erkannt &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Benutzerdefinierte Berichtselemente erkannt wurden, auf dem Berichtsserver &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [IIS-Abwärtskompatibilitätskomponenten wurden nicht erkannt. &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [IP-adresseinschränkung erkannt &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [ISAPI-Filter erkannt wird, auf die Berichtsserversite &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [Veraltete Erweiterungen wurden auf dem Berichtsservercomputer erkannt &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [Berichtsserver-Datenbank ist nicht konfiguriert. &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [SQL Server 2005 Report Server Web Service-Gruppe, die erkannt &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [Virtuelle Verzeichnisse sind nicht spezifiziert &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [Virtuelles Verzeichnis weist eine nicht unterstützte Authentifizierungsmethode &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [Änderungen an CPU- und Arbeitsspeicherlimits für SQL Server Standard und Enterprise &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [Erforderliche Domänenkonten für SharePoint-Farm &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [Direktes Navigieren zum Berichtsserver &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 ist installiert &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server Reporting Services SharePoint Shared Service wird parallel installiert &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [Nicht kompatible Datenbank-Engine-Serversortierung &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Weitere Upgradeprobleme bei Reporting Services](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
