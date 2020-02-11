---
title: Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung (SSRS-Configuration Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c2e34258f10033c61f9966e62fa7c14025423613
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952335"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a>Konfigurieren eines Berichtsservers für die E-Mail-Übermittlung (SSRS-Konfigurations-Manager)


  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält eine Erweiterung zur E-Mail-Übermittlung, damit Sie Berichte per E-Mail verteilen können. Je nachdem, wie Sie das Abonnieren von E-Mails definieren, kann eine E-Mail-Übermittlung aus einer Nachricht, einem Link, einem Anhang oder einem eingebetteten Bericht bestehen. Die Erweiterung der E-Mail-Übermittlung arbeitet mit Ihrer vorhandenen E-Mail-Server-Technologie. Der E-Mail-Server muss ein SMTP-Server oder eine Weiterleitung sein. Der Berichtsserver stellt über CDO-Bibliotheken (Collaboration Data Objects, cdosys.dll), die das Betriebssystem stellt, eine Verbindung zu einem SMTP-Server her.  
  
 Die E-Mail-Übermittlungserweiterung des Berichtsservers ist standardmäßig nicht konfiguriert. Sie müssen den Reporting Services-Konfigurations-Manager verwenden, um die Erweiterung minimal zu konfigurieren. Sie müssen die Datei `RSReportServer.config` bearbeiten, um die erweiterten Eigenschaften festzulegen. Wenn Sie den Berichtsserver für die Verwendung dieser Erweiterung nicht konfigurieren können, können Sie stattdessen Berichte an einen freigegebenen Ordner übermitteln. Weitere Informationen finden Sie unter [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus|  
  
 
  
##  <a name="bkmk_configuration_requirements"></a>Konfigurations Anforderungen  
  
-   Die E-Mail-Übermittlung des Berichtsservers wird über Collaboration Data Objects (CDO) implementiert und erfordert einen SMTP-Remoteserver oder einen lokalen SMTP-Server (Simple Mail Transfer Protocol) bzw. eine SMTP-Weiterleitung. SMTP wird nicht von allen Windows-Betriebssystemen unterstützt. Wenn Sie die Itanium-basierte Edition von Windows Server 2008 verwenden, wird SMTP nicht unterstützt. Weitere Informationen zu den Konfigurationsoptionen von CDO finden Sie unter [Configuration CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) auf MSDN.  
  
-   Das Berichtsserver-Dienstkonto muss auf dem SMTP-Server berechtigt sein, E-Mails zu senden.  
  
-   Für die Erweiterung der E-Mail-Übermittlung wird in E-Mail-Anlagen die UTF-8-Codierung verwendet. Die Codierung kann nicht geändert werden. Die HTML-Renderingerweiterung unterstützt ausschließlich UTF-8.  
  
> [!NOTE]  
>  Die standardmäßige E-Mail-Übermittlungserweiterung bietet keine Unterstützung für digitale Signaturen oder für die Verschlüsselung ausgehender E-Mail-Nachrichten.  
  
 
  
##  <a name="bkmk_configure_for_local_or_remote_SMTP"></a>Konfigurieren eines Berichts Servers für einen lokalen oder Remote-SMTP-Dienst  
 Zur Unterstützung der E-Mail-Übermittlung können Sie einen lokalen SMTP-Dienst oder einen SMTP-Remoteserver bzw. eine SMTP-Weiterleitung verwenden. Wenn Sie auf einen vorhandenen SMTP-Remoteserver zugreifen können, sollten Sie ihn verwenden. Wenn kein SMTP-Server verfügbar ist oder wenn zu einem späteren Zeitpunkt Berichtsübermittlungsfehler auftreten, die auf Fehler bei der Computerverbindung zurückzuführen sind, sollten Sie stattdessen einen lokalen SMTP-Dienst verwenden. Informationen zum Konfigurieren eines Berichtsservers für lokale Dienste und Remotedienste finden Sie weiter unten in diesem Thema.  
  
  
  
##  <a name="bkmk_setting_email_delivery"></a>Festlegen von Konfigurationsoptionen für e-Mail-Übermittlung  
 Bevor Sie die E-Mail-Übermittlung des Berichtsservers verwenden können, müssen Sie Konfigurationswerte festlegen, die angeben, welcher SMTP-Server verwendet werden soll.  
  
 Gehen Sie wie folgt vor, um einen Berichtsserver für die E-Mail-Übermittlung zu konfigurieren:  
  
-   Verwenden Sie den Reporting Services-Konfigurations-Manager, wenn Sie nur einen SMTP-Server und ein Benutzerkonto angeben, das über die Berechtigung zum Senden von E-Mail verfügt. Dies sind die zum Konfigurieren der E-Mail-Übermittlungserweiterung für einen Berichtsserver erforderlichen Mindesteinstellungen. Weitere Informationen finden Sie unter [e-Mail-Einstellungen-Configuration Manager &#40;SSRS im einheitlichen Modus&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) und [e-Mail-Übermittlung in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   (Optional) Verwenden Sie einen Text-Editor, um zusätzliche Einstellungen in der Datei RSreportserver.config anzugeben. Diese Datei enthält alle Konfigurationseinstellungen für die Berichtsserver-E-Mail-Übermittlung. Wenn Sie einen lokalen SMTP-Server verwenden oder die E-Mail-Übermittlung auf bestimmte Hosts beschränken, müssen Sie zusätzliche Einstellungen in diesen Dateien angeben. Weitere Informationen zum Suchen und Ändern von Konfigurationsdateien finden Sie unter [Ändern einer Reporting Services Konfigurationsdatei &#40;RSReportServer. config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) in SQL Server-Onlinedokumentation.  
  
> [!NOTE]  
>  E-Mail-Einstellungen für den Berichtsserver basieren auf CDO (Collaboration Data Objects). Ausführlichere Informationen zu bestimmten Einstellungen finden Sie in der CDO-Produktdokumentation.  
  

  
##  <a name="bkmk_example_config_file"></a>Beispiel für eine e-Mail-Konfiguration  
 Das folgende Beispiel veranschaulicht die Einstellungen für einen SMTP-Remoteserver in der Datei RSreportserver.config. Informationen zu Ein derstellungsbeschreibungen und gültigen Werten fin derden Sie unter [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onlin dere or the CDO product documentation.  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="bkmk_setting_TO_field"></a>Konfigurationsoptionen zum Festlegen des Felds an: in einer Nachricht  
 Benutzerdefinierte Abonnements, die gemäß den durch den Task **einzelne Abonnements verwalten** erteilten Berechtigungen erstellt werden, enthalten einen vorab festgelegten Benutzernamen, der auf dem Domänen Benutzerkonto basiert. Wenn der Benutzer das Abonnement erstellt, wird der Empfängername im **An:** -Feld mit dem Domänenbenutzerkonto der Person ausgefüllt, die das Abonnement erstellt.  
  
 Bei Verwendung eines SMTP-Servers bzw. einer Weiterleitung, der bzw. die E-Mail-Konten verwendet, die mit dem Domänenbenutzerkonto nicht übereinstimmen, erzeugt die Berichtsübermittlung einen Fehler, wenn der SMTP-Server den Bericht an diesen Benutzer übermitteln will.  
  
 Sie können die Konfigurationseinstellungen ändern, die Benutzern das Eingeben eines Namens im Feld **An:** ermöglichen, um das Problem zu umgehen:  
  
1.  Öffnen Sie RSReportServer.config mit einem Text-Editor.  
  
2.  Setzen Sie `SendEmailToUserAlias` auf `False`.  
  
3.  Legen Sie `DefaultHostName` auf den DNS-Namen (Domain Name System) oder die IP-Adresse des SMTP-Servers bzw. der Weiterleitung fest.  
  
4.  Speichern Sie die Datei .  
  
  
  
##  <a name="bkmk_options_remote_SMTP"></a>Konfigurationsoptionen für den SMTP-Remote Dienst  
 Die Verbindung zwischen dem Berichtsserver und einem SMTP-Server oder einer SMTP-Weiterleitung wird durch die folgenden Konfigurationseinstellungen bestimmt:  
  
-   
  `SendUsing` gibt eine Methode für das Senden von Nachrichten an. Sie können zwischen einem SMTP-Netzwerkdienst und einem lokalen SMTP-Dienstabholverzeichnis wählen. Um einen SMTP-Remotedienst zu verwenden, muss dieser Wert in der Datei RSReportServer.config auf **2** eingestellt werden.  
  
-   
  `SMTPServer` gibt den SMTP-Remoteserver bzw. die SMTP-Weiterleitung an. Dieser Wert ist erforderlich, wenn Sie einen SMTP-Remoteserver oder eine SMTP-Weiterleitung verwenden.  
  
-   `From`Legt den Wert fest, der in der **from:** -Zeile einer e-Mail-Nachricht angezeigt wird. Dieser Wert ist erforderlich, wenn Sie einen SMTP-Remoteserver oder eine SMTP-Weiterleitung verwenden.  
  
 Andere Werte, die für den SMTP-Remotedienst verwendet werden, sind folgende (diese Werte müssen Sie nur angeben, wenn Sie die Standardwerte überschreiben möchten).  
  
-   **SMTPServerPort** wird für Port 25 konfiguriert.  
  
-   **SMTPAuthenticate** gibt an, wie der Berichts Server eine Verbindung mit dem SMTP-Remote Server herstellt. Der Standardwert ist 0 (d. h. keine Authentifizierung). In diesem Fall wird die Verbindung über den anonymen Zugriff hergestellt. Je nach Domänenkonfiguration müssen der Berichtsserver und der SMTP-Server unter Umständen zu derselben Domäne gehören.  
  
     Um E-Mail an eingeschränkte Verteilerlisten zu senden (z. B. Verteilerlisten, die nur eingehende Nachrichten von authentifizierten Konten akzeptieren), legen Sie **SMTPAuthenticate** auf **2**fest.  
  

  
##  <a name="bkmk_options_local_SMTP"></a>Konfigurationsoptionen für den lokalen SMTP-Dienst  
 Das Konfigurieren eines lokalen SMTP-Dienstes ist sinnvoll, wenn Sie die E-Mail-Übermittlung des Berichtsservers testen oder entsprechende Probleme behandeln. Der lokale SMTP-Dienst ist standardmäßig nicht aktiviert. Anweisungen zur Aktivierung finden Sie unter [Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung (SSRS Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) und [e-Mail-Einstellungen-Configuration Manager &#40;SSRS-&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)im einheitlichen Modus.  
  
 Die Verbindung zwischen dem Berichtsserver und einem lokalen SMTP-Server oder einer SMTP-Weiterleitung wird durch die folgenden Konfigurationseinstellungen bestimmt:  
  
-   `SendUsing`wird auf **1**festgelegt.  
  
-   **SMTPServerPickupDirectory** ist auf einen Ordner auf dem lokalen Laufwerk festgelegt.  
  
    > [!NOTE]  
    >  Stellen Sie sicher, dass Sie nicht `SMTPServer` festlegen, wenn Sie einen lokalen SMTP-Server verwenden.  
  
-   `From`Legt den Wert fest, der in der **from:** -Zeile einer e-Mail-Nachricht angezeigt wird. Dieser Wert ist erforderlich.  
  
 
  
##  <a name="bkmk_use_configuration_manager"></a>So konfigurieren Sie Berichts Server-e-Mails mithilfe der Konfigurations-Manager für Reporting Services  
  
1.  Überprüfen Sie, ob der Report Server-Windows-Dienst über `Send As`-Berechtigungen auf dem SMTP-Server verfügt.  
  
2.  Starten Sie den Reporting Services-Konfigurations-Manager, und stellen Sie eine Verbindung mit der Berichtsserverinstanz her.  
  
3.  Geben Sie auf der Seite E-Mail-Einstellungen den Namen des SMTP-Servers ein. Bei diesem Wert kann es sich um eine IP-Adresse, den UNC-Namen eines Computers im Firmenintranet oder um einen vollqualifizierten Domänennamen handeln.  
  
4.  Geben Sie in **Absenderadresse**den Namen eines Kontos ein, das über die Berechtigung zum Senden von E-Mail vom SMTP-Server verfügt.  
  
5.  Klicken Sie auf **Anwenden**.  
  

  
##  <a name="bkmk_confiugre_remote_SMTP"></a>So konfigurieren Sie einen SMTP-Remote Dienst für den Berichts Server  
  
1.  Überprüfen Sie, ob der Report Server-Windows-Dienst über `Send As`-Berechtigungen auf dem SMTP-Server verfügt.  
  
2.  Öffnen Sie die Datei RSReportServer.config in einem Text-Editor.  
  
3.  Vergewissern Sie sich `UrlRoot` , dass <> auf die URL-Adresse des Berichts Servers festgelegt ist. Dieser Wert wird beim Konfigurieren des Berichtsservers festgelegt und sollte bereits ausgefüllt sein. Geben Sie andernfalls die URL-Adresse des Berichtsservers ein.  
  
4.  Suchen Sie im Abschnitt "Delivery" `ReportServerEmail` nach <>.  
  
5.  Geben Sie `SMTPServer` in <> den Namen des SMTP-Servers ein. Bei diesem Wert kann es sich um eine IP-Adresse, den UNC-Namen eines Computers im Firmenintranet oder um einen vollqualifizierten Domänennamen handeln.  
  
6.  Vergewissern Sie sich `SendUsing` , dass <> auf 2 festgelegt ist. Bei einem anderen Wert ist der Berichtsserver nicht für die Verwendung eines Remote-SMTP-Diensts konfiguriert.  
  
7.  Geben Sie `From` in <> den Namen eines Kontos ein, das über die Berechtigung zum Senden von e-Mails vom SMTP-Server verfügt.  
  
8.  Speichern Sie die Datei .  
  
     Die neuen Einstellungen werden automatisch vom Berichtsserver verwendet, Sie müssen den Dienst nicht neu starten. Sie können weitere SMTP-Einstellungen angeben, um die Verwendung des SMTP-Servers für die Berichtsserver-E-Mail-Übermittlung weiter zu konfigurieren. Weitere Informationen fin derden Sie unter [Configurin derg a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) und [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onlin dere.  
  

  
##  <a name="bkmk_confiugre_local_SMTP"></a>So konfigurieren Sie einen lokalen SMTP-Dienst für den Berichts Server  
  
1.  Klicken Sie in der Systemsteuerung auf **Software**.  
  
2.  Klicken Sie auf **Windows-Komponenten hinzufügen/entfernen** , um den Assistenten für Windows-Komponenten zu starten.  
  
3.  Wählen Sie **Anwendungsserver** aus, und klicken Sie auf **Details**.  
  
4.  Wählen Sie **Internetinformationsdienste (IIS)** aus, und klicken Sie auf **Details**.  
  
5.  Aktivieren Sie das Kontrollkästchen **SMTP-Dienst** , und klicken Sie auf **OK**.  
  
6.  Klicken Sie im Assistenten für Windows-Komponenten auf **Weiter**. Klicken Sie auf **Fertig stellen**.  
  
7.  Überprüfen Sie in der **** Dienstekonsole, ob der Dienst ausgeführt wird.  
  
8.  Öffnen Sie die Datei **RSReportServer. config** in einem Text-Editor.  
  
9. Überprüfen Sie, ob `<UrlRoot>` auf die URL-Adresse des Berichtsservers festgelegt ist. Dieser Wert wird beim Konfigurieren des Berichtsservers festgelegt und sollte bereits ausgefüllt sein. Geben Sie andernfalls die URL-Adresse des Berichtsservers ein.  
  
10. Suchen Sie im Abschnitt Delivery nach `<ReportServerEmail>.`  
  
11. Deaktivieren Sie in `<SMTPServer>`die Werte für diese Einstellung, aber löschen Sie nicht die Tags.  
  
12. Legen Sie `<SendUsing>` auf 1 fest. Bei einem anderen Wert ist der Berichtsserver nicht für die Verwendung eines lokalen SMTP-Diensts konfiguriert.  
  
13. Legen Sie `<SMTPServerPickupDirectory>` auf einen Ordner auf dem lokalen Laufwerk fest.  
  
14. Legen Sie `<From>` auf ein Konto fest, das über die Berechtigung zum Senden von E-Mail vom SMTP-Server verfügt.  
  
15. Speichern Sie die Datei .  
  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
