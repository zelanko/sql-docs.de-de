---
title: Konfigurieren des Berichtsserver-Dienstkontos (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: 19eca52c1686f218b2c59449b139d684700822b5
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53328960"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a>Konfigurieren des Berichtsserver-Dienstkontos (SSRS-Konfigurations-Manager)

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird als Einzeldienst mit einem Report Server-Webdienst (Berichts-Manager) und einer Hintergrundverarbeitungsanwendung implementiert, die für die geplante Berichtsverarbeitung und die Abonnementübermittlung verwendet wird. In diesem Thema wird erläutert, wie das Dienstkonto zu Beginn konfiguriert wird. Außerdem wird beschrieben, wie das Konto oder das Kennwort mit dem Reporting Services-Konfigurationstool geändert wird.  
  
## <a name="initial-configuration"></a>Anfängliche Konfiguration

 Das Berichtsserver-Dienstkonto wird während der Ausführung von Setup definiert. Sie können den Dienst unter einem Domänenbenutzerkonto oder unter einem integrierten Konto wie einem `NetworkService`-Konto ausführen. Es gibt kein Standardkonto ein. alle Konten, die Sie, in angeben der [Serverkonfiguration – Dienstkonten](../../sql-server/install/server-configuration-service-accounts.md) Seite des Installations-Assistenten wird das Konto für den Berichtsserverdienst.  
  
> [!IMPORTANT]
> Der Report Server-Webdienst und der Berichts-Manager sind [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]-Anwendungen; sie werden jedoch nicht unter dem [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]-Konto ausgeführt. Die Einzeldienstarchitektur führt beide ASP.NET-Anwendungen im Rahmen der gleichen Berichtsserver-Prozessidentität aus. Dies ist eine wichtige Änderung gegenüber früheren Versionen, in denen der Report Server-Webdienst und der Berichts-Manager unter der gleichen, in IIS angegebenen [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]-Arbeitsprozessidentität ausgeführt wurden.
  
## <a name="changing-the-service-account"></a>Ändern des Dienstkontos

 Verwenden Sie stets das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool, um die Informationen für das Dienstkonto anzuzeigen und neu zu konfigurieren. Die Informationen zur Dienstidentität werden intern an mehreren Speicherorten gespeichert. Durch die Verwendung des Tools wird sichergestellt, dass alle Verweise entsprechend aktualisiert werden, wenn Sie das Konto oder das Kennwort ändern. Vom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool werden folgende zusätzlichen Schritte ausgeführt, um sicherzustellen, dass der Berichtsserver verfügbar bleibt:  
  
- Das neue Konto wird automatisch der auf dem lokalen Computer erstellten Berichtsservergruppe hinzugefügt. Diese Gruppe wird in den Zugriffssteuerungslisten (Access Control Lists, ACLs) angegeben, die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dateien schützen.  
  
- Die Anmeldeberechtigungen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz, die als Host für die Berichtsserver-Datenbank fungiert, werden automatisch aktualisiert. Das neue Konto wird der **RSExecRole**hinzugefügt.  
  
     Die Datenbankanmeldung für das alte Konto wird nicht automatisch entfernt. Stellen Sie sicher, dass nicht mehr benötigte Konten entfernt werden. Weitere Informationen finden Sie unter [Verwalten einer Berichtsserver-Datenbank (einheitlicher SSRS-Modus)](../report-server/report-server-database-ssrs-native-mode.md) in der SQL Server-Onlinedokumentation.  
  
     Um einem neuen Dienstkonto Datenbankberechtigungen gewähren zu können, muss die Berichtsserver-Datenbankverbindung zuvor für das Dienstkonto konfiguriert worden sein. Wenn Sie die Berichtsserver-Datenbankverbindung für ein Domänenbenutzerkonto oder eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung konfiguriert haben, hat die Aktualisierung des Dienstkontos keine Auswirkungen auf die Verbindungsinformationen.  
  
- Der Verschlüsselungsschlüssel wird automatisch aktualisiert, sodass er die Profilinformationen des neuen Kontos enthält.  
  
    > [!NOTE]  
    > Wenn der Berichtsserver Teil einer Bereitstellung für horizontales Skalieren ist, ist nur der Berichtsserver betroffen, den Sie aktualisieren. Auf die Verschlüsselungsschlüssel für andere Berichtsserver in der Bereitstellung hat die Änderung des Dienstkontos keine Auswirkung.  
  
 Anweisungen dazu, wie Sie das Konto festzulegen, finden Sie unter [Konfigurieren eines Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).  
  
## <a name="choosing-an-account"></a>Auswählen eines Kontos

 Sie können den Berichtsserver-Dienst zur Ausführung unter einem der folgenden Kontotypen konfigurieren:  
  
- Windows-Benutzerkonto mit minimalen Privilegien  
  
- NetworkService  
  
- LocalSystem  
  
- LocalService  
  
 Es gibt nicht den einen idealen Ansatz zum Auswählen eines Kontotyps. Jedes Konto hat Vor- und Nachteile, die Sie berücksichtigen sollten. Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf einem Produktionsserver bereitstellen, empfiehlt es sich, den Dienst für ein Domänenbenutzerkonto zu konfigurieren. Auf diese Weise können Sie schwere Schäden vermeiden, wenn sich Dritte unbefugten Zugriff auf ein freigegebenes Konto verschaffen. Dies erleichtert ferner die Überwachung der Anmeldeaktivitäten für dieses Konto. Wenn Sie ein Windows-Benutzerkonto verwenden und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in einem Netzwerk mit Kerberos-Authentifizierung verwenden, ist eine Registrierung des Diensts für das Benutzerkonto erforderlich. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
 Die folgenden Richtlinien und Links in diesem Abschnitt können Ihnen helfen, den für Ihre Bereitstellung am besten geeigneten Ansatz zu finden.  
  
- [Dienstkonto &#40;einheitlicher SSRS-Modus&#41;](../../sql-server/install/service-account-ssrs-native-mode.md).  
  
- [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) in SQL Server-Onlinedokumentation.  
  
- [Die Dienste und Service Accounts Security Planning Guide](http://usergroup.doubletake.com/file_cabinet/download/0x000021733).  
  
## <a name="updating-an-expired-password"></a>Aktualisieren eines abgelaufenen Kennworts

 Wenn der Berichtsserver-Dienst unter einem Domänenkonto ausgeführt wird und das Kennwort abläuft, bevor Sie es im Reporting Services-Konfigurationstool aktualisieren können, wird der Dienst erst wieder gestartet, wenn Sie ein neues Kennwort angeben. Wenn der Dienst nicht gestartet werden kann, können Sie mit dem Reporting Services-Konfigurationstool keine Verbindung zum Server herstellen, um das Konto zu aktualisieren. In diesem Fall müssen Sie den Server mit einer Reihe von Tools wieder online schalten.  
  
 Gehen Sie wie folgt vor, um das Kennwort zurückzusetzen:  
  
1. Auf der **starten** , zeigen Sie auf **Systemsteuerung**, zeigen Sie auf **Administratortools**, und klicken Sie auf **Services**.  
  
2. Mit der rechten Maustaste **SQL Server Reporting Services**Option **Eigenschaften**.  
  
3. Klicken Sie auf **anmelden**, und geben Sie das neue Kennwort.  
  
4. Nachdem Sie das Kennwort aktualisiert haben, starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool, und aktualisieren Sie das Kenwort auf der Seite Dienstkonto. Dieser zusätzliche Schritt ist erforderlich, um die Kontoinformationen zu aktualisieren, die intern vom Berichtsserver gespeichert werden.  
  
 Wenn das Kennwort des Dienstkontos für das [!INCLUDE[ssDE](../../includes/ssde-md.md)] abgelaufen ist, tritt beim Versuch, eine Verbindung mit dem Berichtsserver herzustellen, der Fehler `rsReportServerDatabaseUnavailable` auf. Durch Zurücksetzen des Kennworts wird der Fehler behoben.  
  
## <a name="configuring-the-report-server-service-for-a-sharepoint-integrated-report-server"></a>Konfigurieren des Berichtsserver-Diensts für einen in SharePoint integrierten Berichtsserver

 Wenn Sie einen Berichtsserver im integrierten SharePoint-Modus ausführen, müssen die Dienstkontoinformationen aktualisiert werden, die in der SharePoint-Konfigurationsdatenbank gespeichert sind, sofern eine der folgenden Bedingungen zutrifft:  
  
- Änderung des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienstkontos (z.&amp;B. Wechsel von einem NetworkService-Konto zu einem Domänenbenutzerkonto).  
  
- Erweiterung einer SharePoint-Farm für eine weitere SharePoint-Webanwendung. Eine Aktualisierung der Datenbankzugriffsinformationen ist erforderlich, wenn die Serverfarm für die Berichtsserverintegration konfiguriert wurde, während die neu hinzugefügte Anwendung zur Ausführung unter einem anderen Benutzerkonto als die Anwendungen in der Farm konfiguriert wurde.  
  
 Nach dem Zurücksetzen der Datenbankzugriffsinformationen sollten Sie den [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]-Dienst neu starten, um sicherzustellen, dass die alte Verbindung nicht mehr verwendet wird.  
  
1. In **Verwaltung**, klicken Sie auf **SharePoint 2010 Central Administration**.  
  
2. Klicken Sie auf **Anwendungsverwaltung**.  
  
3. Klicken Sie im Abschnitt Reporting Services auf **Gewähren von Datenbankzugriff**.  
  
4. Klicken Sie auf **OK**. Das Dialogfeld Anmeldeinformationen eingeben wird angezeigt.  
  
5. Geben Sie die Anmeldeinformationen eines Benutzers ein, der ein Mitglied der Gruppe lokaler Administratoren auf dem Computer ist, der den Berichtsserver hostet. Die Anmeldeinformationen werden für eine einmalige Verbindung mit dem Berichtsservercomputer zum Abrufen von Dienstkontoinformationen verwendet. Die für jedes Dienstkonto erstellte Datenbankanmeldung wird in SharePoint-Datenbanken aktualisiert.  
  
6. Um den Dienst neu starten, klicken Sie auf **Vorgänge**.  
  
7. Klicken Sie in der Topologie und Dienste auf **Dienste auf dem Server**.  
  
8. Klicken Sie für Windows SharePoint Services-Webanwendung auf **beenden**.  
  
9. Warten Sie, bis der Dienst beendet wird.  
  
10. Klicken Sie auf **starten**.  
  
> [!NOTE]  
> Für SharePoint-Produkte und -Technologien sind Domänenkonten zur Dienstkonfiguration erforderlich, wie der SharePoint-Modus für Reporting Services.  
  
## <a name="next-steps"></a>Nächste Schritte

 [Konfigurieren eines Dienstkontos &#40;SSRS-Konfigurations-Manager&#41; ](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [-Dienstkonto &#40;einheitlicher SSRS-Modus&#41; ](../../sql-server/install/service-account-ssrs-native-mode.md) [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfiguration Manager&#41; ](configure-report-server-urls-ssrs-configuration-manager.md) [Reporting Services-Konfigurations-Manager &#40;im einheitlichen Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)
