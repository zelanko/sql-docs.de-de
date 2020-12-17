---
description: Behandlung von Problemen bei der Installation von Reporting Services
title: Behandlung von Problemen bei der Installation von Reporting Services | Microsoft-Dokumentation
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1cc420302bb8d1610adcc1848fda226c4c55b492
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472471"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Behandlung von Problemen bei der Installation von Reporting Services

  Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aufgrund von Fehlern während der Ausführung von Setup nicht installieren können, können Sie mithilfe der Anweisungen in diesem Artikel die häufigsten Ursachen von Installationsfehlern behandeln.  
  
 Informationen zu anderen Fehlern und Problemen in Bezug auf [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Beheben von SSRS-Problemen und Fehlern](https://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx).  
  
 Lesen Sie online die [Anmerkungen zu dieser Version](https://go.microsoft.com/fwlink/?linkid=236893); das aufgetretene Problem wird möglicherweise dort beschrieben.  
  
##  <a name="check-setup-logs"></a><a name="bkmk_setuplogs"></a> Überprüfen von Setupprotokollen  
 Setupfehler werden in Protokolldateien im Ordner **[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Setup Bootstrap\Log** aufgezeichnet. Wenn Sie Setup ausführen, wird ein Unterordner erstellt. Der Name des Unterordners entspricht dem Datum und der Uhrzeit der Ausführung von Setup. Informationen zum Anzeigen der Setupprotokolldateien finden Sie unter [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
-   Die Protokolldateien enthalten eine Auflistung von Dateien.  
  
-   Öffnen Sie die Datei * _summary.txt, um Informationen über Produkt, Komponente und Instanz anzuzeigen.  
  
-   Öffnen Sie die Datei * _errorlog.txt, um Informationen zu Fehlern während der Ausführung von Setup anzuzeigen.  
  
-   Öffnen Sie *_RS\_\*_ComponentUpdateSetup.log, um Setupinformationen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] anzuzeigen.  
  
##  <a name="check-prerequisites"></a><a name="bkmk_prereq"></a> Überprüfen von Voraussetzungen  
 Die Voraussetzungen werden von Setup automatisch überprüft. Wenn Sie Setupprobleme behandeln möchten, ist es jedoch hilfreich, zu wissen, welche Voraussetzungen von Setup überprüft werden.  
  
-   Zu den Kontoanforderungen für die Ausführung von Setup gehört die Mitgliedschaft in der lokalen Gruppe Administratoren. Setup muss über die Berechtigung zum Hinzufügen von Dateien und Registrierungseinstellungen sowie zum Erstellen von lokalen Sicherheitsgruppen und zum Festlegen von Berechtigungen verfügen. Beim Installieren einer Standardkonfiguration muss das Setup die Berechtigung zum Erstellen einer Berichtsserver-Datenbank auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, auf der die Installation durchgeführt wird, aufweisen.  
  
-   HTTP.SYS 1.1 muss vom Betriebssystem unterstützt werden.  
  
-   Der HTTP-Dienst muss aktiviert sein und ausgeführt werden.  
  
-   Wenn Sie auch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst installieren, ist eine Ausführung von Distributed Transaction Coordinator (DTC) erforderlich.  
  
-   Der Ordner System32 muss die Datei Authz.dll enthalten.  
  
 Setup führt keine Überprüfung für Internet Information Services (IIS) oder [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]mehr durch. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erfordert MDAC 2.0 und [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], Version 2.0. Falls nicht bereits installiert, werden diese Komponenten von Setup installiert.  

::: moniker range="=sql-server-2016"
  
##  <a name="troubleshoot-problems-with-sharepoint-mode-installations"></a><a name="bkmk_tshoot_sharepoint"></a> Problembehandlung von Installationen im SharePoint-Modus  
  
-   [Der Berichtsserver-Konfigurations-Manager wird nicht gestartet](#bkmk_configmanager_notstart)  
  
-   [Nach der Installation von SQL Server 2016 SSRS im SharePoint-Modus wird der SQL Server Reporting Services-Dienst nicht in der SharePoint-Zentraladministration angezeigt.](#bkmk_no_ssrs_service)  
  
-   [PowerShell-Cmdlets für Reporting Services sind nicht verfügbar, und Befehle werden nicht erkannt.](#bkmk_cmdlets_not_recognized)  
  
-   [Sie sehen eine Fehlermeldung, die angibt, dass die URL nicht konfiguriert ist](#bkmk_URL_not_configured)  
  
-   [Setup erzeugt einen Fehler, wenn SharePoint auf einem Computer zwar installiert, aber nicht konfiguriert ist.](#bkmk_sharepoint_not_confiugred)  
  
-   [Die Seite der SharePoint-Zentraladministration ist leer.](#bkmk_central_admin_blank)  
  
-   [Eine Fehlermeldung wird angezeigt, wenn Sie versuchen, einen neuen Bericht mit dem Berichts-Generator zu erstellen.](#bkmk_reportbuilder_newreport_error)  
  
-   [Eine Fehlermeldung wird angezeigt, die besagt, dass RS_SHP nicht mit PREPAREIMAGE unterstützt wird.](#bkmk_RS_SHP_notsupported)  

### <a name="report-server-configuration-manager-does-not-start"></a><a name="bkmk_configmanager_notstart"></a> Der Berichtsserver-Konfigurations-Manager wird nicht gestartet

 **Beschreibung:** Dieses Problem ist ein Merkmal von SQL Server 2012 höher. Reporting Services ist auf die SharePoint-Dienstarchitektur ausgelegt. Zum Konfigurieren und Verwalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird der Konfigurations-Manager nicht mehr benötigt.  
  
 **Problemumgehung:** Verwenden Sie zum Konfigurieren eines Berichtsservers im SharePoint-Modus die SharePoint-Zentraladministration. Weitere Informationen finden Sie unter [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)  
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
###  <a name="you-do-not-see-the-sql-server-reporting-services-service-in-sharepoint-central-administration-after-installing-sql-server-2016-ssrs-in-sharepoint-mode"></a><a name="bkmk_no_ssrs_service"></a> Nach der Installation von SQL Server 2016 SSRS im SharePoint-Modus wird der SQL Server Reporting Services-Dienst nicht in der SharePoint-Zentraladministration angezeigt.  
 **Beschreibung:** Wenn Ihnen nach einer erfolgreichen Installation von SQL Server 2016 Reporting Services im SharePoint-Modus und dem SQL Server 2016 Reporting Services-Add-In für SharePoint 2013/2016 in den folgenden beiden Menüs nicht der Eintrag „SQL Server Reporting Services“ angezeigt wird, wurde der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst nicht registriert:  
  
-   Klicken Sie auf SharePoint 2013/2016-Zentraladministration > „Anwendungsverwaltung“ > Seite „Dienste auf dem Server verwalten“.  
  
-   Menü „SharePoint 2013/2016-Zentraladministration“ -> „Anwendungsverwaltung“ -> „Dienstanwendungen verwalten“ ->“Neu“  
  
 **Problemumgehung:** Um die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services zu registrieren und zu starten, führen Sie folgende Schritte aus:  
  
1.  Auf dem Computer, auf dem SharePoint 2013/2016-Zentraladministration ausgeführt wird  
  
    1.  Öffnen Sie die SharePoint 2013/2016-Verwaltungsshell mit Administratorberechtigungen. Klicken Sie mit der rechten Maustaste auf das Symbol, und klicken Sie auf **Als Administrator ausführen**. Führen Sie die folgenden drei Cmdlets von der Shell aus:  
  
    2.  ```  
        Install-SPRSService  
        ```  
  
    3.  ```  
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```  
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  Überprüfen Sie, ob der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienst auf der Seite als **Gestartet** angezeigt wird: SharePoint 2013/2016-Zentraladministration -> **Anwendungsverwaltung** -> **Dienste auf dem Server verwalten**  
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
###  <a name="reporting-services-powershell-cmdlets-are-not-available-and-commands-are-not-recognized"></a><a name="bkmk_cmdlets_not_recognized"></a> PowerShell-Cmdlets für Reporting Services sind nicht verfügbar, und Befehle werden nicht erkannt.  
 **Beschreibung:** Wenn Sie versuchen, ein [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-PowerShell-Cmdlet auszuführen, wird eine Fehlermeldung mit etwa folgendem Wortlaut angezeigt:  
  
-   Der Begriff „Install-SPRSServiceInstall-SPRSService“ wurde **nicht** als Name eines Cmdlets, einer Funktion, einer Skriptdatei oder eines ausführbaren Programms erkannt. Prüfen Sie die Schreibweise des Namens bzw. stellen Sie sicher, dass der Pfad korrekt angegeben wurde, und versuchen Sie es erneut. In Zeile: 1 Zeichen:39+ Install-SPRSServiceInstall-SPRSService <<<<    + CategoryInfo          : ObjectNotFound: (Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **Problemumgehung:** Führen Sie eine der folgenden Aktionen aus:  
  
-   Führen Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte aus. **rssharepoint.msi**.  
  
-   Installieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus von den SQL Server-Installationsmedien.  
  
 Wenn die **SharePoint 2013/2016-Verwaltungsshell** beim Ausführen einer dieser Problemumgehungen geöffnet ist, schließen Sie diese, und öffnen Sie sie erneut.  
  
 Weitere Informationen finden Sie in den folgenden Artikeln:  
  
-   [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Installieren des ersten Berichtsservers im SharePoint-Modus](install-the-first-report-server-in-sharepoint-mode.md)  
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
###  <a name="you-see-an-error-message-indicating-the-url-is-not-configured"></a><a name="bkmk_URL_not_configured"></a> Sie sehen eine Fehlermeldung, die angibt, dass die URL nicht konfiguriert ist  
 **Beschreibung:** Sie erhalten eine ähnliche Fehlermeldung wie diese:  
  
 Diese SQL Server Reporting Services (SSRS)-Funktionalität wird nicht unterstützt. Verwenden Sie Zentraladministration, um eines oder mehrere der folgenden Probleme zu überprüfen und zu korrigieren:
 
 - Eine Berichtsserver-URL ist nicht konfiguriert. Verwenden Sie die SSRS-Integration-Seite zu ihrer Festlegung.
 
 - Der SSRS-Dienstanwendungsproxy ist nicht konfiguriert. Verwenden Sie die SSRS-Dienstanwendungsseiten, um den Proxy zu konfigurieren.
 
 - Die SSRS-Dienstanwendung ist nicht dieser Webanwendung zugeordnet. Verwenden Sie, die SSRS-Dienstanwendungsseiten, um den Proxy der SSRS-Dienstanwendung der Anwendungsproxygruppe dieser Webanwendung zuzuordnen. 
  
 **Problemumgehung:** Die Fehlermeldung enthält drei vorgeschlagene Schritte, um dieses Problem zu beheben. Der erste Vorschlag in der Meldung „Es wurde keine Berichtsserver-URL konfiguriert.“ spielt bei der Integration der früheren Version des Berichtsservers in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eine wichtige Rolle. Die SharePoint-Konfiguration für die vorherigen Berichtsserverversionen wird auf der Seite **Allgemeine Anwendungseinstellungen** abgeschlossen und verwendet **SQL Server Reporting Services (2008 und 2008 R2)**.  
  
 **Weitere Informationen:** Diese Fehlermeldung wird beim Versuch angezeigt, eine der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen zu verwenden, die eine Verbindung zum [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst erfordern. Dies schließt Folgendes ein:  
  
-   Öffnen von SQL Server-Berichts-Generator von einer SharePoint-Dokumentbibliothek.  
  
-   Verwalten von Abonnements.  
  
-   Verwalten einer Dienstanwendung.  
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
###  <a name="setup-fails-on-a-computer-with-sharepoint-installed-but-it-is-not-configured"></a><a name="bkmk_sharepoint_not_confiugred"></a> Setup erzeugt einen Fehler, wenn SharePoint auf einem Computer zwar installiert, aber nicht konfiguriert ist.  
 **Beschreibung:** Wenn Sie auswählen, Reporting Services SharePoint-Modus auf einem Computer zu installieren, auf dem SharePoint installiert, aber nicht konfiguriert ist, sehen Sie eine Meldung ähnlich der folgenden, und Setup wird angehalten:  
  
 SQL Server-Setup wird nicht mehr ausgeführt.  
  
 **Problemumgehung:** Konfigurieren Sie SharePoint, und führen Sie dann die SQL Server-Installation aus.  
  
 **Weitere Informationen:** Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine vorhandene SharePoint-Installation installieren, versucht Setup, den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -SharePoint-Dienst zu installieren und zu starten. Wenn SharePoint nicht konfiguriert ist, schlägt die Dienstinstallation fehl, sodass Setup fehlschlägt.  
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
###  <a name="sharepoint-central-administration-page-is-blank"></a><a name="bkmk_central_admin_blank"></a> Die Seite der SharePoint-Zentraladministration ist leer.  
 **Beschreibung:** Sie konnten SharePoint 2013/2016 ohne Installationsfehler erfolgreich installieren. Wenn Sie jedoch zur Zentraladministration wechseln, sehen Sie nur eine leere Seite:  
  
 **Problemumgehung:** Dieses Problem ist nicht typisch für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , bezieht sich jedoch auf die Konfiguration von Berechtigungen in der gesamten SharePoint-Installation. Hier sehen Sie einige Vorschläge:  
  
-   Sehen Sie sich den SharePoint-Artikel zu Entwicklungsumgebungen an. [Einrichten einer allgemeinen Entwicklungsumgebung für SharePoint](/sharepoint/dev/general-development/set-up-a-general-development-environment-for-sharepoint)  
  
-   Lesen Sie den Forumsbeitrag: [Die Zentraladministration gibt nach der Installation unter Windows 7 eine leere Seite zurück](https://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   Das Dienstkonto, das Sie für SharePoint-Dienste verwenden, z.B. der SharePoint 2013/2016-Zentraladministrationsdienst, sollte im lokalen Betriebssystem Administratorprivilegien haben.  
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
###  <a name="you-see-an-error-message-when-you-try-to-create-a-new-report-builder-report"></a><a name="bkmk_reportbuilder_newreport_error"></a> Eine Fehlermeldung wird angezeigt, wenn Sie versuchen, einen neuen Bericht mit dem Berichts-Generator zu erstellen.  
 **Beschreibung:** Sie sehen eine Fehlermeldung ähnlich der folgenden, wenn Sie versuchen, in einer Dokumentbibliothek einen Bericht mit dem Berichts-Generator zu erstellen:  
  
 Diese Funktionalität wird nicht unterstützt, da eine SQL Server Reporting Services-Dienstanwendung nicht vorhanden ist, oder eine Berichtsserver-URL wurde nicht in der Zentraladministration konfiguriert.  
  
 **Problemumgehung:** Überprüfen Sie, ob eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung vorhanden und ordnungsgemäß konfiguriert ist. Weitere Informationen finden Sie unter [Installieren des ersten Berichtsservers im SharePoint-Modus](install-the-first-report-server-in-sharepoint-mode.md).
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  
  
###  <a name="you-see-an-error-message-that-rs_shp-is-not-supported-with-prepareimage"></a><a name="bkmk_RS_SHP_notsupported"></a> Eine Fehlermeldung wird angezeigt, die besagt, dass RS_SHP nicht mit PREPAREIMAGE unterstützt wird.  
 **Beschreibung:** Wenn Sie versuchen, PREPAREIMAGE für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auszuführen, wird eine Fehlermeldung ähnlich der folgenden angezeigt:  
  
 „Beim Ausführen der PREPAREIMAGE-Aktion wird die angegebene Funktion „RS_SHP“ nicht unterstützt, da sie SysPrep nicht unterstützt. Entfernen Sie die Funktionen, die nicht mit SysPrep kompatibel sind, und führen Sie das Setup erneut aus.“  
  
 **Problemumgehung:** Es gibt keine Problemumgehung. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt SYSPREP (PREPAREIMAGE) nicht. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt SYSPREP.  
  
 ![Pfeilsymbol mit Rückverweis auf den Seitenanfang](/analysis-services/analysis-services/instances/media/uparrow16x16.gif "Pfeilsymbol, das mit dem Link „Zurück zum Anfang“ verwendet wird") [Beheben von Problemen bei Installationen im SharePoint-Modus](#bkmk_tshoot_sharepoint)  

::: moniker-end
  
##  <a name="troubleshoot-problems-with-the-native-mode-installations"></a><a name="bkmk_tshoot_native"></a> Behandeln von Problemen bei Installationen im einheitlichen Modus  
  
###  <a name="performance-counters-are-not-visible-after-upgrading-to-windows-vista-or-windows-server-2008"></a><a name="PerfCounters"></a> Nach dem Upgrade auf Windows Vista oder Windows Server 2008 werden keine Leistungsindikatoren angezeigt.  
 Wenn Sie auf einem Computer mit [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] ein Upgrade des Betriebssystems auf [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]vornehmen, werden die Leistungsindikatoren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nach dem Upgrade nicht festgelegt.  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>So stellen Sie die Leistungsindikatoren von Reporting Services wieder her  
  
1.  Löschen Sie die folgenden Registrierungsschlüssel:  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2016 Windows Service**  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster, und geben Sie den folgenden Befehl ein:  
  
    -   **run \<** *.NET 4.0 Framework directory* **>\InstallUtil.exe \<** *Report Server Bin directory* **>\ReportingServicesLibrary.dll**  
  
        > [!NOTE]  
        >  Ersetzen Sie \<*.NET 4.0 Framework directory*> durch den physischen Pfad der .NET Framework 4.0-Dateien und \<*Report Server Bin directory*> durch den physischen Pfad der Berichtsserver-Binärdateien.  
  
3.  Starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst neu.  
  
 Überprüfen Sie, ob die Schritte erfolgreich ausgeführt wurden, indem Sie einen Webbrowser aufrufen und auf die URLs des Webportals oder des Berichtsservers navigieren. Öffnen Sie anschließend den Systemmonitor, um sicherzustellen, dass die Indikatoren funktionieren.  
  
#### <a name="to-add-the-performance-registry-keys-again-by-using-registry-editor"></a>So fügen Sie die Leistungsregistrierungsschlüssel mit dem Registrierungs-Editor erneut hinzu  
  
1.  Öffnen Sie den Registrierungs-Editor:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  Geben Sie im Dialogfeld **Ausführen** im Feld **Öffnen** den Befehl **regedit** ein.  
  
2.  Wählen Sie im Registrierungs-Editor den folgenden Registrierungsschlüssel aus: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance`  
  
3.  Klicken Sie mit der rechten Maustaste auf den Knoten **Performance** , zeigen Sie auf **Neu**, und klicken Sie auf **Wert der mehrteiligen Zeichenfolge**.  
  
4.  Geben Sie **Counter Names** ein, und drücken Sie dann die EINGABETASTE.  
  
5.  Wiederholen Sie den Vorgang, um in diesem Knoten den Registrierungsschlüssel **Counter Types** hinzuzufügen.  
  
6.  Navigieren Sie zu folgendem Registrierungsschlüssel: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance`  
  
7.  Klicken Sie mit der rechten Maustaste auf den Knoten **Performance** , zeigen Sie auf **Neu**, und klicken Sie auf **Wert der mehrteiligen Zeichenfolge**.  
  
8.  Geben Sie **Counter Names** ein, und drücken Sie dann die EINGABETASTE.  
  
9. Wiederholen Sie den Vorgang, um in diesem Knoten den Registrierungsschlüssel **Counter Types** hinzuzufügen.  
  
 Nachdem Sie die 64-Bit-Instanz repariert oder die Registrierungsschlüssel manuell erneut hinzugefügt haben, können Sie mit dem Systemmonitor die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Leistungsobjekte konfigurieren, die Sie überwachen möchten.  
  
###  <a name="reportserverexternalurl-and-passthroughcookies-configuration-properties-are-not-configured-after-an-upgrade-from-sql-server-2005"></a><a name="ConfigPropsMissing"></a> Nach einem Upgrade von SQL Server 2005 sind die "ReportServerExternalURL"-Konfigurationseigenschaft und die "PassThroughCookies"-Konfigurationseigenschaft nicht konfiguriert.  
 Beim Aktualisieren von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], werden die Konfigurationseigenschaften **ReportServerExternalURL** und **PassThroughCookies** nicht durch den Aktualisierungsvorgang konfiguriert. **ReportServerExternalURL** ist eine optionale Eigenschaft und sollte nur dann festgelegt werden, wenn Sie SharePoint 2.0 Webparts verwenden und möchten, dass Benutzer einen Bericht abrufen und in einem neuen Browserfenster öffnen können. Weitere Informationen zu **ReportServerExternalURL** finden Sie unter [URLs in Configuration Files (Report Server Configuration Manager)](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) (URLs in Konfigurationsdateien &#40;Berichtsserver-Konfigurations-Manager&#41;). **PassThroughCookies** ist nur beim Verwenden der benutzerdefinierten Authentifizierungsmethode erforderlich. Weitere Informationen zu **PassThroughCookies** finden Sie unter [Konfigurieren des Weportals für die Übergabe von benutzerdefinierten Authentifizierungscookies](../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
> [!NOTE]  
>  Wenn Sie benutzerdefinierte Authentifizierung verwenden, wird empfohlen, die Installation zu migrieren, statt ein Upgrade durchzuführen. Weitere Informationen zur Migration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Migrate a Reporting Services Installation (Native Mode) (Migrieren einer Installation von Reporting Services (einheitlicher Modus))](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
 Standardmäßig sind diese Eigenschaften in der [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Konfiguration nicht vorhanden. Wenn Sie diese Eigenschaften in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] konfiguriert haben und die von ihnen bereitgestellte Funktionalität weiterhin benötigen, müssen Sie sie nach dem Upgrade manuell der Datei **RSReportServer.config** hinzufügen. Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  

### <a name="401-unauthorized-error-when-using-windows-authentication-after-an-upgrade-from-sql-server-2005-to-sql-server-2016"></a><a name="WindowsAuthBreaksAfterUpgrade"></a> Fehler 401 „Nicht autorisiert“ bei Verwendung der Windows-Authentifizierung nach einem Upgrade von SQL Server 2005 auf SQL Server 2016

 Wenn Sie ein Upgrade von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] durchführen und für das Berichtsserver-Dienstkonto die NTLM-Authentifizierung mit einem integrierten Konto verwenden, tritt nach dem Upgrade beim Zugriff auf das Webportal oder den Berichtsserver möglicherweise der Fehler „401 – Nicht autorisiert“ auf.  
  
 Sie sehen diese Meldung aufgrund einer Änderung in der [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]-Standardkonfiguration für Windows-Authentifizierung. In der Konfiguration ist Aushandeln festgelegt, wenn es sich bei dem Berichtsserver-Dienstkonto um einen Netzwerkdienst oder ein lokales System handelt. In der Konfiguration ist NTLM festgelegt, wenn es sich bei dem Berichtsserver-Dienstkonto um keines dieser integrierten Konten handelt. Um das Problem nach dem Upgrade zu beheben, können Sie die Datei „RSReportServer.config“ bearbeiten und **AuthentificationType** als **RSWindowsNTLM** konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der Windows-Authentifizierung für den Berichtsserver](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).  

### <a name="uninstalling-32-bit-instance-of-sql-server-2016-reporting-services-in-side-by-side-deployment-with-a-64-bit-instance-breaks-the-64-bit-instance"></a><a name="Uninstall32BitBreaks64Bit"></a> Durch das Deinstallieren einer 32-Bit-Instanz von SQL Server 2016 Reporting Services in einer parallelen Bereitstellung mit einer 64-Bit-Instanz wird die 64-Bit-Instanz beschädigt.

 Wenn Sie eine 32-Bit-Instanz und eine 64-Bit-Instanz von [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] parallel auf einem Computer installieren und die 32-Bit-Instanz deinstallieren, werden vier [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Registrierungsschlüssel entfernt. Hierdurch wird die 64-Bit-Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] beschädigt. Beim Deinstallieren der 32-Bit-Instanz werden die folgenden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Registrierungsschlüssel entfernt:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2016 Windows Service\Performance:Counter Types`  
  
 Um dieses Problem zu beheben, können Sie die 64-Bit-Instanz reparieren. Zwar wird empfohlen, die Reparatur auszuführen, Sie können jedoch mithilfe des Registrierungs-Editors die Registrierungsschlüssel manuell erneut hinzufügen.  
  
> [!CAUTION]  
>  Ein fehlerhaftes Bearbeiten der Registrierung kann eine schwerwiegende Beschädigung des Systems zur Folge haben. Bevor Sie Änderungen an der Registrierung vornehmen, sollten Sie alle wichtigen Computerdaten sichern.  
  
##  <a name="additional-resources"></a><a name="bkmk_additional"></a> Weiterführende Artikel  
 Zur Unterstützung bei der Problembehandlung können Sie zusätzlich folgende Ressourcen überprüfen:  
  
-   TechNet Wiki: [Troubleshoot SQL Server Reporting Services (SSRS) in SharePoint 2010 Integrated Mode (Problembehandlung bei SQL Server Reporting Services im integrierten SharePoint 2010-Modus)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [Microsoft – Fragen und Antworten: SQL Server Reporting Services](/answers/topics/sql-server-reporting-services.html)  
  
-   Haben Sie weitere Fragen oder Feedback? Besuchen Sie [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server).  
  
