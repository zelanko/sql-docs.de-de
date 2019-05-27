---
title: Konfigurations-Manager für Reporting Services (einheitlicher Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
- components [Reporting Services], Reporting Services Configuration tool
ms.assetid: 379eab68-7f13-4997-8d64-38810240756e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bbd786485915405de36511f5710e3490bdfd8a3f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092659"
---
# <a name="reporting-services-configuration-manager-native-mode"></a>Reporting Services-Konfigurations-Manager (einheitlicher Modus)
  Sie konfigurieren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installationen mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager im einheitlichen Modus. Wenn Sie einen Berichtsserver mit der Option für die ausschließliche Datei-Installation installiert haben, muss der Server mithilfe des Konfigurations-Managers konfiguriert werden, bevor er verwendet werden kann. Wenn Sie einen Berichtsserver mit der Standardkonfigurationsoption der Installation installiert haben, können Sie mit dem Konfigurations-Manager die während der Installation festgelegten Einstellungen überprüfen oder ändern. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager können Sie eine lokale Berichtsserverinstanz eine oder Remote-Berichtsserverinstanz konfigurieren.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
> [!NOTE]  
>  Mit der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version beginnend, wird der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager nicht entworfen, um SharePoint-Modusberichtsserver zu verwalten. Der SharePoint-Modus wird verwaltet und wird mit der SharePoint-Zentraladministration und PowerShell-Skripts konfiguriert. Weitere Informationen finden Sie unter [Reporting Services SharePoint-Modus-Installation &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
 **In diesem Abschnitt:**  
  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Gibt Empfehlungen und Schritte zum Ändern von Dienstkonto und Kennwort an.  
  
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Beschreibt das Konfigurieren von URLs, die für den Zugriff auf den Report Server-Webdienst und den Berichts-Manager verwendet werden.  
  
 [Erstellen einer Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 Beschreibt das Erstellen einer Berichtsserver-Datenbank, die für das Speichern von Server-Metadaten und -Objekten erforderlich ist.  
  
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Beschreibt das Ändern der Verbindungszeichenfolge, die vom Berichtsserver zum Herstellen einer Verbindung mit der Berichtsserver-Datenbank verwendet wird.  
  
 [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Beschreibt, wie Sie für ein Benutzerkonto die Verarbeitung von Berichten im unbeaufsichtigten Modus konfigurieren.  
  
 [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Beschreibt, wie Sie für einen Berichtsserver die Verteilung von Berichten per E-Mail konfigurieren.  
  
 [Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Bietet Informationen zum Konfigurieren mehrerer Berichtsserverinstanzen, die eine freigegebene Berichtsserver-Datenbank verwenden.  
  
 [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
 Erläutert das Verwenden und Verwalten von Verschlüsselungsschlüsseln beim Speichern von sensiblen Daten.  
  
 [Manage a Reporting Services Native Mode Report Server (Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus)](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
 Bietet Schritt-für-Schritt-Anweisungen für häufige Aufgaben.  
  
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
 Bietet Hilfethemen für die Seiten im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool.  
  
 **In diesem Thema:**  
  
-   [Szenarien für die Verwendung von Reporting Services-Konfigurations-Manager](#bkmk_scenarios)  
  
-   [Anforderungen](#bkmk_requirements)  
  
-   [So starten Sie den Reporting Services-Konfigurations-Manager](#bkmk_start_configuration_manager)  
  
##  <a name="bkmk_scenarios"></a> Szenarien für die Verwendung des Reporting Services-Konfigurations-Managers  
 Mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager können Sie die folgenden Aufgaben ausführen:  
  
-   Konfigurieren des Berichtsserver-Dienstkontos. Das Konto wird während der Installation konfiguriert, kann aber mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager geändert werden, wenn Sie das Kennwort aktualisieren oder ein anderes Konto verwenden möchten.  
  
-   Erstellen und Konfigurieren von URLs. Der Berichtsserver und der Berichts-Manager sind [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] -Anwendungen, auf die über URLs zugegriffen wird. Die Berichtsserver-URL stellt Zugriff auf die SOAP-Endpunkte vom Berichtsserver bereit. Die Berichts-Manager-URL wird zum Öffnen des Berichts-Managers verwendet. Sie können eine einzelne URL oder mehrere URLs für jede Anwendung konfigurieren.  
  
-   Erstellen und Konfigurieren der Berichtsserver-Datenbank. Der Berichtsserver ist ein statusloser Server, der für die interne Speicherung eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank benötigt. Mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager können Sie eine Verbindung mit der Berichtsserverdatenbank erstellen und konfigurieren. Sie können auch eine bereits vorhandene Berichtsserver-Datenbank auswählen, die bereits den zu verwendenden Inhalt enthält.  
  
-   Konfigurieren Sie eine Bereitstellung im einheitlichen Modus für horizontales Skalieren. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt eine Bereitstellungstopologie, in der mehrere Berichtsserverinstanzen eine einzelne, freigegebene Berichtsserver-Datenbank verwenden. Um einen Berichtsserver für horizontales Skalieren bereitzustellen, stellen Sie mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager eine Verbindung zwischen den einzelnen Berichtsservern und der freigegebenen Berichtsserver-Datenbank her.  
  
-   Sicherung, Wiederherstellung oder Ersetzen des symmetrischen Schlüssels, der verwendet wird, um gespeicherte Verbindungszeichenfolgen und Anmeldeinformationen zu verschlüsseln. Sie müssen über eine Sicherung des symmetrischen Schlüssels verfügen, wenn Sie das Dienstkonto ändern oder eine Berichtsserver-Datenbank auf einen anderen Computer verschieben möchten.  
  
-   Konfigurieren Sie das Konto für die unbeaufsichtigte Ausführung. Dieses Konto wird während geplanter Vorgänge für Remoteverbindungen verwendet oder dann, wenn keine Benutzeranmeldeinformationen verfügbar sind.  
  
-   Konfigurieren Sie Berichtsserver-E-Mail-Optionen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] umfasst eine Berichtsserver-E-Mail-Übermittlungserweiterung, die SMTP (Simple Mail Transfer Protocol) für die Übermittlung von Berichten oder Berichtsverarbeitungsbenachrichtigungen an ein elektronisches Postfach verwendet. Sie können den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager verwenden, um anzugeben, welcher SMTP-Server oder welches Gateway Sie in Ihrem Netzwerk für die E-Mail-Übermittlung verwenden möchten.  
  
 Mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager können Sie keinen Berichtsserverinhalt verwalten, zusätzliche Funktionen aktivieren oder Zugriff auf den Server gewähren. Eine vollständige Bereitstellung setzt voraus, dass Sie auch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] verwenden, um zusätzliche Funktionen zu aktivieren oder Standardwerte zu ändern, sowie den Berichts-Manager, um Benutzerzugriff auf den Server zu gewähren.  
  
##  <a name="bkmk_requirements"></a> Anforderungen  
 Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager ist versionsspezifisch. Mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, der mit dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert wird, können keine früheren Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]konfiguriert werden. Wenn Sie frühere und aktuelle [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Versionen parallel auf einem Computer ausführen, müssen Sie die jeweilige Version des Reporting Services-Konfigurations-Managers verwenden, um Einstellungen für die entsprechende Instanz vorzunehmen.  
  
 Um den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager zu verwenden, müssen folgende Bedingungen erfüllt sein:  
  
-   Lokale Systemadministratorenberechtigungen für den Computer, der den Berichtsserver hostet, den Sie konfigurieren möchten. Wenn Sie einen Remotecomputer konfigurieren, müssen Sie auch über lokale Systemadministratorenberechtigungen verfügen.  
  
-   Sie müssen über die Berechtigung zum Erstellen von Datenbanken auf dem [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verfügen, um Berichtsserver-Datenbanken zu hosten.  
  
-   Der WMI-Dient (Windows Management Instrumentation) muss aktiviert sein und auf jedem Berichtsserver ausgeführt werden, den Sie konfigurieren. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager verwendet zum Herstellen einer Verbindung mit lokalen oder Remoteberichtsservern den WMI-Anbieter des Berichtsservers. Wenn Sie einen Remoteberichtsserver konfigurieren, muss für den Computer der WMI-Remotezugriff zulässig sein. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die Remoteverwaltung](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md).  
  
-   Bevor Sie eine Verbindung zur Instanz eines Berichtsservers herstellen und diese konfigurieren können, müssen Windows Management Instrumentation (WMI)-Remoteaufrufe für die Windows-Firewall aktiviert werden. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die Remoteverwaltung](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager wird bei der Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
##  <a name="bkmk_start_configuration_manager"></a> So starten Sie den Reporting Services-Konfigurations-Manager  
  
#### <a name="to-start-reporting-services-configuration"></a>So starten Sie die Reporting Services-Konfiguration  
  
1.  Führen Sie den folgenden Schritt aus, der für Ihre jeweilige Version von Microsoft Windows geeignet ist:  
  
    -   Geben Sie im Windows-Startbildschirm **Reporting** ein, und wählen Sie in den Suchergebnissen **Konfigurations-Manager für Reporting Services** aus.  
  
    -   Zeigen Sie im Menü **Start**auf **Alle Programme**und anschließend auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], und klicken Sie auf **Konfigurationstools**.  
  
         Wenn Sie eine Berichtsserver-Instanz einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]konfigurieren möchten, öffnen Sie den Programmordner für diese Version. Zeigen Sie beispielsweise auf [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] anstelle von [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] , um die Konfigurationstools für Serverkomponenten von [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] zu öffnen.  
  
         Klicken Sie auf **Reporting Services-Manager**.  
  
2.  Das Dialogfeld **Konfigurationsverbindung für Reporting Services** wird angezeigt, mit dem Sie die Berichtsserverinstanz auswählen können, die Sie konfigurieren möchten. Klicken Sie auf **Verbinden**.  
  
3.  Geben Sie unter **Servername**den Namen des Computers an, auf dem die Berichtsserverinstanz installiert ist. Standardmäßig wird der Name des lokalen Computers angezeigt. Sie können jedoch den Namen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Remoteinstanz eingeben, wenn Sie eine Verbindung mit einem Berichtsserver auf einem Remotecomputer herstellen möchten.  
  
4.  Falls Sie einen Remotecomputer angeben, klicken Sie auf **Suchen** , um eine Verbindung herzustellen.  
  
5.  Wählen Sie unter **Report Server Wählen Sie unterstance**die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz aus, die Sie konfigurieren möchten. Nur Berichtsserverinstanzen für diese Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden in der Liste angezeigt. Frühere Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]können nicht konfiguriert werden.  
  
6.  Klicken Sie auf **Verbinden**.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Reporting Services-Tools](../../reporting-services/tools/reporting-services-tools.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md)   
 [Konfigurieren und Verwalten eines Berichtsservers &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
