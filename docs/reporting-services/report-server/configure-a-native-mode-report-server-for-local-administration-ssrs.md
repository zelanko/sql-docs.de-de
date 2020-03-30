---
title: Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung | Microsoft-Dokumentation
ms.date: 05/28/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 535284c89f54fb39f448a71e5484e81c1a9d31af
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "77080892"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a>Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung (SSRS)
  Für die Bereitstellung eines [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsservers unter einem der folgenden Betriebssysteme sind weitere Konfigurationsschritte erforderlich, wenn die Berichtsserverinstanz lokal verwaltet werden soll. In diesem Thema wird beschrieben, wie der Berichtsserver für die lokale Verwaltung konfiguriert wird. Wenn Sie den Berichtsserver noch nicht installiert oder konfiguriert haben, lesen Sie [Installieren von SQL Server über den Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) und [Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 Da Berechtigungen durch die angegebenen Betriebssysteme beschränkt werden, führen Mitglieder der lokalen Gruppe Administratoren die meisten Anwendungen auf die gleiche Weise wie bei der Verwendung des Standardbenutzerkontos aus.  
  
 Dieses Verfahren verbessert zwar die allgemeine Sicherheit des Systems, verhindert jedoch, dass Sie die vordefinierten integrierten Rollenzuweisungen verwenden, die von Reporting Services für lokale Administratoren erstellt werden.  
  
-   [Übersicht der Konfigurationsänderungen](#bkmk_configuraiton_overview)  
  
-   [So konfigurieren Sie den lokalen Berichtsserver und die Webportalverwaltung](#bkmk_configure_local_server)  
  
-   [So konfigurieren Sie SQL Server Management Studio (SSMS) für die lokale Verwaltung des Berichtsservers](#bkmk_configure_ssms)  
  
-   [So konfigurieren Sie SQL Server Data Tools (SSDT) für die Veröffentlichung auf einem lokalen Berichtsserver](#bkmk_configure_ssdt)  
  
-   [Weitere Informationen](#bkmk_addiitonal_informaiton)  
  
##  <a name="overview-of-configuration-changes"></a><a name="bkmk_configuraiton_overview"></a> Übersicht der Konfigurationsänderungen  
 Durch die folgenden Konfigurationsänderungen wird der Server so konfiguriert, dass Berichtsserverinhalte und -vorgänge mit Standardbenutzerberechtigungen verwaltet werden können:  
  
-   Fügen Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -URLs zu vertrauenswürdigen Websites hinzu. Internet Explorer wird unter den aufgelisteten Betriebssystemen standardmäßig im **geschützten Modus**ausgeführt. Diese Funktion verhindert, dass Browseranforderungen Prozesse auf hoher Ebene erreichen, die auf demselben Computer ausgeführt werden. Sie können den geschützten Modus für die Berichtsserveranwendungen deaktivieren, indem Sie sie als vertrauenswürdige Sites hinzufügen.  
  
-   Erstellen Sie Rollenzuweisungen, die Ihnen als Berichtsserveradministrator die Berechtigung zur Verwaltung von Inhalt und Vorgängen verleihen, ohne die Funktion **Als Administrator ausführen** in Internet Explorer verwenden zu müssen. Durch das Erstellen von Rollenzuweisungen für Ihr Windows-Benutzerkonto erhalten Sie Zugriff auf einen Berichtsserver mit Inhalts-Manager- und Systemadministratorberechtigungen durch explizite Rollenzuweisungen, die die vordefinierten, integrierten Rollenzuweisungen ersetzen, die von Reporting Services erstellt werden.  
  
##  <a name="to-configure-local-report-server-and-web-portal-administration"></a><a name="bkmk_configure_local_server"></a> So konfigurieren Sie den lokalen Berichtsserver und die Webportalverwaltung  
 Führen Sie die Konfigurationsschritte in diesem Abschnitt aus, wenn beim Navigieren zu einem lokalen Berichtsserver eine mit der folgenden vergleichbare Fehlermeldung angezeigt wird:  
  
-   Der Benutzer `'Domain\[user name]`' verfügt nicht über die erforderlichen Berechtigungen. Stellen Sie sicher, dass ausreichende Berechtigungen erteilt und die Einschränkungen der Windows-Benutzerkontensteuerung (UAC) behandelt wurden.  
  
###  <a name="trusted-site-settings-in-the-browser"></a><a name="bkmk_site_settings"></a> Browsereinstellungen für vertrauenswürdige Sites  
  
1.  Öffnen Sie ein Browserfenster mit "Als Administrator ausführen"-Berechtigungen. Klicken Sie im Menü **Start** mit der rechten Maustaste auf **Internet Explorer**, und wählen Sie dann **Als Administrator ausführen** aus.  
  
2.  Wählen Sie **Ja** aus, wenn Sie dazu aufgefordert werden, um den Vorgang fortzusetzen.  
  
3.  Geben Sie in der URL-Adresse die Webportal-URL ein. Anleitungen finden Sie unter [Webportal eines Berichtsservers &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
4.  Klicken Sie auf **Extras**.  
  
5.  Klicken Sie auf **Internetoptionen**.  
  
6.  Klicken Sie auf **Sicherheit**.  
  
7.  Klicken Sie auf **Vertrauenswürdige Sites**.  
  
8.  Klicken Sie auf **Websites**.  
  
9. Fügen Sie `https://<your-server-name>`hinzu.  
  
10. Deaktivieren Sie das Kontrollkästchen **Für Sites dieser Zone ist eine Serverüberprüfung (https:) erforderlich** , falls Sie HTTPS nicht für die Standardwebsite verwenden.  
  
11. Klicken Sie auf **Hinzufügen**.  
  
12. Klicken Sie auf **OK**.  
  
###  <a name="web-portal-folder-settings"></a><a name="bkmk_configure_folder_settings"></a> Ordnereinstellungen des Webportals  
  
1.  Klicken Sie im Webportal auf der Startseite auf **Ordner verwalten**.  
  
2.  Klicken Sie auf Ordnerseite **Verwalten** auf **Sicherheit**, und wählen Sie dann **Gruppe oder Benutzer hinzufügen** aus.  
  
3.  Geben Sie auf der Seite **Neue Rollenzuweisung** im Feld **Gruppe oder Benutzer** Ihr Windows-Benutzerkonto im folgenden Format ein: `<domain>\<user>`.  
  
5.  Wählen Sie **Inhalts-Manager**aus.  
  
6.  Klicken Sie auf **OK**.  
  
###  <a name="web-portal-site-settings"></a><a name="bkmk_configure_site_settings"></a> Siteeinstellungen des Webportals  
  
1.  Öffnen Sie den Browser mit Administratorprivilegien, und navigieren Sie zum Webportal (`https://<server name>/reports`).  
  
2.  Wählen Sie das Zahnradsymbol in der obersten Zeile der Startseite aus, und klicken Sie dann im Dropdownmenü auf **Siteeinstellungen**. 
  
    ![Zahnradsymbol](../media/ssrsgearmenu.png)erforderlich.
    >[!TIP]  
    >**Hinweis:** Wenn die Option **Siteeinstellungen** nicht angezeigt wird, schließen Sie den Browser, öffnen Sie ihn mit Administratorberechtigungen erneut, und navigieren Sie zum Webportal.  
  
3.  Wählen Sie auf der Seite „Siteeinstellungen“ die Option **Sicherheit** aus, und wählen Sie dann **Gruppe oder Benutzer hinzufügen** aus.  
  
4.  Geben Sie im Feld **Gruppen- oder Benutzername** Ihr Windows-Benutzerkonto im folgenden Format ein: `<domain>\<user>`.  

5.  Wählen Sie **Systemadministrator**aus.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Schließen Sie das Webportal.  
  
8. Öffnen Sie das Webportal in Internet Explorer erneut, ohne **Als Administrator ausführen**zu verwenden.  
  
##  <a name="to-configure-sql-server-management-studio-ssms-for-local-report-server-administration"></a><a name="bkmk_configure_ssms"></a> So konfigurieren Sie SQL Server Management Studio (SSMS) für die lokale Verwaltung des Berichtsservers  
 Standardmäßig ist es nur möglich, auf alle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügbaren Berichtsservereigenschaften zuzugreifen, wenn Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] mit Administratorprivilegien starten.  
  
 **So konfigurieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** , sodass [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] nicht jedes Mal mit erweiterten Berechtigungen gestartet werden muss:  
  
-   Klicken Sie im Menü **Start** mit der rechten Maustaste auf **Microsoft SQL Server[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]** , und klicken Sie dann auf **Als Administrator ausführen**.  
  
-   Stellen Sie eine Verbindung mit dem lokalen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Server her.  
  
-   Klicken Sie im Knoten **Sicherheit** auf **Systemrollen**.  
  
-   Klicken Sie mit der rechten Maustaste auf **Systemadministrator** , und klicken Sie anschließend auf **Eigenschaften**.  
  
-   Wählen Sie auf der Seite **Systemrolleneigenschaften** die Option **Berichtsservereigenschaften anzeigen**aus. Wählen Sie weitere Eigenschaften aus, die Sie Mitgliedern der Systemadministratorrolle zuordnen möchten.  
  
-   Klicken Sie auf **OK**.  
  
-   Schließen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Informationen zum Hinzufügen eines Benutzers zur Systemrolle „Systemadministrator“ finden Sie im Abschnitt [Siteeinstellungen des Webportals](#bkmk_configure_site_settings) weiter oben in diesem Artikel.  
  
 Wenn Sie jetzt [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] öffnen und nicht explizit **Als Administrator ausführen** auswählen, haben Sie Zugriff auf die Berichtsservereigenschaften.  
  
##  <a name="to-configure-sql-server-data-tools-ssdt-to-publish-to-a-local-report-server"></a><a name="bkmk_configure_ssdt"></a> So konfigurieren Sie SQL Server Data Tools (SSDT) für die Veröffentlichung auf einem lokalen Berichtsserver  
 Wenn Sie [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] unter einem der im ersten Abschnitt dieses Themas aufgeführten Betriebssysteme installiert haben und SSDT mit einem lokalen Berichtsserver im einheitlichen Modus interagieren soll, treten Berechtigungsfehler auf, sofern Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nicht mit erweiterten Berechtigungen öffnen oder Reporting Services-Rollen konfigurieren. Wenn Sie nicht über ausreichende Berechtigungen verfügen, können z. B. folgende Probleme auftreten:  
  
-   Beim Versuch, Berichtselemente auf dem lokalen Berichtsserver bereitzustellen, wird im Fenster **Fehlerliste** eine Fehlermeldung wie die folgende angezeigt:  
  
    -   Die dem Benutzer „Domain\\<Benutzername\>“ erteilten Berechtigungen reichen zum Ausführen des Vorgangs nicht aus.  
  
 **So verwenden Sie bei jedem Öffnen von SSDT erweiterte Berechtigungen**  
  
1.  Wählen Sie im Startmenü **Microsoft SQL Server** aus, und klicken Sie anschließend mit der rechten Maustaste auf **SQL Server Data Tools**. Klicken Sie auf **Als Administrator ausführen**.  
  
2.  Wählen Sie **Ja** aus, wenn Sie dazu aufgefordert werden, um den Vorgang fortzusetzen.  
  
Sie können jetzt Berichte und andere Elemente auf einem lokalen Berichtsserver bereitstellen.  
  
 **So konfigurieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Rollenzuweisungen, damit SSDT nicht jedes Mal mit erweiterten Berechtigungen gestartet werden muss**  
  
-   Weitere Informationen finden Sie in den Abschnitten [Ordnereinstellungen des Webportals](#bkmk_configure_folder_settings) und [Siteeinstellungen des Webportals](#bkmk_configure_site_settings) weiter oben in diesem Thema.  
  
##  <a name="additional-information"></a><a name="bkmk_addiitonal_informaiton"></a> Zusätzliche Informationen  
 Ein weiterer häufiger Konfigurationsschritt in Verbindung mit der Verwaltung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] besteht darin, Port 80 in der Windows-Firewall zu öffnen, um den Zugriff auf den Berichtsservercomputer zu ermöglichen. Anweisungen finden Sie unter [Configure a Firewall for Report Server Access](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Manage a Reporting Services Native Mode Report Server (Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus)](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
