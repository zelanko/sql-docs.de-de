---
title: Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 275503157f0bfbc004463f3bc567cfbef4a3fc41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117048"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a>Konfigurieren eines Berichtsservers für die E-Mail-Übermittlung (SSRS-Konfigurations-Manager)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält eine Erweiterung zur E-Mail-Übermittlung, damit Sie Berichte per E-Mail verteilen können. Je nachdem, wie Sie das Abonnieren von E-Mails definieren, kann eine E-Mail-Übermittlung aus einer Nachricht, einem Link, einem Anhang oder einem eingebetteten Bericht bestehen. Die Erweiterung der E-Mail-Übermittlung arbeitet mit Ihrer vorhandenen E-Mail-Server-Technologie. Der E-Mail-Server muss ein SMTP-Server oder eine Weiterleitung sein. Der Berichtsserver stellt über CDO-Bibliotheken (Collaboration Data Objects, cdosys.dll), die das Betriebssystem stellt, eine Verbindung zu einem SMTP-Server her.  
  
 Die E-Mail-Übermittlungserweiterung des Berichtsservers ist standardmäßig nicht konfiguriert. Sie müssen den Reporting Services-Konfigurations-Manager verwenden, um die Erweiterung minimal zu konfigurieren. Sie müssen die Datei `RSReportServer.config` bearbeiten, um die erweiterten Eigenschaften festzulegen. Wenn Sie den Berichtsserver für die Verwendung dieser Erweiterung nicht konfigurieren können, können Sie stattdessen Berichte an einen freigegebenen Ordner übermitteln. Weitere Informationen finden Sie unter [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus|  
  
 
  
##  <a name="bkmk_configuration_requirements"></a> Konfigurationsanforderungen  
  
-   Die E-Mail-Übermittlung des Berichtsservers wird über Collaboration Data Objects (CDO) implementiert und erfordert einen SMTP-Remoteserver oder einen lokalen SMTP-Server (Simple Mail Transfer Protocol) bzw. eine SMTP-Weiterleitung. SMTP wird nicht von allen Windows-Betriebssystemen unterstützt. Wenn Sie die Itanium-basierte Edition von Windows Server 2008 verwenden, wird SMTP nicht unterstützt. Weitere Informationen zu den Konfigurationsoptionen von CDO finden Sie unter [Configuration CoClass](http://go.microsoft.com/fwlink/?LinkId=98237) auf MSDN.  
  
-   Das Berichtsserver-Dienstkonto muss auf dem SMTP-Server berechtigt sein, E-Mails zu senden.  
  
-   Für die Erweiterung der E-Mail-Übermittlung wird in E-Mail-Anlagen die UTF-8-Codierung verwendet. Die Codierung kann nicht geändert werden. Die HTML-Renderingerweiterung unterstützt ausschließlich UTF-8.  
  
> [!NOTE]  
>  Die standardmäßige E-Mail-Übermittlungserweiterung bietet keine Unterstützung für digitale Signaturen oder für die Verschlüsselung ausgehender E-Mail-Nachrichten.  
  
 
  
##  <a name="bkmk_configure_for_local_or_remote_SMTP"></a> Konfigurieren eines Berichtsservers für lokale oder Remote-SMTP-Dienst  
 Zur Unterstützung der E-Mail-Übermittlung können Sie einen lokalen SMTP-Dienst oder einen SMTP-Remoteserver bzw. eine SMTP-Weiterleitung verwenden. Wenn Sie auf einen vorhandenen SMTP-Remoteserver zugreifen können, sollten Sie ihn verwenden. Wenn kein SMTP-Server verfügbar ist oder wenn zu einem späteren Zeitpunkt Berichtsübermittlungsfehler auftreten, die auf Fehler bei der Computerverbindung zurückzuführen sind, sollten Sie stattdessen einen lokalen SMTP-Dienst verwenden. Informationen zum Konfigurieren eines Berichtsservers für lokale Dienste und Remotedienste finden Sie weiter unten in diesem Thema.  
  
  
  
##  <a name="bkmk_setting_email_delivery"></a> Festlegen von Konfigurationsoptionen für die e-Mail-Übermittlung  
 Bevor Sie die E-Mail-Übermittlung des Berichtsservers verwenden können, müssen Sie Konfigurationswerte festlegen, die angeben, welcher SMTP-Server verwendet werden soll.  
  
 Gehen Sie wie folgt vor, um einen Berichtsserver für die E-Mail-Übermittlung zu konfigurieren:  
  
-   Verwenden Sie den Reporting Services-Konfigurations-Manager, wenn Sie nur einen SMTP-Server und ein Benutzerkonto angeben, das über die Berechtigung zum Senden von E-Mail verfügt. Dies sind die zum Konfigurieren der E-Mail-Übermittlungserweiterung für einen Berichtsserver erforderlichen Mindesteinstellungen. Weitere Informationen finden Sie unter [e-Mail-Einstellungen – Konfigurations-Manager &#40;einheitlicher SSRS-Modus&#41; ](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) und [e-Mail-Übermittlung in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   (Optional) Verwenden Sie einen Text-Editor, um zusätzliche Einstellungen in der Datei RSreportserver.config anzugeben. Diese Datei enthält alle Konfigurationseinstellungen für die Berichtsserver-E-Mail-Übermittlung. Wenn Sie einen lokalen SMTP-Server verwenden oder die E-Mail-Übermittlung auf bestimmte Hosts beschränken, müssen Sie zusätzliche Einstellungen in diesen Dateien angeben. Weitere Informationen zum Suchen und Ändern von Konfigurationsdateien finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei &#40;"rsreportserver.config"&#41; ](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) in SQL Server-Onlinedokumentation.  
  
> [!NOTE]  
>  E-Mail-Einstellungen für den Berichtsserver basieren auf CDO (Collaboration Data Objects). Ausführlichere Informationen zu bestimmten Einstellungen finden Sie in der CDO-Produktdokumentation.  
  

  
##  <a name="bkmk_example_config_file"></a> Beispiel-e-Mail Berichtsserverkonfiguration  
 Das folgende Beispiel veranschaulicht die Einstellungen für einen SMTP-Remoteserver in der Datei RSreportserver.config. Informationen zu einstellungsbeschreibungen und gültigen Werten finden Sie unter [RSReportServer-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Onlinedokumentation oder in der CDO-Produktdokumentation.  
  
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
  

  
##  <a name="bkmk_setting_TO_field"></a> Konfigurationsoptionen für die Einstellung der auf: Feld in einer Nachricht  
 Benutzerdefinierte Abonnements, die gemäß den durch den Task **Einzelne Abonnements verwalten** erteilten Berechtigungen erstellt werden, enthalten einen vorher festgelegten Benutzernamen, der auf dem Domänenbenutzerkonto basiert. Wenn der Benutzer das Abonnement erstellt, wird der Empfängername im **An:** -Feld mit dem Domänenbenutzerkonto der Person ausgefüllt, die das Abonnement erstellt.  
  
 Bei Verwendung eines SMTP-Servers bzw. einer Weiterleitung, der bzw. die E-Mail-Konten verwendet, die mit dem Domänenbenutzerkonto nicht übereinstimmen, erzeugt die Berichtsübermittlung einen Fehler, wenn der SMTP-Server den Bericht an diesen Benutzer übermitteln will.  
  
 Sie können die Konfigurationseinstellungen ändern, die Benutzern das Eingeben eines Namens im Feld **An:** ermöglichen, um das Problem zu umgehen:  
  
1.  Öffnen Sie RSReportServer.config mit einem Text-Editor.  
  
2.  Legen Sie `SendEmailToUserAlias` zu `False`.  
  
3.  Legen Sie `DefaultHostName` zum Domain Name System (DNS)-Namen oder IP-Adresse des SMTP-Servers bzw. der Weiterleitung.  
  
4.  Speichern Sie die Datei.  
  
  
  
##  <a name="bkmk_options_remote_SMTP"></a> Konfigurationsoptionen für den SMTP-Remotedienst  
 Die Verbindung zwischen dem Berichtsserver und einem SMTP-Server oder einer SMTP-Weiterleitung wird durch die folgenden Konfigurationseinstellungen bestimmt:  
  
-   `SendUsing` Gibt eine Methode zum Senden von Nachrichten. Sie können zwischen einem SMTP-Netzwerkdienst und einem lokalen SMTP-Dienstabholverzeichnis wählen. Um einen SMTP-Remotedienst zu verwenden, muss dieser Wert in der Datei RSReportServer.config auf **2** eingestellt werden.  
  
-   `SMTPServer` Gibt den SMTP-Remoteserver oder die Weiterleitung. Dieser Wert ist erforderlich, wenn Sie einen SMTP-Remoteserver oder eine SMTP-Weiterleitung verwenden.  
  
-   `From` Legt den Wert, der in der **aus:** -Zeile einer E-mail. Dieser Wert ist erforderlich, wenn Sie einen SMTP-Remoteserver oder eine SMTP-Weiterleitung verwenden.  
  
 Andere Werte, die für den SMTP-Remotedienst verwendet werden, sind folgende (diese Werte müssen Sie nur angeben, wenn Sie die Standardwerte überschreiben möchten).  
  
-   **SMTPServerPort** wird für Port 25 konfiguriert.  
  
-   **SMTPAuthenticate** gibt an, wie der Berichtsserver eine Verbindung zum SMTP-Remoteserver herstellt. Der Standardwert ist 0 (d. h. keine Authentifizierung). In diesem Fall wird die Verbindung über den anonymen Zugriff hergestellt. Je nach Domänenkonfiguration müssen der Berichtsserver und der SMTP-Server unter Umständen zu derselben Domäne gehören.  
  
     Um E-Mail an eingeschränkte Verteilerlisten zu senden (z. B. Verteilerlisten, die nur eingehende Nachrichten von authentifizierten Konten akzeptieren), legen Sie **SMTPAuthenticate** auf **2**fest.  
  

  
##  <a name="bkmk_options_local_SMTP"></a> Konfigurationsoptionen für die lokale SMTP-Dienst  
 Das Konfigurieren eines lokalen SMTP-Dienstes ist sinnvoll, wenn Sie die E-Mail-Übermittlung des Berichtsservers testen oder entsprechende Probleme behandeln. Der lokale SMTP-Dienst ist standardmäßig nicht aktiviert. Anweisungen dazu, wie Sie diese aktivieren, finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung (SSRS-Konfigurations-Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) und [e-Mail-Einstellungen – Konfigurations-Manager &#40;einheitlicher SSRS-Modus&#41; ](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) .  
  
 Die Verbindung zwischen dem Berichtsserver und einem lokalen SMTP-Server oder einer SMTP-Weiterleitung wird durch die folgenden Konfigurationseinstellungen bestimmt:  
  
-   `SendUsing` nastaven NA hodnotu **1**.  
  
-   Für**SMTPServerPickupDirectory** ist ein Ordner auf dem lokalen Laufwerk festgelegt.  
  
    > [!NOTE]  
    >  Achten Sie darauf, dass Sie nicht festlegen `SMTPServer` Wenn Sie einen lokalen SMTP-Server verwenden.  
  
-   `From` Legt den Wert, der in der **aus:** -Zeile einer E-mail. Dieser Wert ist erforderlich.  
  
 
  
##  <a name="bkmk_use_configuration_manager"></a> So konfigurieren Sie die Report Server-e-Mail mithilfe von Configuration Manager für Reporting Services  
  
1.  Überprüfen Sie, ob der Report Server-Windows-Dienst über `Send As`-Berechtigungen auf dem SMTP-Server verfügt.  
  
2.  Starten Sie den Reporting Services-Konfigurations-Manager, und stellen Sie eine Verbindung mit der Berichtsserverinstanz her.  
  
3.  Geben Sie auf der Seite E-Mail-Einstellungen den Namen des SMTP-Servers ein. Bei diesem Wert kann es sich um eine IP-Adresse, den UNC-Namen eines Computers im Firmenintranet oder um einen vollqualifizierten Domänennamen handeln.  
  
4.  Geben Sie in **Absenderadresse**den Namen eines Kontos ein, das über die Berechtigung zum Senden von E-Mail vom SMTP-Server verfügt.  
  
5.  Klicken Sie auf **Anwenden**.  
  

  
##  <a name="bkmk_confiugre_remote_SMTP"></a> So konfigurieren Sie einen SMTP-Remotedienst auf, für den Berichtsserver  
  
1.  Überprüfen Sie, ob der Report Server-Windows-Dienst über `Send As`-Berechtigungen auf dem SMTP-Server verfügt.  
  
2.  Öffnen Sie die Datei RSReportServer.config in einem Text-Editor.  
  
3.  Überprüfen Sie, ob <`UrlRoot`> auf URL-Adresse des Berichtsservers festgelegt ist. Dieser Wert wird beim Konfigurieren des Berichtsservers festgelegt und sollte bereits ausgefüllt sein. Geben Sie andernfalls die URL-Adresse des Berichtsservers ein.  
  
4.  Suchen Sie im Abschnitt Delivery nach <`ReportServerEmail`>.  
  
5.  Geben Sie in <`SMTPServer`> den Namen des SMTP-Servers ein. Bei diesem Wert kann es sich um eine IP-Adresse, den UNC-Namen eines Computers im Firmenintranet oder um einen vollqualifizierten Domänennamen handeln.  
  
6.  Überprüfen Sie, ob <`SendUsing`> auf 2 festgelegt ist. Bei einem anderen Wert ist der Berichtsserver nicht für die Verwendung eines Remote-SMTP-Diensts konfiguriert.  
  
7.  In <`From`>, geben Sie den Namen eines Kontos mit der Berechtigung zum Senden von E-mail vom SMTP-Server.  
  
8.  Speichern Sie die Datei.  
  
     Die neuen Einstellungen werden automatisch vom Berichtsserver verwendet, Sie müssen den Dienst nicht neu starten. Sie können weitere SMTP-Einstellungen angeben, um die Verwendung des SMTP-Servers für die Berichtsserver-E-Mail-Übermittlung weiter zu konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) und [RSReportServer-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  

  
##  <a name="bkmk_confiugre_local_SMTP"></a> So konfigurieren Sie einen lokalen SMTP-Dienst für den Berichtsserver  
  
1.  Klicken Sie in der Systemsteuerung auf **Software**.  
  
2.  Klicken Sie auf **Windows-Komponenten hinzufügen/entfernen** , um den Assistenten für Windows-Komponenten zu starten.  
  
3.  Wählen Sie **Anwendungsserver** aus, und klicken Sie auf **Details**.  
  
4.  Wählen Sie **Internetinformationsdienste (IIS)** aus, und klicken Sie auf **Details**.  
  
5.  Aktivieren Sie das Kontrollkästchen **SMTP-Dienst** , und klicken Sie auf **OK**.  
  
6.  Klicken Sie im Assistenten für Windows-Komponenten auf **Weiter**. Klicken Sie auf **Fertig stellen**.  
  
7.  Überprüfen Sie in der **Dienstekonsole**, ob der Dienst ausgeführt wird.  
  
8.  Öffnen Sie die Datei **RSReportServer.config** in einem Text-Editor.  
  
9. Überprüfen Sie, ob `<UrlRoot>` auf die URL-Adresse des Berichtsservers festgelegt ist. Dieser Wert wird beim Konfigurieren des Berichtsservers festgelegt und sollte bereits ausgefüllt sein. Geben Sie andernfalls die URL-Adresse des Berichtsservers ein.  
  
10. Suchen Sie im Abschnitt Delivery nach `<ReportServerEmail>.`  
  
11. Deaktivieren Sie in `<SMTPServer>`die Werte für diese Einstellung, aber löschen Sie nicht die Tags.  
  
12. Legen Sie `<SendUsing>` auf 1 fest. Bei einem anderen Wert ist der Berichtsserver nicht für die Verwendung eines lokalen SMTP-Diensts konfiguriert.  
  
13. Legen Sie `<SMTPServerPickupDirectory>` auf einen Ordner auf dem lokalen Laufwerk fest.  
  
14. Legen Sie `<From>` auf ein Konto fest, das über die Berechtigung zum Senden von E-Mail vom SMTP-Server verfügt.  
  
15. Speichern Sie die Datei.  
  
 
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
