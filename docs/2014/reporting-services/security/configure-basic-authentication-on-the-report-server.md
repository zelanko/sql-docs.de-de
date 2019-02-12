---
title: Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- Basic authentication
ms.assetid: 8faf2938-b71b-4e61-a172-46da2209ff55
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a605117b6d2b1011d9285c0fb02275e5abeb35ac
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56019331"
---
# <a name="configure-basic-authentication-on-the-report-server"></a>Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver
  Standardmäßig akzeptiert Reporting Services Anforderungen, die Negotiate- und NTLM-Authentifizierung angeben. Wenn Ihre Bereitstellung Client-Anwendungen oder Browser umfasst, die die Standardauthentifizierung verwenden, müssen Sie die Standardauthentifizierung in die Liste der unterstützten Typen aufnehmen. Zusätzlich müssen Sie den anonymen Zugriff auf die Dateien des Berichts-Generators aktivieren, wenn Sie mit dem Berichts-Generator arbeiten möchten.  
  
 Um die Standardauthentifizierung auf dem Berichtsserver zu konfigurieren, bearbeiten Sie die XML-Elemente und -werte in der Datei RSReportServer.config. Sie können die Beispiele in diesem Thema kopieren und einfügen, um die Standardwerte zu ersetzen.  
  
 Bevor Sie die Standardauthentifizierung aktivieren, stellen Sie sicher, dass sie von der Sicherheitsinfrastruktur unterstützt wird. Unter der Standardauthentifizierung übergibt der Berichtsserver-Webdienst Anmeldeinformationen an die lokale Sicherheitsinstanz. Wenn die Anmeldeinformationen auf ein lokales Benutzerkonto verweisen, wird der Benutzer auf dem Computer, der den Berichtsserver ausführt, von der lokalen Sicherheitsinstanz authentifiziert und erhält ein Sicherheitstoken, das für lokale Ressourcen gültig ist. Anmeldeinformationen für Domänenbenutzerkonten werden an einen Domänencontroller weitergeleitet und von diesem authentifiziert. Das resultierende Ticket gilt für Netzwerkressourcen.  
  
 Wenn Sie das Risiko einschränken möchten, dass Anmeldeinformationen während der Übertragung auf einen Domänencontroller in Ihrem Netzwerk abgefangen werden, benötigen Sie eine Verschlüsselung auf Kanalebene wie Secure Sockets Layer (SSL). Die Standardauthentifizierung selbst überträgt den Benutzernamen in Klartext und das Kennwort in base64-Codierung. Die zusätzliche Verschlüsselung auf Kanalebene macht das Paket unlesbar. Weitere Informationen finden Sie unter [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](configure-ssl-connections-on-a-native-mode-report-server.md).  
  
 Bedenken Sie, dass Benutzer nach einer Aktivierung der Standardauthentifizierung die Option **Integrierte Sicherheit von Windows** nicht auswählen können, wenn Sie die Verbindungseigenschaften auf eine externe Datenquelle einstellen, die Daten an einen Bericht übergibt. Die Option ist auf den Seiten zu den Datenquelleneigenschaften grau abgeblendet.  
  
> [!NOTE]  
>  Die folgenden Anweisungen beziehen sich auf Berichtsserver, die im einheitlichen Modus ausgeführt werden. Wenn der Berichtserver im integrierten SharePoint-Modus bereitgestellt wird, müssen die Standardauthentifizierungseinstellungen verwendet werden, welche die integrierte Sicherheit von Windows angeben. Der Berichtsserver verwendet interne Erweiterungsfunktionen für die Standard-Windows-Authentifizierung, um Berichtsserver zu unterstützen, die im integrierten SharePoint-Modus ausgeführt werden.  
  
### <a name="to-configure-a-report-server-to-use-basic-authentication"></a>So konfigurieren Sie einen Berichtsserver für die Verwendung der Standardauthentifizierung  
  
1.  Öffnen Sie RSReportServer.config in einem Text-Editor.  
  
     Die Datei befindet sich unter  *\<Laufwerk >:* \Programme\Microsoft SQL Server\MSRS12. MSSQLSERVER\Reporting Services\ReportServer.  
  
2.  Suchen Sie den Eintrag <`Authentication`>.  
  
3.  Kopieren Sie die XML-Struktur, die Ihren Anforderungen am besten entspricht. Die erste XML-Struktur stellt Platzhalter bereit, über die Sie alle im nächsten Abschnitt beschriebenen Elemente angegeben können:  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsBasic>  
                       <LogonMethod>3</LogonMethod>  
                       <Realm></Realm>  
                       <DefaultDomain></DefaultDomain>  
                 </RSWindowsBasic>  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     Wenn Sie Standardwerte verwenden, können Sie die minimale Elementstruktur kopieren:  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsBasic/>  
          </AuthenticationTypes>  
    ```  
  
4.  Ersetzen Sie damit die vorhandenen Einträge für <`Authentication`>.  
  
     Wenn Sie mehrere Authentifizierungstypen verwenden, fügen Sie lediglich das `RSWindowsBasic`-Element ein, löschen Sie jedoch die Einträge für `RSWindowsNegotiate`, `RSWindowsNTLM` oder `RSWindowsKerberos` nicht.  
  
     Wenn Sie den Safari-Browser unterstützen möchten, können Sie den Berichtsserver nicht für die Verwendung mehrerer Authentifizierungstypen konfigurieren. Geben Sie nur `RSWindowsBasic` an, und löschen Sie die anderen Einträge.  
  
     Beachten Sie, dass Sie `Custom` nicht mit anderen Authentifizierungstypen verwenden können.  
  
5.  Ersetzen Sie leere Werte für <`Realm`> oder <`DefaultDomain`> durch Werte, die für Ihre Umgebung gültig sind.  
  
6.  Speichern Sie die Datei.  
  
7.  Wenn Sie eine horizontal skalierte Bereitstellung konfiguriert haben, wiederholen Sie diese Schritte für andere in der Bereitstellung vorhandene Berichtsserver.  
  
8.  Starten Sie den Berichtsserver neu, um alle momentan geöffneten Sitzungen zu beenden.  
  
## <a name="rswindowsbasic-reference"></a>Referenz auf RSWindowsBasic  
 Beim Konfigurieren der Standardauthentifizierung können die folgenden Elemente angegeben werden.  
  
|Element|Erforderlich|Gültige Werte|  
|-------------|--------------|------------------|  
|LogonMethod|Ja<br /><br /> Wenn Sie keinen Wert angeben, wird 3 verwendet.|`2` = Netzwerkanmeldung für Server mit hoher Leistungsfähigkeit zur Authentifizierung von Nur-Text-Kennwörtern<br /><br /> `3` = Klartextanmeldung, wobei die Anmeldeinformationen in das Authentifizierungspaket, die mit jeder HTTP-Anforderung gesendet wird beibehalten, so, dass der Server die Identität des Benutzers beim Verbinden mit anderen Servern im Netzwerk. (Standardwert)<br /><br /> Hinweis: Die Werte 0 (für interaktive Anmeldung) und 1 (für Batchanmeldung) werden in [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] nicht unterstützt.|  
|Realm|Optional|Gibt eine Ressourcenpartition mit Autorisierungs- und Authentifizierungsfunktionen an, mit denen Sie den Zugriff auf geschützte Ressourcen in Ihrem Unternehmen steuern können.|  
|DefaultDomain|Optional|Gibt die Domäne an, die vom Server für die Benutzerauthentifizierung verwendet wird. Dieser Wert ist optional. Wenn Sie ihn weglassen, verwendet der Berichtsserver den Computernamen als Domäne. Wenn der Computer zu einer Domäne gehört, ist diese Domäne die Standarddomäne. Wenn Sie den Berichtsserver auf einem Domänencontroller installiert haben, ist die verwendete Domäne die vom Computer gesteuerte.|  
  
## <a name="enabling-anonymous-access-to-report-builder-application-files"></a>Aktivieren des anonymen Zugriffs auf Anwendungsdateien des Berichts-Generators  
 Der Berichts-Generator verwendet die ClickOnce-Technologie, um Anwendungsdateien auf den Clientcomputer herunterzuladen und zu installieren. Beim Starten des Clientcomputers fordert das Anwendungsstartprogramm ClickOnce zusätzliche Anwendungsdateien auf dem Berichtsservercomputer an. Wenn der Berichtsserver auf Standardauthentifizierung eingestellt ist, kann die Authentifizierungsprüfung für das Anwendungsstartprogramm ClickOnce nicht erfolgreich durchgeführt werden. ClickOnce unterstützt die Standardauthentifizierung nicht.  
  
 Sie können dieses Problem umgehen, indem Sie den anonymen Zugriff auf die Programmdateien des Berichts-Generators aktivieren. Auf diese Weise kann ClickOnce beim Abrufen seiner Dateien die Authentifizierungsprüfung umgehen. Führen Sie folgende Schritte aus, um den anonymen Zugriff zu aktivieren:  
  
-   Überprüfen Sie, ob der Berichtsserver für die Standardauthentifizierung konfiguriert ist.  
  
-   Erstellen Sie unter ReportBuilder einen BIN-Ordner, und kopieren Sie vier Assemblys in den Ordner.  
  
-   Fügen Sie das `IsReportBuilderAnonymousAccessEnabled`-Element in RSReportServer.config ein, und stellen Sie es auf `True` ein. Nachdem Sie die Datei gespeichert haben, erstellt der Berichtsserver einen neuen Endpunkt zum Berichts-Generator. Der Endpunkt wird intern verwendet, um auf Programmdateien zuzugreifen und hat keine programmatische Schnittstelle, die Sie im Code verwenden können. Dank des separaten Endpunkts kann der Berichts-Generator in seiner eigenen Anwendungsdomäne innerhalb der Service-Prozessgrenze ausgeführt werden.  
  
-   Optional können Sie ein Konto mit Minimalprivilegien angeben, um Anforderungen in einem Sicherheitskontext zu verarbeiten, der sich von dem des Berichtsservers unterscheidet. Dieses Konto ist das anonyme Konto, mit dem Sie auf Dateien des Berichts-Generators zugreifen können, die sich auf einem Berichtsserver befinden. Das Konto legt die Identität des Threads im ASP.NET-Workerprozess fest. Die in diesem Thread ausgeführten Anforderungen werden ohne eine Authentifizierungsprüfung an den Berichtsserver übergeben. Dieses Konto entspricht der IUSR_\<Machine > Konto in IIS (Internetinformationsdienste), dient zum Festlegen des Sicherheitskontexts für ASP.NET Worker verarbeitet, wenn anonymer Zugriff und Identitätswechsel aktiviert sind. Um das Konto anzugeben, fügen Sie es einer Web.config-Datei auf dem Berichts-Generator hinzu.  
  
 Der Berichtsserver muss für die Standardauthentifizierung konfiguriert sein, wenn Sie den anonymen Zugriff auf die Programmdateien des Berichts-Generators aktivieren möchten. Wenn der Berichtsserver nicht für die Standardauthentifizierung konfiguriert ist, erhalten Sie eine Fehlermeldung, sobald Sie versuchen, den anonymen Zugriff zu aktivieren.  
  
 Weitere Informationen zu Problemen bei der Authentifizierung und zum Berichts-Generator finden Sie unter [Konfigurieren des Berichts-Generator-Zugriffs](../report-server/configure-report-builder-access.md).  
  
#### <a name="to-configure-report-builder-access-on-a-report-server-configured-for-basic-authentication"></a>So konfigurieren Sie den Berichts-Generator-Zugriff auf einem für die Standardauthentifizierung konfigurierten Berichtsserver  
  
1.  Stellen Sie sicher, dass der Berichtsserver für die Standardauthentifizierung konfiguriert ist, indem Sie die Authentifizierungseinstellungen in der Datei RSReportServer.config überprüfen.  
  
2.  Erstellen Sie im Ordner ReportBuilder einen BIN-Ordner. Standardmäßig befindet sich dieser Ordner im Verzeichnis \Programme\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder.  
  
3.  Kopieren Sie die folgenden Assemblys vom Ordner ReportServer\Bin in den Ordner ReportBuilder\BIN:  
  
     Microsoft.ReportingServices.Diagnostics.dll  
  
     Microsoft.ReportingServices.Interfaces.dll  
  
     ReportingServicesAppDomainManager.dll  
  
     RSHttpRuntime.dll  
  
4.  Erstellen Sie optional eine Web.config-Datei, um Berichts-Generator-Anforderungen in einem anonymen Konto zu verarbeiten:  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
    <system.web>  
    <authentication mode="Windows" />    
    <identity impersonate="true " userName="username" password="password"/>  
    </system.web>  
    </configuration>  
    ```  
  
     Der Authentifizierungsmodus muss auf `Windows` festgelegt werden, wenn Sie eine Web.config-Datei aufnehmen möchten.  
  
     `Identity impersonate` kann `True` oder `False` sein.  
  
    -   Legen Sie `False` fest, wenn ASP.NET das Sicherheitstoken nicht lesen darf. Die Anforderung wird im Sicherheitskontext des Berichtsserverdienstes ausgeführt.  
  
    -   Legen Sie `True` fest, wenn ASP.NET das Sicherheitstoken von der Hostebene lesen soll. Wenn Sie `True` festlegen, müssen Sie auch `userName` und `password` angeben, damit ein anonymes Konto bestimmt werden kann. Die von Ihnen angegebenen Anmeldeinformationen legen den Sicherheitskontext fest, unter dem die Anforderung ausgegeben wird.  
  
5.  Speichern Sie die Datei Web.config im Ordner ReportBuilder\bin.  
  
6.  Öffnen Sie die Datei RSReportServer.config im Abschnitt zu Reporting Services, suchen Sie `IsReportManagerEnabled`, und fügen Sie den folgenden Eintrag an das Ende an:  
  
    ```  
    <IsReportBuilderAnonymousAccessEnabled>True</IsReportBuilderAnonymousAccessEnabled>  
    ```  
  
7.  Speichern und schließen Sie die Datei RSReportServer.config.  
  
8.  Starten Sie den Berichtsserver neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsdomänen für Berichtsserveranwendungen](../report-server/application-domains-for-report-server-applications.md)   
 [Sicherheit und Schutz für Reporting Services](reporting-services-security-and-protection.md)  
  
  
