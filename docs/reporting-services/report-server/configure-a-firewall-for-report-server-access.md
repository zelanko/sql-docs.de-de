---
title: Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie die Windows-Firewall so konfigurieren, dass der Zugriff auf Berichtsserveranwendungen und auf veröffentlichte Berichte möglich ist, auf die über URLs zugegriffen wird.
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 08a80c8307d551813a30becbed6d12507e6b2947
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545584"
---
# <a name="configure-a-firewall-for-report-server-access"></a>Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserveranwendungen und veröffentlichte Berichte erfolgt über URLs, die eine IP-Adresse, einen Port und ein virtuelles Verzeichnis angeben. Wenn die Windows-Firewall aktiviert ist, ist der Port, für den der Berichtsserver konfiguriert ist, höchstwahrscheinlich geschlossen. Ein Anzeichen für einen geschlossenen Port ist die Anzeige einer leeren Seite, wenn Sie versuchen, das Webportal von einem Remoteclientcomputer aus zu öffnen, oder einer leeren Webseite nach dem Anfordern eines Berichts.  
  
 Um einen Port zu öffnen, müssen Sie das Hilfsprogramm Windows-Firewall auf dem Berichtsservercomputer verwenden. Reporting Services öffnet keine Ports für Sie; Sie müssen diesen Schritt manuell ausführen.  
  
 Standardmäßig lauscht der Berichtsserver HTTP-Anforderungen an Port 80. Die folgenden Anweisungen beinhalten daher Schritte, die diesen Port angeben. Wenn Sie die Berichtsserver-URLs für einen anderen Port konfiguriert haben, müssen Sie die entsprechende Portnummer beim Ausführen der unten stehenden Anweisungen angeben.  
  
 Wenn Sie auf relationale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken auf externen Computern zugreifen oder wenn sich die Berichtsserver-Datenbank auf einer externen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz befindet, müssen Sie Port 1433 und Port 1434 auf dem externen Computer öffnen. Weitere Informationen zur Windows-Firewall finden Sie unter [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md). Weitere Informationen zu den Standardeinstellungen der Windows-Firewall und eine Beschreibung der TCP-Ports, die sich auf das [!INCLUDE[ssDE](../../includes/ssde-md.md)], die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]und die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]auswirken, finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Diese Anweisungen setzen voraus, dass Sie bereits das Dienstkonto konfiguriert, die Berichtsserver-Datenbank erstellt und die URLs für den Berichtsserver-Webdienst und das Webportal konfiguriert haben. Weitere Informationen finden Sie unter [Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md).  
  
 Außerdem sollten Sie überprüft haben, dass auf den Berichtsserver über eine lokale Webbrowserverbindung mit der lokalen Berichtsserverinstanz zugegriffen werden kann. Dieser Schritt setzt voraus, dass Sie eine Arbeitsinstallation haben. Sie sollten überprüfen, ob die Installation ordnungsgemäß konfiguriert ist, bevor Sie mit dem Öffnen von Ports beginnen. Um diesen Schritt auf Windows Server auszuführen, müssen Sie die Berichtsserversite außerdem zu den vertrauenswürdigen Sites hinzugefügt haben. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="opening-ports-in-windows-firewall"></a>Öffnen von Ports in der Windows-Firewall  
  
#### <a name="to-open-port-80"></a>So öffnen Sie Port 80  
  
1.  Klicken Sie im Menü **Start** auf **Systemsteuerung**und dann auf **System und Sicherheit**und **Windows-Firewall**. Wenn die Systemsteuerung nicht für die Kategorieansicht konfiguriert ist, müssen Sie nur **Windows-Firewall**auswählen.  
  
2.  Klicken Sie auf **Erweiterte Einstellungen**.  
  
3.  Klicken Sie auf **Eingehende Regeln**.  
  
4.  Klicken Sie im Fenster **Aktionen** auf **Neue Regel**.  
  
5.  Wählen Sie **Port** als **Regeltyp**aus.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Klicken Sie auf der Seite **Protokolle und Ports** auf **TCP**.  
  
8.  Wählen Sie **Bestimmte lokale Ports** aus, und geben Sie den Wert **80**ein.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Klicken Sie auf der Seite **Aktion** auf **Verbindung zulassen**.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Klicken Sie auf der Seite **Profil** auf die entsprechenden Optionen für die Umgebung.  
  
13. Klicken Sie auf **Weiter**.  
  
14. Geben Sie auf der Seite **Name** den Namen**ReportServer (TCP an Port 80)** ein.  
  
15. Klicken Sie auf **Fertig stellen**.  
  
16. Starten Sie den Computer neu.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nach dem Öffnen des Ports und vor dem Bestätigen, ob Remotebenutzer auf den Berichtsserver über den von Ihnen geöffneten Port zugreifen können, müssen Sie Benutzerzugriff auf den Berichtsserver über Rollenzuweisungen für den Stammordner und auf Siteebene erteilen. Ein Port kann richtig geöffnet sein und dennoch fehlgeschlagene Berichtsserververbindungen verursachen, wenn Benutzer nicht über entsprechende Berechtigungen verfügen. Weitere Informationen finden Sie unter [Gewähren von Benutzerzugriff auf einen Berichtsserver](../../reporting-services/security/grant-user-access-to-a-report-server.md).  
  
 Sie können auch überprüfen, ob der Port richtig geöffnet ist, indem Sie das Webportal auf einem anderen Computer starten. Weitere Informationen finden Sie unter [Das Webportal eines Berichtsservers](../../reporting-services/web-portal-ssrs-native-mode.md).
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Erstellen einer Berichtsserver-Datenbank](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Manage a Reporting Services Native Mode Report Server (Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus)](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
