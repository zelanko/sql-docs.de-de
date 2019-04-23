---
title: „Nur-Datei“-Installation (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c76e3e4f1f2e427d8f56c0b832475a22aee6648d
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59941927"
---
# <a name="files-only-installation-reporting-services"></a>Ausschließliche Datei-Installation (Reporting Services)
  Die*Nur-Dateien-Installation* bezieht sich auf eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation, bei der Setup Folgendes ausführt: Die Ordnerstruktur für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Programmdateien wird erstellt, die Dateien werden auf den Datenträger kopiert, der Berichtsserverdienst wird auf dem lokalen Computer registriert, das Dienstkonto wird konfiguriert, die Dateien erhalten Berechtigungen für das Dienstkonto, und der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Anbieter wird registriert.  
  
 Eine ausschließliche Datei-Installation umfasst die folgenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Features: Berichtsserver-Dienst (hostet die Berichtsserver-Webdienst, hintergrundverarbeitungsanwendung und Berichts-Manager), Berichts-Generator die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, und die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Befehlszeilen-Hilfsprogramme (rsconfig.exe, rskeymgmt.exe und RS.exe). Sie gilt nicht für gemeinsam genutzte Funktionen wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], die im gegebenen Fall bei der Installation als separate Elemente angegeben werden müssen.  
  
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
  
-   [Installieren von SQLServer 2014 vom Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
-   [Installieren von SQLServer 2014 über die Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
#### <a name="example-command-line-script"></a>Beispiel eines Befehlszeilenskripts:  
 Aus Gründen der Klarheit umfasst das Beispiel den /RSINSTALLMODE = "FilesOnlyMode". Da der ausschließliche Dateimodus jedoch als Standardinstallationsmodus verwendet wird, können Sie diesen Schritt weglassen. Es erfolgt trotzdem eine ausschließliche Datei-Installation.  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a>Installations-Assistent  
 Wenn Sie auf der Seite Funktionsauswahl die Option [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auswählen, öffnet das Setup die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsseite, auf der Sie den Installationsmodus angeben können. Um anzugeben, dass nur Dateien installiert werden, wählen Sie auf der Seite **-Konfiguration die Option** Berichtsserver installieren, aber nicht konfigurieren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen einer Installation von Reporting Services](verify-a-reporting-services-installation.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Installation von SharePoint-Modus von Reporting Services &#40;SharePoint 2010 und SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md)   
 [Installieren des Reporting Services-Berichtsservers im einheitlichen Modus](install-reporting-services-native-mode-report-server.md)   
 [Reporting Services-Tools](../tools/reporting-services-tools.md)  
  
  
