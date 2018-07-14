---
title: Installieren Sie Reporting Services-Berichtsserver im einheitlichen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- report servers [Reporting Services], default configurations
- installation options [Reporting Services]
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
caps.latest.revision: 58
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0260982df5dff6640a4a273916c8e4455bd18621
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329440"
---
# <a name="install-reporting-services-native-mode-report-server"></a>Installieren des Reporting Services-Berichtsservers im einheitlichen Modus
  Ein [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver im einheitlichen Modus kann mit dem Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder über die Befehlszeile installiert werden. Im Setup-Assistenten können Sie wahlweise 1) Dateien installieren und den Server anhand der Standardeinstellungen konfigurieren oder 2) nur die Dateien installieren, ohne dass der Server vom Installations-Assistenten konfiguriert wird. In diesem Thema wird die *Standardkonfiguration für den einheitlichen Modus* beschrieben, in der eine Berichtsserverinstanz von Setup installiert und konfiguriert wird. Nach Abschluss der Installation wird der Berichtsserver ausgeführt und ist einsatzbereit. Ein Berichtsserver im einheitlichen Modus wird als eigenständiger Anwendungsserver ausgeführt. Der einheitliche Modus ist der standardmäßige Servermodus.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus|  
  
##  <a name="bkmk_top"></a> In diesem Thema  
  
-   [Was ist die Standardkonfiguration?](#bkmk_whatisdefaultconfiguration)  
  
-   [Zeitpunkt der Installation der Standardkonfiguration für den einheitlichen Modus](#bkmk_whentoinstalldefaultconfig)  
  
-   [Anforderungen](#bkmk_requirements)  
  
-   [Standard-URL-Reservierungen](#bkmk_defaultURLreservations)  
  
-   [Installieren des einheitlichen Modus mit der SQL Server-Installations-Assistenten](#bkmk_installwithwizard)  
  
-   [Installieren des einheitlichen Modus über die Befehlszeile](#bkmk_commandline)  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> Was ist die Standardkonfiguration?  
 Beim Setup werden die folgenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen installiert, wenn Sie die Standardkonfiguration für den einheitlichen Modus auswählen:  
  
-   Berichtsserver-Dienst (einschließlich des Berichtsserver-Webdienstes, der Hintergrundverarbeitungsanwendung und des Berichts-Managers)  
  
-   Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager  
  
-   Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Befehlszeilen-Hilfsprogramme (rsconfig.exe, rskeymgmt.exe und rs.exe)  
  
 Diese Option gilt nicht für gemeinsam genutzte Funktionen wie z. B. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], die muss als separate Elemente angegeben werden, wenn Sie sie installieren möchten.  
  
 Setup konfiguriert für die Installation eines Berichtsservers im einheitlichen Modus folgende Elemente:  
  
-   Dienstkonto für den Berichtsserverdienst.  
  
-   URL des Report Server-Webdiensts  
  
-   URL des Berichts-Managers  
  
-   Berichtsserver-Datenbank  
  
-   Dienstkontozugriff auf die Berichtsserver-Datenbanken  
  
-   DSN-Verbindung für die Berichtsserver-Datenbanken  
  
 Setup konfiguriert weder das unbeaufsichtigte Ausführungskonto noch Berichtsserver-E-Mail, Sicherung der Verschlüsselungsschlüssel noch die Bereitstellung für horizontales Skalieren. Sie können diese Eigenschaften mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager konfigurieren. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> Zeitpunkt der Installation der Standardkonfiguration für den einheitlichen Modus  
 Bei der Standardkonfiguration wird [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im Betriebszustand installiert, sodass Sie den Berichtsserver sofort nach Ende des Setups verwenden können. Geben Sie diesen Modus an, wenn Sie nicht alle Schritte ausführen möchten und alle erforderlichen Konfigurationsaufgaben weglassen, die Sie ansonsten im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool ausführen müssten.  
  
 Die Installation der Standardkonfiguration garantiert nicht, dass der Berichtsserver funktioniert, wenn das Setup beendet ist. Es kann sein, dass die Standard-URLs nicht registriert werden, wenn der Dienst gestartet wird. Testen Sie Ihre Installation immer, um zu überprüfen, ob der Dienst erwartungsgemäß gestartet und ausgeführt wird.  
  
##  <a name="bkmk_requirements"></a> Anforderungen  
 Bei der Standardkonfigurationsoption werden die Haupteinstellungen, die für den Betrieb eines Berichtsservers erforderlich sind, mithilfe von Standardwerten konfiguriert. Es bestehen folgende Anforderungen:  
  
-   Ihre Hardware sollte die Mindestanforderungen an die Hardware und Software zum Ausführen von Microsoft SQL Server erfüllen. Weitere Informationen finden Sie unter [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] müssen zusammen in derselben Instanz installiert werden. Die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] hostet die Berichtsserver-Datenbank, die vom Setup erstellt und konfiguriert wurde.  
  
-   Das zur Ausführung des Setups verwendete Benutzerkonto muss Mitglied der lokalen Administratorgruppe sein und die Berechtigung zum Datenbankzugriff sowie zur Datenbankerstellung mithilfe der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz besitzen, die die Berichtsserver-Datenbanken hostet.  
  
-   Setup muss die Standardwerte für die URL-Reservierung verwenden können, mit denen auf den Berichtsserver und den Berichts-Manager zugegriffen wird. Zu diesen Werten gehören Port 80, ein starker Platzhalter und die Namen der virtuellen Verzeichnisse im Format **ReportServer_\<***Instanzname***>** und **Reports\<***_Instanzname***>**.  
  
-   Setup muss die Standardwerte für die Erstellung der Berichtsserver-Datenbanken verwenden können. Diese Werte lauten **ReportServer** und **ReportServerTempDB**. Wenn Sie über bestehende Datenbanken aus einer früheren Installation verfügen, wird das Setup blockiert, weil es den Berichtsserver nicht in der Standardkonfiguration für den einheitlichen Modus konfigurieren kann. Sie müssen die Datenbanken umbenennen, verschieben oder löschen, um die Blockierung des Setups aufzuheben.  
  
 Wenn Ihr Computer nicht alle Anforderungen für eine Standardinstallation erfüllt, müssen Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im Dateimodus installieren und dann den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsmanager verwenden, um nach dem Setup die Konfiguration durchzuführen.  
  
 Versuchen Sie nicht, den Computer neu zu konfigurieren, nur um die Standardinstallation fortsetzen zu können. Dies könnte mehrere Stunden Arbeit bedeuten, was die Zeitersparnis der Installationsoption wieder zunichte machen würde. Die beste Lösung ist zum Installieren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in im Dateimodus und konfigurieren Sie dann auf dem Berichtsserver her, um bestimmte Werte zu verwenden.  
  
##  <a name="bkmk_defaultURLreservations"></a> Standard-URL-Reservierungen  
 URL-Reservierungen bestehen aus Präfix, Hostname, Port und virtuellem Verzeichnis:  
  
|Teil|Description|  
|----------|-----------------|  
|Präfix|Das Standardpräfix ist http. Wenn Sie zuvor ein SSL-Zertifikat (Secure Sockets Layer) installiert haben, versucht das Setup, die URL-Reservierungen mit dem Präfix HTTPS zu erstellen.|  
|Hostname|Der Standardhostname ist ein Platzhalter (+). Es gibt an, dass der Berichtsserver jede HTTP-Anforderung an den angegebenen Port für einen beliebigen Hostnamen, die den Computer akzeptiert, einschließlich http://\<Computername > / Reportserver, http://localhost/reportserver, oder http://\<IP-Adresse > / ReportServer.|  
|Port|Der Standardport ist 80. Hinweis: Wenn Sie einen anderen Port als Port 80 verwenden, müssen Sie diesen ausdrücklich der URL hinzufügen, wenn Sie eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Webanwendung in einem Browserfenster öffnen.|  
|Virtuelles Verzeichnis|Standardmäßig werden virtuelle Verzeichnisse im Format reportserver_ erstellt\<*Instance_name*> für die Berichtsserver-Webdienst und Reports_\<*Instance_name*> für Berichts-Manager. Beim Berichtsserver-Webdienst lautet der Standardname für das virtuelle Verzeichnis **reportserver**. Beim Berichts-Manager lautet der Standardname für das virtuelle Verzeichnis **reports**.|  
  
 Ein Beispiel für die vollständige URL-Zeichenfolge könnte folgendermaßen aussehen:  
  
-   http://+:80/reportserver bietet Zugriff auf den Berichtsserver.  
  
-   http://+:80/reports, bietet Zugriff zum Berichts-Manager.  
  
##  <a name="bkmk_installwithwizard"></a> Installieren des einheitlichen Modus mit der SQL Server-Installations-Assistenten  
 Die folgende Liste beschreibt die  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -spezifischen Schritte und Optionen, die Sie im SQL Server-Installations-Assistenten auswählen. Die Liste beschreibt nicht jede im Installations-Assistenten angezeigte Seite. Es werden nur die auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bezogenen Seiten beschrieben, die Teil einer Installation im einheitlichen Modus sind.  
  
1.  Wählen Sie auf der Seite **Setuprolle** die Option **SQL Server-Funktionsinstallation**aus.  
  
     ![SQL Server-Funktionsinstallation für Setuprolle](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")  
  
2.  Wählen Sie Folgendes auf der Seite **Funktionsauswahl** aus:  
  
    -   
  **Datenbank-Engine-Dienste**, sofern nicht eine Instanz der Datenbank-Engine bereits installiert ist.  
  
    -   **Einheitlicher Modus von Reporting Services**.  
  
    -   **Verwaltungstools – Standard**. Die Verwaltungstools sind nicht erforderlich, sie werden jedoch empfohlen, sofern Sie über keine andere Installation von Verwaltungstools verfügen. Die Standardkonfigurationsoption führt zu einem funktionierenden Berichtsserver, Sie möchten die Konfigurationsoptionen jedoch möglicherweise an einem späteren Datum ändern. Einige Optionen wie 'Meine Berichte' werden über verwaltet. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
     ![Auswahl des einheitlichen SSRS-Modus bei der Funktionsauswahl](../../../2014/sql-server/install/media/rs-setupfeatureselection-native-withcircles.gif "SSRS Native Mode Select in Feature Selection")  
  
3.  Wenn Sie planen, verwenden Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Abonnementfunktion, klicken Sie dann auf die **Serverkonfiguration** , Sie möchten überprüfen, ob für SQL Server-Agent konfiguriert ist **automatische** Starttyp.  
  
4.  Wählen Sie auf der Seite **Reporting Services-Konfiguration** die Option zum **Installieren und Konfigurieren** aus.  
  
     ![SSRS-Konfiguration im einheitlichen Modus](../../../2014/sql-server/install/media/rs-setupconfiguration-native-with-circles.gif "SSRS Native Mode Configuration")  
  
5.  Nachdem der SQL Server-Installations-Assistent abgeschlossen ist, überprüfen Sie die standardmäßige Installation im einheitlichen Modus mithilfe der folgenden Schritte.  
  
    -   Öffnen Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und bestätigen Sie, dass Sie keine Verbindung zum Berichtsserver herstellen können.  
  
    -   Öffnen Sie den Browser mit Administratorprivilegien, und stellen Sie eine Verbindung zum [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichts-Manager her, beispielsweise `http://loclahost/Reports`.  
  
    -   Öffnen Sie den Browser mit Administratorprivilegien, und stellen Sie eine Verbindung zur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserverseite her. Zum Beispiel  `http://loclahost/ReportServer`  
  
 Weitere Informationen finden Sie im Abschnitt über die einheitlichen Modi in den folgenden zwei Themen:  
  
 [Überprüfen einer Installation von Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)  
  
 [Troubleshoot a Reporting Services Installation (Problembehandlung für eine Reporting Services-Installation)](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)  
  
##  <a name="bkmk_commandline"></a> Installieren des einheitlichen Modus über die Befehlszeile  
 Im folgenden Beispiel ist der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Dienst enthalten, da dieser für eine Standardkonfiguration erforderlich ist.  
  
```  
setup /q /ACTION=install /FEATURES=SQL,RS,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS"   
/RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK   
SERVICE" /RSSVCSTARTUPTYPE="Manual" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
 Weitere Informationen und Beispiele finden Sie unter [Command Prompt Installation von Reporting Services SharePoint-Modus und einheitlichen Modus](../../reporting-services/install-windows/install-reporting-services-at-the-command-prompt.md) und [Installieren von SQL Server 2014 über die Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung für eine Reporting Services-Installation](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
 [Überprüfen einer Installation von Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren eine Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Ausschließliche Datei-Installation &#40;Reporting Services&#41;](../../reporting-services/install-windows/files-only-installation-reporting-services.md)   
 [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](../security/configure-ssl-connections-on-a-native-mode-report-server.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Schnellstart-Installation von SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
