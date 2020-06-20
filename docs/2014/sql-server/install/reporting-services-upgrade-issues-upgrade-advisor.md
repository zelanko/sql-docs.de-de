---
title: Reporting Services Upgradeprobleme (Upgrade Advisor) | Microsoft-Dokumentation
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
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0e2f39ea7b911f2ca83767dcfbfd82947acd4f52
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059010"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Upgradeprobleme bei Reporting Services (Upgrade Advisor)
  In den folgenden Themen werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Probleme beschrieben, die sich möglicherweise auf das Upgrade auf auswirken [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . In den Themen werden Aktionen beschrieben, mit denen Sie die Auswirkungen dieser Änderungen auf Ihre Umgebung mindern können.  
  
 Der Updateratgeber analysiert eine Berichtsserverinstallation. Wenn nur Clientkomponenten installiert sind (wenn z. B. der Berichts-Designer als einzige [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Komponente auf dem Computer installiert ist), werden keine Probleme gemeldet.  
  
 Abhängig von der Konfiguration der Installation können weitere Probleme auftreten, die vom Updateratgeber nicht gemeldet werden. Diese Probleme lassen ein [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Update nicht scheitern, sie können sich aber auf die Ausführung von Berichten und Anwendungen nach Abschluss des Updates auswirken. Informationen zu diesen Problemen finden Sie unter "Abwärtskompatibilität von Reporting Services" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Wenn Sie nicht das Setup zum Upgrade der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation verwenden können, können Sie eine neue Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installieren und die bestehende Installation zur neuen Instanz migrieren. Weitere Informationen finden Sie unter "Upgrade und Migration Reporting Services" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation, [aktualisieren und Migrieren von Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 In den folgenden Themen werden bekannte Probleme beschrieben, die vom Updateratgeber gemeldet werden. Außerdem wird erläutert, wie Sie die vorhandene Installation ändern können, um ein Upgrade zuzulassen.  
  
> [!IMPORTANT]  
>  Upgrade Advisor muss auf dem Berichtsserver installiert werden, um eine Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zu analysieren. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt keine Remoteanalyse.  
>   
>  Weitere Informationen finden Sie unter [Installieren des Upgrade Advisors](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Client Zertifikate auf der Berichts Server-Website &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [Auf dem Berichts Server &#40;Upgrade Advisor wurden benutzerdefinierte Erweiterungen erkannt&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Auf dem Berichts Server &#40;Upgrade Advisor wurden benutzerdefinierte Berichts Elemente erkannt&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [IIS-abwärts Kompatibilitäts Komponenten wurden &#40;Upgrade Advisor nicht erkannt&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [Die IP-Adress Einschränkung wurde &#40;Upgrade Advisor erkannt&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [ISAPI-Filter wurden auf der Berichts Server Website &#40;Upgrade Advisor erkannt&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [Veraltete Erweiterungen wurden auf dem Berichts Server Computer &#40;Upgrade Advisor erkannt&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [Die Berichts Server-Datenbank ist &#40;Upgrade Advisor nicht konfiguriert&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [&#40;Upgrade Advisor wurde SQL Server 2005-Berichts Server-Webdienst Gruppe erkannt&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [Virtuelle Verzeichnisse sind nicht angegeben &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [Das virtuelle Verzeichnis verfügt über eine nicht unterstützte Authentifizierungsmethode &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [Änderungen an den CPU-und Arbeitsspeicher Limits für SQL Server Standard und Enterprise &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [Erforderliche Domänen Konten für die SharePoint-Farm &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [Direktes Navigieren zum Berichts Server &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 wird &#40;Upgrade Advisor installiert&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server Reporting Services gemeinsamer SharePoint-Dienst wird parallel &#40;Upgrade Advisor installiert&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [Nicht kompatible Datenbank-Engine Server-Sortierung &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Weitere Upgradeprobleme bei Reporting Services](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
