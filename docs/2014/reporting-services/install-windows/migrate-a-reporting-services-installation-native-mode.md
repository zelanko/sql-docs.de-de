---
title: Migrieren einer Reporting Services-Installation (einheitlicher Modus) | Microsoft-Dokumentation
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.custom: ''
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.date: 08/10/2017
ms.openlocfilehash: c359f709b2c0a1ba779111a007843dd249b5d7b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63261303"
---
# <a name="migrate-a-reporting-services-installation-native-mode"></a>Migrieren einer Reporting Services-Installation (einheitlicher Modus)

  Dieses Thema enthält Schritt-für-Schritt-Anleitungen zum Migrieren einer der folgenden unterstützten Versionen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] einer-Bereitstellung im einheitlichen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modus zu einer neuen-Instanz:  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)](Es sind weitere Schritte erforderlich. Weitere Informationen hierzu finden [Sie unter SQL Server 2005 zum Hosten von Berichts Server 2014-Datenbanken](https://support.microsoft.com/kb/2796721)  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Einheitlicher Modus.|  
  
 Informationen zum Migrieren einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung im SharePoint-Modus finden Sie unter [Migrieren einer Installation von Reporting Services &#40;SharePoint-Modus&#41;](migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
 Eine Migration wird als das Verschieben von Anwendungsdatendateien in eine neue [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Instanz definiert. Die folgenden häufigen Ursachen erfordern das Migrieren der Installation:  
  
-   Sie verfügen über eine umfangreiche Implementierung oder benötigen ein hoch verfügbares System.  
  
-   Die Hardware oder Topologie der Installation wurde geändert.  
  
-   Es ist ein Problem aufgetreten, das Upgrades blockiert.  
  
##  <a name="bkmk_nativemode_migration_overview"></a>Übersicht über die Migration im einheitlichen Modus  
 Der Migrationsprozess für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] umfasst manuelle und automatisierte Schritte. Die Migration eines Berichtsservers besteht aus den folgenden Teilaufgaben:  
  
-   Sichern Sie Datenbank-, Anwendungs- und Konfigurationsdateien.  
  
-   Sichern Sie den Verschlüsselungsschlüssel.  
  
-   Installieren Sie eine neue Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Wenn Sie dieselbe Hardware verwenden, können Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] parallel zu einer vorhandenen Installation installieren, wenn diese eine der unterstützten Versionen aufweist.  
  
    > [!TIP]  
    >  Bei einer parallelen Installation kann es erforderlich sein, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] als benannte Instanz zu installieren.  
  
-   Verschieben Sie die Berichtsserver-Datenbank und andere Anwendungsdateien aus der vorhandenen Installation in die neue [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installation.  
  
-   Verschieben Sie alle benutzerdefinierten Anwendungsdateien in die neue Installation.  
  
-   Konfigurieren Sie den Berichtsserver.  
  
-   Bearbeiten Sie **RSReportServer.config** , um ggf. vorhandene benutzerdefinierte Einstellungen aus der vorherigen Installation zu übernehmen.  
  
-   Sie können optional benutzerdefinierte Zugriffssteuerungslisten (ACLs) für die neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows-Dienstgruppe konfigurieren.  
  
-   Entfernen Sie nicht verwendete Anwendungen und Tools, nachdem Sie sich überzeugt haben, dass die neue Instanz voll funktionstüchtig ist.  
  
 Es gelten Beschränkungen bezüglich der Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , auf denen die Berichtsserver-Datenbank gehostet wird. Lesen Sie das folgende Thema, wenn Sie eine Berichtsserver-Datenbank, die in einer früheren Installation erstellt wurde, erneut verwenden.  
  
-   [Erstellen einer Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
##  <a name="bkmk_fixed_database_name"></a>Fester Datenbankname  
 Sie können die Berichtsserver-Datenbank nicht umbenennen. Die Identität der Datenbank wird bei der Datenbankerstellung in auf dem Berichtsserver gespeicherten Prozeduren aufgezeichnet. Wenn die primären oder temporären Berichtsserver-Datenbanken umbenannt werden, treten während der Ausführung der Prozeduren Fehler auf, sodass die Berichtsserverinstallation ungültig wird.  
  
 Wenn der Datenbankname der vorhandenen Installation für die neue Installation ungeeignet ist, sollten Sie eine neue Datenbank mit dem Namen erstellen und die vorhandenen Anwendungsdaten mithilfe der in der folgenden Liste beschriebenen Verfahren laden:  
  
-   Schreiben Sie ein [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Skript, das SOAP-Methoden des Berichtsserver-Webdiensts aufruft, um Daten von einer Datenbank in eine andere Datenbank zu kopieren. Zum Ausführen des Skripts können Sie das Hilfsprogramm RS.exe verwenden. Weitere Informationen zu diesem Verfahren finden Sie unter [Skripterstellung und PowerShell mit Reporting Services](../tools/scripting-and-powershell-with-reporting-services.md).  
  
-   Schreiben Sie Code, in dem der WMI-Anbieter aufgerufen wird, um Daten von einer Datenbank in eine andere Datenbank zu kopieren. Weitere Informationen zu diesem Verfahren finden Sie unter [Zugreifen auf den Reporting Services-WMI-Anbieter](../tools/access-the-reporting-services-wmi-provider.md).  
  
-   Wenn nur wenige Elemente vorliegen, können Sie die Berichte, Berichtsmodelle und freigegebenen Datenquellen vom Berichts-Designer, Modell-Designer und Berichts-Generator aus erneut auf dem neuen Berichtsserver veröffentlichen. Sie müssen Rollenzuweisungen, Abonnements, freigegebene Zeitpläne, Zeitpläne für Berichtmomentaufnahmen, benutzerdefinierte Eigenschaften, die Sie für Berichte und andere Elemente festlegen, Modellelementsicherheit und Eigenschaften, die Sie auf dem Berichtsserver festlegen, erneut erstellen. Die Protokolldaten über Berichtsverlauf und Berichtsausführung gehen verloren.  
  
##  <a name="bkmk_before_you_start"></a>Bevor Sie beginnen  
 Auch wenn Sie die Installation nicht aktualisieren, sondern migrieren, sollten Sie die Ausführung von Upgrade Advisor für die vorhandene Installation in Erwägung ziehen, um mögliche Probleme zu ermitteln, die sich auf die Migration auswirken könnten. Dieser Schritt ist besonders dann nützlich, wenn Sie einen Berichtsserver migrieren, den Sie nicht selbst installiert oder konfiguriert haben. Wenn Sie Upgrade Advisor ausführen, können Sie benutzerdefinierte Einstellungen ausfindig machen, die ggf. in einer neuen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installation nicht unterstützt werden.  
  
 Zudem müssen Sie sich mehrerer wichtiger Änderungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] bewusst sein, die sich auf Ihre Vorgehensweise beim Migrieren der Installation auswirken:  
  
-   Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]ist IIS keine erforderliche Komponente mehr. Wenn Sie eine Berichtsserverinstallation zu einem neuen Computer migrieren, müssen Sie die Webserverrolle nicht hinzufügen. Zudem unterscheiden sich die Schritte zum Konfigurieren von URLs und Authentifizierung von den in der vorherigen Version erforderlichen Schritten. Dasselbe gilt für Methoden und Tools für die Diagnose und Problembehandlung.  
  
-   Der Report Server-Webdienst, der Berichts-Manager und der Report Server-Windows-Dienst sind in einem einzigen Report Server-Dienst zusammengefasst. Alle drei Anwendungen werden unter dem gleichen Konto ausgeführt. Alle drei Anwendungen lesen Konfigurationseinstellungen aus der Datei RSReportServer.config, wodurch RSWebApplication.config nun veraltet ist.  
  
-   Der Berichts-Manager und SQL Server Management Studio sind umgestaltet worden, um überlappende Funktionen zu entfernen. Jedes Tool unterstützt unterschiedliche Tasks; die Tools sind nicht mehr austauschbar.  
  
-   ISAPI-Filter werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und höheren Versionen nicht unterstützt. Wenn Sie ISAPI-Filter verwenden, müssen Sie Ihre Berichtslösung vor der Migration umgestalten.  
  
-   IP-Adress Einschränkungen werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und höheren Versionen nicht unterstützt. Wenn Sie IP-Adresseinschränkungen verwenden, müssen Sie Ihre Berichtslösung vor der Migration umgestalten oder eine Technologie wie z. B. eine Firewall, einen Router oder NAT (Network Address Translation) verwenden, um Adressen zu konfigurieren, die nur eingeschränkt auf den Berichtsserver zugreifen dürfen.  
  
-   Client Secure Sockets Layer (SSL)-Zertifikate werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und höheren Versionen nicht unterstützt. Wenn Sie Client-SSL-Zertifikate verwenden, müssen Sie Ihre Berichtslösung vor der Migration umgestalten.  
  
-   Wenn Sie einen anderen Authentifizierungstyp als die integrierte Windows-Authentifizierung verwenden, müssen Sie das Element `<AuthenticationTypes>` in der Datei **RSReportServer.config** anhand eines unterstützten Authentifizierungstyps aktualisieren. Die unterstützten Authentifizierungstypen sind NTLM, Kerberos, Negotiate und Standard. Anonyme, .NET Passport-und Digest-Authentifizierung werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und höheren Versionen nicht unterstützt.  
  
-   Wenn Sie benutzerdefinierte Cascading Stylesheets in der Berichterstellungsumgebung verwenden, werden sie nicht migriert. Sie müssen sie nach der Migration manuell verschieben.  
  
 Weitere Informationen zu Änderungen in finden [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sie in der Dokumentation des Upgrade Advisors und in den [Neuerungen &#40;Reporting Services&#41;](../what-s-new-reporting-services.md).  
  
##  <a name="bkmk_backup"></a>Sicherungsdateien und-Daten  
 Vor dem Installieren einer neuen Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]müssen Sie alle Dateien der aktuellen Installation sichern.  
  
1.  Sichern Sie den Verschlüsselungsschlüssel für die Berichtsserver-Datenbank. Dieser Schritt ist für den Erfolg der Migration entscheidend. Im weiteren Verlauf des Migrationsprozesses müssen Sie den Schlüssel wiederherstellen, damit der Berichtsserver wieder auf verschlüsselte Daten zugreifen kann. Verwenden Sie den Reporting Services-Konfigurations-Manager, um den Schlüssel zu sichern.  
  
2.  Sichern Sie die Berichtsserver-Datenbank mit einer der unterstützten Methoden zum Sichern einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank. Weitere Informationen finden Sie in der Anleitung zum Sichern der Berichtsserver-Datenbank unter [Verschieben von Berichtsserver-Datenbanken auf einen anderen Computer (einheitlicher SSRS-Modus)](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
3.  Sichern Sie die Konfigurationsdateien des Berichtsservers. Folgende Dateien müssen gesichert werden:  
  
    1.  RSReportServer.config  
  
    2.  Rswebapplication.config  
  
    3.  Rssvrpolicy.config  
  
    4.  Rsmgrpolicy.config  
  
    5.  Reportingservicesservice.exe.config  
  
    6.  Web.config für die beiden [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] -Anwendungen Berichtsserver und Berichts-Manager  
  
    7.  Machine.config für [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] , wenn Sie die Datei für Berichtsservervorgänge geändert haben  
  
##  <a name="bkmk_install_ssrs"></a>Installieren von SQL Server Reporting Services  
 Installieren Sie eine neue Berichtsserverinstanz im Dateimodus, um sie so konfigurieren zu können, dass Nichtstandardwerte verwendet werden. Verwenden Sie bei der Befehlszeileninstallation das `FilesOnly`-Argument. Wählen Sie im Installations-Assistenten die Option **Server installieren, jedoch nicht konfigurieren**aus.  
  
 Klicken Sie auf einen der folgenden Links, um Anweisungen zum Installieren einer neuen Instanz von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]anzuzeigen.  
  
-   [Installieren Sie SQL Server 2014 über den Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)  
  
-   [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
##  <a name="bkmk_move_database"></a>Verschieben der Berichts Server-Datenbank  
 Die Berichtsserver-Datenbank enthält veröffentlichte Berichte, Modelle, freigegebene Datenquellen, Zeitpläne, Ressourcen, Abonnements und Ordner. Außerdem enthält sie System- und Elementeigenschaften sowie Berechtigungen für den Zugriff auf den Berichtsserverinhalt.  
  
 Wenn die Migration den Wechsel zu einer anderen [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz einschließt, müssen Sie die Berichtsserver-Datenbank in die neue [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz verschieben. Wenn Sie dieselbe [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz verwenden, gehen Sie zum Abschnitt [Verschieben von benutzerdefinierten Assemblys oder Erweiterungen](#bkmk_move_custom).  
  
 Gehen Sie zum Verschieben der Berichtsserver-Datenbank folgendermaßen vor:  
  
1.  Wählen Sie die zu verwendende [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz aus. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erfordert, dass Sie eine der folgenden Versionen zum Hosten der Berichts Server-Datenbank verwenden:  
  
    -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
    -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
    -   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
    -   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
2.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
3.  Wenn `RSExecRole` noch keine Berichtsserver-Datenbank gehostet hat, erstellen Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] in den Systemdatenbanken. Weitere Informationen finden Sie unter [Erstellen der Rolle RSExecRole](../security/create-the-rsexecrole.md).  
  
4.  Befolgen Sie die Anweisungen unter [Verschieben von Berichtsserver-Datenbanken auf einen anderen Computer (einheitlicher SSRS-Modus)](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
 Denken Sie daran, dass die Berichtsserver-Datenbank und die temporäre Datenbank voneinander abhängig sind und gemeinsam verschoben werden müssen. Kopieren Sie die Datenbanken nicht; durch das Kopieren werden nicht alle Sicherheitseinstellungen auf die neue Installation übertragen. Verschieben Sie keine SQL Server-Agent-Aufträge für geplante Berichtsservervorgänge. Der Berichtsserver erstellt diese Aufträge automatisch neu.  
  
##  <a name="bkmk_move_custom"></a>Verschieben benutzerdefinierter Assemblys oder Erweiterungen  
 Wenn die Installation benutzerdefinierte Berichtselemente, Assemblys oder Erweiterungen umfasst, müssen Sie die benutzerdefinierten Komponenten erneut bereitstellen. Wenn Sie keine benutzerdefinierten Komponenten verwenden, fahren Sie mit dem Abschnitt [Konfigurieren des Berichtsservers](#bkmk_configure_reportserver)fort.  
  
 Gehen Sie zum erneuten Bereitstellen der benutzerdefinierten Komponenten wie folgt vor:  
  
1.  Ermitteln Sie, ob die Assemblys unterstützt werden oder neu kompiliert werden müssen:  
  
    -   Für die Version [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] erstellte benutzerdefinierte Authentifizierungserweiterungen müssen neu kompiliert werden.  
  
    -   Benutzerdefinierte Renderingerweiterungen für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] müssen mithilfe des Renderingobjektmodells (Rom) umgeschrieben werden  
  
    -   HTML 3,2-und HTML OWC-Renderer werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und höheren Versionen nicht unterstützt.  
  
    -   Andere benutzerdefinierte Assemblys müssen normalerweise nicht neu kompiliert werden.  
  
2.  Verschieben Sie die Assemblys auf den neuen Berichtsserver und in die Berichts-Manager-Ordner \bin. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]befinden sich die Binärdateien des Berichts Servers an folgendem Speicherort für die Standard [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Instanz:  
  
     `\Program files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\bin`  
  
3.  Ändern Sie die Konfigurationsdateien, indem Sie Einträge für die benutzerdefinierte Komponente hinzufügen. Die Einträge sind von der Art der verwendeten Assembly abhängig. Anweisungen dazu, wo Dateien platziert und Konfigurationseinträge hinzugefügt werden, finden Sie unter folgenden Links:  
  
    1.  [Bereitstellen einer benutzerdefinierten Assembly](../custom-assemblies/deploying-a-custom-assembly.md)  
  
    2.  [Vorgehensweise: Bereitstellen eines benutzerdefinierten Berichtselements](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
    3.  [Bereitstellen von Datenverarbeitungserweiterungen](../extensions/data-processing/deploying-a-data-processing-extension.md)  
  
    4.  [Bereitstellen von Übermittlungserweiterungen](../extensions/delivery-extension/deploying-a-delivery-extension.md)  
  
    5.  [Bereitstellen von Renderingerweiterungen](../extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
    6.  [Implementieren von Sicherheitserweiterungen](../extensions/security-extension/implementing-a-security-extension.md)  
  
##  <a name="bkmk_configure_reportserver"></a>Konfigurieren des Berichts Servers  
 Konfigurieren Sie URLs für den Report Server-Webdienst und den Berichts-Manager, und konfigurieren Sie die Verbindung mit der Berichtsserver-Datenbank.  
  
 Wenn Sie eine Bereitstellung für horizontales Skalieren migrieren, müssen Sie alle Berichtsserverknoten offline schalten und jeden Server einzeln migrieren. Nach der Migration des ersten Berichtsservers und einem erfolgreichen Verbindungsaufbau mit der Berichtsserver-Datenbank, wird die Version der Berichtsserver-Datenbank automatisch auf die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Datenbankversion aktualisiert.  
  
> [!IMPORTANT]  
>  Wenn irgendwelche Berichtsserver in der Bereitstellung für horizontales Skalieren online sind und nicht migriert wurden, könnte die Ausnahme rsInvalidReportServerDatabase auftreten, weil sie ein älteres Schema verwenden, wenn sie mit den aktualisierten verbunden werden.  
  
> [!NOTE]  
>  Wenn der migrierte Berichtsserver als freigegebene Datenbank für eine Bereitstellung für horizontales Skalieren konfiguriert wurde, müssen Sie alle alten Verschlüsselungsschlüssel aus der Tabelle **Keys** in der **ReportServer** -Datenbank vor dem Konfigurieren des Berichtsserverdiensts löschen. Wenn die Schlüssel nicht entfernt werden, versucht der migrierte Berichtsserver, im Bereitstellungsmodus für horizontales Skalieren zu initialisieren. Weitere Informationen finden Sie unter [Hinzufügen und Entfernen von Verschlüsselungsschlüsseln für die Bereitstellung für horizontales Skalieren (SSRS-Konfigurations-Manager)](add-and-remove-encryption-keys-for-scale-out-deployment.md) und [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (SSRS-Konfigurations-Manager)](ssrs-encryption-keys-manage-encryption-keys.md).  
>   
>  Die Schlüssel für horizontales Skalieren können nicht mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager gelöscht werden. Die alten Schlüssel müssen mit SQL Server Management Studio aus der Tabelle **Keys** in der **ReportServer** -Datenbank gelöscht werden. Löschen Sie alle Zeilen in der Keys-Tabelle. Dadurch wird die Tabelle bereinigt und für das ausschließliche Wiederherstellen des symmetrischen Schlüssels vorbereitet, wie in den folgenden Schritten aufgezeigt.  
>   
>  Vor dem Löschen der Schlüssel wird empfohlen, die symmetrischen Verschlüsselungsschlüssel zu sichern. Mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager können Sie den Schlüssel sichern. Öffnen Sie das Configuration Manager öffnen, klicken Sie auf die Registerkarte **Verschlüsselungsschlüssel** und dann auf die Schaltfläche **sichern** . Sie können auch WMI-Befehle zum Sichern des Verschlüsselungsschlüssels schreiben. Weitere Informationen finden Sie unter [BackupEncryptionKey-Methode (WMI MSReportServer_ConfigurationSetting)](../wmi-provider-library-reference/configurationsetting-method-backupencryptionkey.md).  
  
1.  Starten Sie den Reporting Services-Konfigurations-Manager, und stellen Sie eine Verbindung mit der soeben installierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz her. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
2.  Konfigurieren Sie URLs für den Berichtsserver und den Berichts-Manager. Weitere Informationen finden Sie unter [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](configure-a-url-ssrs-configuration-manager.md).  
  
3.  Konfigurieren Sie die Berichtsserver-Datenbank, und wählen Sie dabei die vorhandene Berichtsserver-Datenbank aus der vorherigen Installation aus. Nach der erfolgreichen Konfiguration werden die Berichts Server Dienste neu gestartet, und sobald eine Verbindung mit der Berichts Server-Datenbank hergestellt wurde, wird die Datenbank automatisch auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]aktualisiert. Informationen zum Ausführen des Assistenten zum Ändern der Datenbank, mit dem Sie eine Berichtsserver-Datenbank erstellen oder auswählen, finden Sie unter [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
4.  Stellen Sie die Verschlüsselungsschlüssel wieder her. Dieser Schritt ist erforderlich, um die umkehrbare Verschlüsselung für vorhandene Verbindungszeichenfolgen und Anmeldeinformationen, die sich bereits in der Berichtsserver-Datenbank befinden, zu aktivieren. Weitere Informationen finden Sie unter [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
5.  Wenn Sie den Berichtsserver auf einem neuen Computer installiert haben und die Windows-Firewall verwenden, muss der TCP-Port, auf dem der Berichtsserver lauscht, geöffnet sein. Standardmäßig ist dies der Port 80. Weitere Informationen finden Sie unter [Konfigurieren einer Firewall für den Zugriff auf den Berichts Server](../report-server/configure-a-firewall-for-report-server-access.md).  
  
6.  Wenn Sie den Berichtsserver im einheitlichen Modus lokal verwalten möchten, müssen Sie das Betriebssystem konfigurieren, um die lokale Verwaltung mit dem Berichts-Manager zuzulassen. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="bkmk_copy_custom_config"></a>Kopieren der benutzerdefinierten Konfigurationseinstellungen in die Datei "RSReportServer. config"  
 Wenn Sie die Datei RSReportServer.config oder RSWebApplication.config in der vorherigen Installation geändert haben, sollten Sie dieselben Änderungen in der neuen Datei RSReportServer.config vornehmen. In der folgenden Liste sind einige der Gründe aufgeführt, aus denen Sie die vorherige Konfigurationsdatei möglicherweise geändert haben. Außerdem sind Links aufgeführt, die zu zusätzlichen Informationen zum Konfigurieren derselben Einstellungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]führen.  
  
|Anpassung|Information|  
|-------------------|-----------------|  
|Berichtsserver-E-Mail-Übermittlung mit benutzerdefinierten Einstellungen|[Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung &#40;SSRS-Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) und [e-Mail-Einstellungen-Configuration Manager &#40;SSRS im einheitlichen Modus&#41;](e-mail-settings-reporting-services-native-mode-configuration-manager.md).|  
|Geräteinformationseinstellungen|[Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.config](../customize-rendering-extension-parameters-in-rsreportserver-config.md)|  
|Berichts-Manager für eine Remoteinstanz|[Konfigurieren Sie Berichts-Manager &#40;einheitlichen Modus&#41;](../report-server/configure-web-portal.md)|  
  
##  <a name="bkmk_windowsservice_group"></a>Windows-Dienstgruppe und Sicherheits-ACLs  
 In [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]gibt es eine Dienstgruppe, die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows-Dienstgruppe, die verwendet wird, um Sicherheits-ACLs für alle Registrierungsschlüssel, Dateien und Ordner zu erstellen, die mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installiert werden. Dieser Windows-Gruppenname wird im Format SQLServerReportServerUser $\<*computer_name*>$\<*instance_name*> angezeigt. Diese Gruppe nutzt die beiden Windows-Dienstgruppen in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie über benutzerdefinierte ACLs verfügen, die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] einer der Windows-Gruppen zugeordnet sind, müssen Sie diese ACLs auf die neue Gruppe für die neue Berichts Serverinstanz [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]in anwenden.  
  
##  <a name="bkmk_verify"></a>Überprüfen der Bereitstellung  
  
1.  Testen Sie die virtuellen Verzeichnisse für den Berichtsserver und den Berichts-Manager, indem Sie einen Browser öffnen und die URL-Adresse eingeben. Weitere Informationen finden Sie unter [Überprüfen einer Installation von Reporting Services](verify-a-reporting-services-installation.md).  
  
2.  Testen Sie Berichte, und überprüfen Sie, ob sie die erwarteten Daten enthalten. Überprüfen Sie, ob in den Datenquelleninformationen noch immer die Datenquellen-Verbindungsinformationen angegeben sind. Der Berichtsserver verwendet beim Verarbeiten und Rendern von Berichten das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Berichtsobjektmodell. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]- oder [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]-Konstrukte werden jedoch nicht durch neue Report Definition Language-Elemente ersetzt. Weitere Informationen zu vorhandenen Berichten, die auf einem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichtsserver ausgeführt werden, finden Sie unter [Aktualisieren von Berichten](upgrade-reports.md).  
  
##  <a name="bkmk_remove_unused"></a>Entfernen nicht verwendeter Programme und Dateien  
 Wenn Sie Ihren Berichts Server erfolgreich zu einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz migriert haben, können Sie die folgenden Schritte ausführen, um nicht mehr benötigte Programme und Dateien zu entfernen.  
  
1.  Deinstallieren Sie die vorherige Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , wenn diese nicht mehr benötigt wird. Mit diesem Schritt werden die folgenden Elemente nicht gelöscht, aber Sie können sie manuell entfernen, wenn Sie sie nicht mehr benötigen:  
  
    -   Die alte Berichtsserver-Datenbank  
  
    -   RSExec-Rolle  
  
    -   Berichtsserver-Dienstkonten  
  
    -   Anwendungspool für den Berichtsserver-Webdienst  
  
    -   Virtuelle Verzeichnisse für den Berichts-Manager und den Berichtsserver  
  
    -   Berichtsserver-Protokolldateien  
  
2.  Entfernen Sie IIS, wenn das Programm auf diesem Computer nicht mehr benötigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren einer Reporting Services-Installation &#40;SharePoint-Modus&#41;](migrate-a-reporting-services-installation-sharepoint-mode.md)   
 [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../report-server/report-server-database-ssrs-native-mode.md)   
 [Aktualisieren und Migrieren Reporting Services](upgrade-and-migrate-reporting-services.md)   
 [Reporting Services Abwärtskompatibilität](../reporting-services-backward-compatibility.md)   
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
