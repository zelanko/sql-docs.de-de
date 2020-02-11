---
title: „Nur-Datei“-Installation (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a854de693bce88fcba0de2f1c08e4b0fe296b512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108843"
---
# <a name="files-only-installation-reporting-services"></a>Ausschließliche Datei-Installation (Reporting Services)
  Die reine *Datei Installation* bezieht sich auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] eine-Installation, bei der das Setup [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] die Ordnerstruktur für Programmdateien erstellt, die Dateien auf den Datenträger kopiert, den Berichts Server Dienst auf dem lokalen Computer registriert, das Dienst Konto konfiguriert, dem Dienst Konto Dateien Berechtigungen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erteilt und den WMI-Anbieter registriert.  
  
 Eine Nur-Dateien-Installationsdatei umfasst folgende [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen: Berichtsserver-Dienst (hostet den Berichtsserver-Webdienst, Hintergrundverarbeitungsanwendung und Berichts-Manager), Berichts-Generator, das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool und die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Befehlszeilenhilfsprogramme (rsconfig.exe, rskeymgmt.exe und rs.exe). Sie gilt nicht für gemeinsam genutzte Funktionen wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], die als separate Elemente angegeben werden müssen, wenn Sie Sie installieren möchten.  
  
 Im Gegensatz zu anderen Installationsarten ist ein Berichtsserver, der ausschließlich mit Dateien installiert wird, nicht funktionsfähig, wenn das Setup beendet ist. Eine zusätzliche Konfiguration ist nötig, damit der Berichtsserver mithilfe von [Konfigurations-Manager für Reporting Services (einheitlicher Modus)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) online geschaltet werden kann.  
  
## <a name="when-to-select-files-only-installation-mode"></a>Sinnvoller Einsatz einer ausschließlichen Datei-Installation  
 Eine ausschließliche Datei-Installation muss ausgeführt werden, wenn:  
  
-   Sie eine Verbindung zwischen Berichtsserverinstanz und einer Remoteberichtsserver-Datenbank herstellen möchten  
  
-   Sie den Berichtsserver als benannte Instanz installieren möchten.  
  
-   Sie Anwendungserfordernisse haben, die benutzerdefinierte Einstellungen oder Funktionen umfassen, und wenn Sie Zeitpunkt und Art der Serverkonfiguration komplett steuern möchten.  
  
-   Installieren eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusters, der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]beinhaltet  
  
## <a name="how-to-perform-a-files-only-installation"></a>Vorgehensweise: Ausführen der ausschließlichen Datei-Installation  
 Die ausschließliche Datei-Installation ist die Standardvorgabe für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Sie können die ausschließliche Datei-Installation über die Befehlszeile oder im Installations-Assistenten angeben. Folgende Themen enthalten Schritt-für-Schritt-Anweisungen:  
  
-   [Installieren Sie SQL Server 2014 aus dem Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
-   [Installieren Sie SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
#### <a name="example-command-line-script"></a>Beispiel eines Befehlszeilenskripts:  
 Aus Gründen der Klarheit umfasst das Beispiel den /RSINSTALLMODE = "FilesOnlyMode". Da der ausschließliche Dateimodus jedoch als Standardinstallationsmodus verwendet wird, können Sie diesen Schritt weglassen. Es erfolgt trotzdem eine ausschließliche Datei-Installation.  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a>Installations-Assistent  
 Wenn Sie auf der Seite Funktionsauswahl die Option [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auswählen, öffnet das Setup die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsseite, auf der Sie den Installationsmodus angeben können. Um anzugeben, dass nur Dateien installiert werden, wählen Sie auf der Seite **-Konfiguration die Option** Berichtsserver installieren, aber nicht konfigurieren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überprüfen einer Reporting Services Installation](verify-a-reporting-services-installation.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren einer Verbindung mit der Berichts Server-Datenbank &#40;SSRS-Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Reporting Services Installation im SharePoint-Modus &#40;SharePoint 2010 und SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md)   
 [Installieren Reporting Services Berichts Servers im einheitlichen Modus](install-reporting-services-native-mode-report-server.md)   
 [Reporting Services-Tools](../tools/reporting-services-tools.md)  
  
  
