---
title: 'Prüfliste für die Bereitstellung: Installieren von Reporting Services in eine vorhandene SharePoint-Farm | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 436b4c3d-3f2f-464a-be7e-5c051d9ffb8f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 27e6b4a1fb9726496ac4ae99a08b2e47a9136562
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52399663"
---
# <a name="deployment-checklist-install-reporting-services-into-an-existing-sharepoint-farm"></a>Prüfliste für die Bereitstellung: Installieren von Reporting Services in eine vorhandene SharePoint-Farm
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Berichtsserver können in eine neue SharePoint-Farm oder eine vorhandene SharePoint-Farm installiert werden. Dieses Thema beschreibt die möglichen Szenarien und Best Practices zum Installieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine vorhandene SharePoint-Farm.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie Setup ausführen, machen Sie sich mit den folgenden Informationen vertraut:  
  
|Schritt|Link|  
|----------|----------|  
|Erstellen oder identifizieren Sie die Konten, die in einer Berichtsserverbereitstellung verwendet werden. Sie müssen über ein Dienstkonto für den Berichtsserverdienst und über Anmeldeinformationen zum Herstellen einer Verbindung mit der Berichtsserver-Datenbank verfügen.||  
|Wählen Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Hosten der Berichtsserver-Datenbank aus. Sie können eine lokale oder eine Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden. Sie sollten eine Instanz auf einem Computer auswählen, der über ausreichend Speicherkapazität für Ihre Berichte verfügt.||  
|(Optional) Wenn Sie in Abonnements Berichtsserver-E-Mails verwenden möchten, suchen Sie den Namen des SMTP-Servers oder -Gateways, der/das den E-Mail-Dienst für Ihre Organisation bereitstellt.|[Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)|  
|Hinweis: Wenn Sie einen Computer von einer vorherigen CTP-Version von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] aktualisieren und benutzerdefinierte Änderungen an den Konfigurationsdateien vorgenommen haben, müssen Sie die gleichen Änderungen an den Konfigurationsdateien nach dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vornehmen. Die betroffenen Dateien sind **"Web.config"** und **client.config**.||  
  
## <a name="installation-scenarios"></a>Installationsszenarien  
 In der folgenden Tabelle werden die möglichen Szenarien beim Installieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine vorhandene SharePoint-Farm beschrieben. Im lokalen Modus können Berichte lokal von der SharePoint-Dokumentbibliothek bereitgestellt werden, ohne das eine Integration in einem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver erfolgen muss. Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte ist erforderlich, ein [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver jedoch nicht. Weitere Informationen zum lokalen Modus finden Sie unter [Berichte im lokalen Modus im Vergleich mit Berichten im Berichts-Viewer &#40;Reporting Services im SharePoint-Modus&#41; ](../../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md) und [, wo Sie das Reporting Services-add-in für SharePoint-Produkte finden](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
|Starten der Konfiguration|Workflow|Beenden der Konfiguration|Kommentare|  
|----------------------------|--------------|--------------------------|--------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] im lokalen Modus|Installation|Verbundener Modus [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].||  
|Verbundener Modus [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|Direktes Upgrade|Verbundener Modus [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].||  
|Verbundener Modus [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|Migration|Verbundener Modus [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].||  
  
## <a name="installation-and-in-place-upgrade-checklist"></a>Prüfliste für Installation und direktes Upgrade  
 In der folgenden Tabelle werden die Schritte, Tools und Informationen zusammengefasst, die Sie prüfen und bei der Installation verwenden sollten:  
  
|Schritt|Link|  
|----------|----------|  
|**Installation und Erstkonfiguration**||  
|Installieren Sie das SharePoint-Add-In auf allen Web-Front-End-Computern (WFE).|[Add an Additional Reporting Services Web Front-end to a Farm (Hinzufügen eines zusätzlichen Reporting Services-Web-Front-Ends zu einer Farm)](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Installieren Sie SQL Server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services und die Datenbank-Engine.|[Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Erstellen Sie mindestens eine SSRS-Dienstanwendung, und konfigurieren Sie die Zuordnung der Dienstanwendung.|Finden Sie im Abschnitt "Dienstanwendung" [installieren Sie Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|**Zusätzliche Konfiguration**||  
|Hinzufügen von SSRS-Inhaltstypen zu Ihrer Dokumentbibliothek.|[Hinzufügen von Berichtsserver-Inhaltstypen zu einer Bibliothek &#40;integrierten Reporting Services im SharePoint-Modus&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)|  
|Bereitstellen des SQL Server-Agent|[Provision Subscriptions and Alerts for SSRS Service Applications (Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen)](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)|  
|Konfigurieren von E-Mail-Einstellungen für die Dienstanwendung|[Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|  
|Konfigurieren des Claims to Windows Token Service (c2WTS)|[Claims to Windows Token Service &#40;C2WTS&#41; und Reporting Services](../../../2014/sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)|  
  
## <a name="migration-checklist"></a>Migrationsprüfliste  
 Es folgt eine Liste der grundlegenden Schritte für eine Migration von einer vorhandenen Installation zu einer neuen Installation.  
  
|Schritt|Link|  
|----------|----------|  
|Installieren und konfigurieren Sie den neuen Server. Dazu gehören:<br /><br /> Vorbereitungstool für SharePoint-Produkte<br /><br /> SharePoint 2010-Produkt<br /><br /> SharePoint 2010 SP1<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint-Modus<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint 2010-Produkte|[Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Erstellen Sie mindestens eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung||  
|Sichern Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenbanken||  
|Sichern Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Verschlüsselungsschlüssel.||  
|Stellen Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenbank und -Verschlüsselungsschlüssel wieder her||  
|Ordnen Sie alle Webanwendungen neuen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienstanwendungen zu|Die neue Installation **ist jetzt funktional**|  
|Entfernen Sie die Integrations-URL auf dem alten Server.|Klicken Sie in der SharePoint-Zentraladministration auf der Seite **Allgemeine Anwendungseinstellungen** auf **Reporting Services-Integration**.|  
|Deinstallieren Sie bei Bedarf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] von der alten Installation.||  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [Installation von SharePoint-Modus von Reporting Services &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Leitfaden zum Verwenden von SQL Server-BI-Funktionen in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)   
 [Unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in &#40;SQLServer 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
  
