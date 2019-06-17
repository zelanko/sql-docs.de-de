---
title: Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: da2eb97e5ce57a2e6a82dda3e264b33e1e3a3b11
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66103793"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a>Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus
  In diesem Abschnitt finden Sie Verfahren zum Konfigurieren einer Berichtsserverinstanz im einheitlichen Modus mithilfe des Reporting Services-Konfigurations-Managers.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die Themen in diesem Abschnitt sind in Kategorien geordnet, sodass Sie die benötigten Anweisungen leichter finden können. Der erste Abschnitt enthält Themen zu Basiskonfigurationsaufgaben für einen Berichtsserver im einheitlichen Modus. Der zweite Abschnitt enthält Themen zur erweiterten Konfiguration. Der dritte Abschnitt enthält Themen zum Konfigurieren eines Berichtsservers zur Ausführung im integrierten SharePoint-Modus.  
  
### <a name="basic-configuration"></a>Basiskonfiguration  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
 Beschreibt die Schritte zum Starten des Reporting Services-Konfigurationstools.  
  
 [Konfigurieren eines Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)  
 Erläutert, wie Konto- und Kennwortinformationen für den Berichtsserver-Dienst angegeben werden.  
  
 [Registrieren eines Dienstprinzipalnamens &#40;SPN&#41; für einen Berichtsserver](register-a-service-principal-name-spn-for-a-report-server.md)  
 Erläutert die manuelle Registrierung eines SPN für einen Berichtsserver, der unter einem Domänenbenutzerkonto in einem Netzwerk ausgeführt wird, das Kerberos-Authentifizierung verwendet.  
  
 [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)  
 Beschreibt die Einrichtung einer oder mehrerer URLs, die für den Zugriff auf den Report Server-Webdienst und den Berichts-Manager verwendet werden.  
  
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 Beschreibt die Schritte zum Erstellen einer Berichtsserver-Datenbank. Dieses Verfahren ist für die Bereitstellung einer Reporting Services-Installation erforderlich.  
  
### <a name="advanced-or-optional-configuration"></a>Erweiterte oder optionale Konfiguration  
 [Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Beschreibt die Schritte zum Konfigurieren mehrerer Berichtsserver für das gemeinsame Verwenden einer Berichtsserver-Datenbank.  
  
 [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Beschreibt die Schritte zum Konfigurieren eines Berichtsservers für die E-Mail-Verteilung.  
  
 [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](configure-a-firewall-for-report-server-access.md)  
 Erklärt, wie für eingehende Anforderungen und ausgehende Antworten von einem Berichtsserver verwendete Ports geöffnet werden.  
  
 [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 Beschreibt zusätzliche Schritte, die erforderlich sind, um über http://localhost eine Verbindung mit dem Berichts-Manager oder einem Berichtsserver herzustellen.  
  
 [Configure a Report Server for Remote Administration (Konfigurieren eines Berichtsservers für die Remoteverwaltung)](configure-a-report-server-for-remote-administration.md)  
 Erläutert, wie eine Remote-Berichtsserverinstanz so konfiguriert werden kann, dass Sie mit ihr eine Verbindung herstellen und sie über einen anderen Computer konfigurieren können.  
  
 [Aktivieren und Deaktivieren der Reporting Services-Funktionen](turn-reporting-services-features-on-or-off.md)  
 Erklärt, wie nicht verwendete Funktionen in einer Reporting Services-Installation entfernt werden können.  
  
 [Aktivieren von Remotefehlern &#40;Reporting Services&#41;](enable-remote-errors-reporting-services.md)  
 Erläutert, wie Servereigenschaften auf einem Berichtsserver festgelegt werden, um zusätzliche Informationen zu auf Remoteservern aufgetretenen Fehlerbedingungen zurückzugeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren und Verwalten eines Berichtsservers &#40;einheitlicher SSRS-Modus&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Konfiguration und Verwaltung eines Berichtsservers &#40;SharePoint-Modus von Reporting Services&#41;](../configure-administer-report-server-reporting-services-sharepoint-mode.md)  
  
  
