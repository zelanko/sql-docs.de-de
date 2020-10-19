---
title: Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus | Microsoft-Dokumentation
description: In diesen Artikeln erhalten Sie weitere Informationen zum Konfigurieren eines Berichtsservers im einheitlichen Modus oder für die Ausführung im integrierten SharePoint-Modus.
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8e6fe5d4571ea8cd276da46f8c89688cd310da07
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91935116"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a>Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus
  In diesem Abschnitt finden Sie Verfahren zum Konfigurieren einer Berichtsserverinstanz im einheitlichen Modus mithilfe des Berichtsserver-Konfigurations-Managers.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die Themen in diesem Abschnitt sind in Kategorien geordnet, sodass Sie die benötigten Anweisungen leichter finden können. Der erste Abschnitt enthält Themen zu Basiskonfigurationsaufgaben für einen Berichtsserver im einheitlichen Modus. Der zweite Abschnitt enthält Themen zur erweiterten Konfiguration. Der dritte Abschnitt enthält Themen zum Konfigurieren eines Berichtsservers zur Ausführung im integrierten SharePoint-Modus.  
  
### <a name="basic-configuration"></a>Basiskonfiguration  
 [Berichtsserver-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)  
 Beschreibt die Schritte zum Starten des Reporting Services-Konfigurationstools.  
  
 [Konfigurieren eines Dienstkontos &#40;Berichtsserver-Konfigurations-Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Erläutert, wie Konto- und Kennwortinformationen für den Berichtsserver-Dienst angegeben werden.  
  
 [Registrieren eines Dienstprinzipalnamens &#40;SPN&#41; für einen Berichtsserver](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md)  
 Erläutert die manuelle Registrierung eines SPN für einen Berichtsserver, der unter einem Domänenbenutzerkonto in einem Netzwerk ausgeführt wird, das Kerberos-Authentifizierung verwendet.  
  
 [Konfigurieren einer URL &#40;Berichtsserver-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)  
 Beschreibt die Einrichtung einer oder mehrerer URLs, die für den Zugriff auf den Berichtsserver-Webdienst und das Webportal verwendet werden.  
  
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;Berichtsserver-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 Beschreibt die Schritte zum Erstellen einer Berichtsserver-Datenbank. Dieses Verfahren ist für die Bereitstellung einer Reporting Services-Installation erforderlich.  
  
### <a name="advanced-or-optional-configuration"></a>Erweiterte oder optionale Konfiguration  
 [Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren &#40;Berichtsserver-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Beschreibt die Schritte zum Konfigurieren mehrerer Berichtsserver für das gemeinsame Verwenden einer Berichtsserver-Datenbank.  
  
 [E-Mail Delivery in Reporting Services (E-Mail-Übermittlung in Reporting Services)](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)   
 Beschreibt die Schritte zum Konfigurieren eines Berichtsservers für die E-Mail-Verteilung.  
  
 [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
 Erklärt, wie für eingehende Anforderungen und ausgehende Antworten von einem Berichtsserver verwendete Ports geöffnet werden.  
  
 [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 Beschreibt zusätzliche Schritte, die erforderlich sind, um über `https://localhost` eine Verbindung mit dem Webportal oder einem Berichtsserver herzustellen.  
  
 [Configure a Report Server for Remote Administration (Konfigurieren eines Berichtsservers für die Remoteverwaltung)](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md)  
 Erläutert, wie eine Remote-Berichtsserverinstanz so konfiguriert werden kann, dass Sie mit ihr eine Verbindung herstellen und sie über einen anderen Computer konfigurieren können.  
  
 [Turn Reporting Services Features On or Off (Aktivieren und Deaktivieren der Reporting Services-Funktionen)](../../reporting-services/report-server/turn-reporting-services-features-on-or-off.md)  
 Erklärt, wie nicht verwendete Funktionen in einer Reporting Services-Installation entfernt werden können.  
  
 [Aktivieren von Remotefehlern &#40;Reporting Services&#41;](../../reporting-services/report-server/enable-remote-errors-reporting-services.md)  
 Erläutert, wie Servereigenschaften auf einem Berichtsserver festgelegt werden, um zusätzliche Informationen zu auf Remoteservern aufgetretenen Fehlerbedingungen zurückzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren und Verwalten eines Berichtsservers &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Konfiguration und Verwaltung eines Berichtsservers (SharePoint-Modus von Reporting Services)](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md)  
  
  
