---
title: Konfigurieren von Power Pivot-Dienst Konten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 76a85cd0-af93-40c9-9adf-9eb0f80b30c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: d4053c7a15d0131773b72f347caab7cbc42d6044
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547532"
---
# <a name="configure-powerpivot-service-accounts"></a>Konfigurieren von PowerPivot-Dienstkonten
  Zu einer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installation gehören zwei Dienste, die Servervorgänge unterstützen. Der **SQL Server Analysis Services (Power Pivot)** -Dienst ist ein Windows-Dienst, der die Power Pivot-Datenverarbeitung und-Abfrage Unterstützung auf einem Anwendungs Server bereitstellt. Das Anmeldekonto für diesen Dienst wird immer während des SQL Server-Setups angegeben, wenn Sie Analysis Services im integrierten SharePoint-Modus installieren.  
  
 Ein zweites Konto muss für die PowerPivot-Dienstanwendung angegeben werden, einen freigegebenen Webdienst, der unter einer Anwendungspoolidentität in einer SharePoint-Farm ausgeführt wird. Dieses Konto wird angegeben, wenn Sie mit dem PowerPivot-Konfigurationstool oder PowerShell eine [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installation konfigurieren.  
  
 Jeder Dienst sollte unter einem dedizierten Konto ausgeführt werden, damit Sie in der Farm Verbindungen überwachen oder das Kerberos-Authentifizierungsprotokoll aktivieren können.  
  
 Nach dem Festlegen der Dienstkonten müssen alle Änderungen an den Konten über die SharePoint-Zentraladministration vorgenommen werden. Wenn Sie alternative Tools (z. B. die Dienste-Konsolenanwendung, IIS-Manager oder SQL Server-Konfigurations-Manager) verwenden, werden Berechtigungen für den Datenbankzugriff in der Farm oder für den lokalen Dateizugriff auf dem physischen Server nicht aktualisiert.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Aktualisieren eines abgelaufenen Kennworts für eine Instanz von SQL Server Analysis Services (PowerPivot)](#bkmk_passwordssas)  
  
 [Aktualisieren eines abgelaufenen Kennworts für die PowerPivot-Dienstanwendung](configure-power-pivot-service-accounts.md#bkmk_passwordapp)  
  
 [Das Konto ändern, unter dem der jeweilige Dienst ausgeführt wird](#bkmk_newacct)  
  
 [Erstellen oder Ändern des Anwendungspools für eine PowerPivot-Dienstanwendung](#bkmk_appPool)  
  
 [Kontoanforderungen und Berechtigungen](#requirements)  
  
 [Problembehandlung: Manuelles Gewähren von Administratorberechtigungen](#updatemanually)  
  
 [Problembehandlung: Beheben von HTTP 503-Fehlern aufgrund abgelaufener Kennwörter für die zentrale Verwaltung oder den SharePoint Foundation-Webanwendungsdienst](#expired)  
  
##  <a name="update-an-expired-password-for-sql-server-analysis-services-powerpivot-instance"></a><a name="bkmk_passwordssas"></a>Aktualisieren eines abgelaufenen Kennworts für SQL Server Analysis Services (Power Pivot)-Instanz  
  
1.  Zeigen Sie auf „Start“, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Dienste**. Doppelklicken Sie auf **SQL Server Analysis Services (Power Pivot)**. Klicken Sie auf **Anmelden**, und geben Sie dann ein neues Kennwort für das Konto ein.  
  
2.  Klicken Sie in der Zentraladministration im Abschnitt „Sicherheit“ auf **Verwaltete Konten konfigurieren**.  
  
3.  Klicken Sie auf **Bearbeiten** , um ein bestimmtes Konto zu ändern.  
  
4.  Wählen Sie **Kennwort jetzt ändern**aus.  
  
5.  Wählen Sie **Kontokennwort auf neuen Wert festlegen**aus. Alle Dienste, die unter dem verwalteten Konto ausgeführt werden, verwenden die aktualisierten Anmeldeinformationen.  
  
##  <a name="update-an-expired-password-for-the-powerpivot-service-application"></a><a name="bkmk_passwordapp"></a>Aktualisieren eines abgelaufenen Kennworts für die Power Pivot-Dienst Anwendung  
  
1.  Klicken Sie in der Zentraladministration im Abschnitt „Sicherheit“ auf **Verwaltete Konten konfigurieren**.  
  
2.  Klicken Sie auf **Bearbeiten** , um ein bestimmtes Konto zu ändern.  
  
3.  Wählen Sie **Kennwort jetzt ändern**aus.  
  
4.  Wählen Sie **Kontokennwort auf neuen Wert festlegen**aus. Alle Dienste, die unter dem verwalteten Konto ausgeführt werden, verwenden die aktualisierten Anmeldeinformationen.  
  
##  <a name="change-the-account-under-which-each-service-runs"></a><a name="bkmk_newacct"></a>Ändern des Kontos, unter dem der jeweilige Dienst ausgeführt wird  
  
1.  Klicken Sie in der Zentraladministration im Abschnitt „Sicherheit“ auf **Dienstkonten konfigurieren**.  
  
2.  Wählen Sie **Windows-Dienst - SQL Server Analysis Services** aus, um das Analysis Services-Dienstkonto zu ändern.  
  
3.  Wählen Sie unter **Select an account for this service**(Ein Konto für diesen Dienst auswählen) ein vorhandenes verwaltetes Konto aus, oder erstellen Sie ein neues. Das Konto muss ein Domänenbenutzerkonto sein.  
  
4.  Wählen Sie **Dienst Anwendungs Pool-SharePoint-Webdienst System** aus, um die Anwendungs Pool Identität der Power Pivot-Standard Dienst Anwendung zu ändern. Je nach Konfiguration der Installation wird der Dienst möglicherweise unter einem vorhandenen Dienstanwendungspool ausgeführt, der für SharePoint Services erstellt wurde. Standardmäßig wird der Dienst vom Power Pivot-Konfigurations Tool als Power Pivot- **Standard Dienst Anwendung (Power Pivot-Dienst Anwendung)** registriert.  
  
     Wenn der Dienst von einem SharePoint-Administrator manuell konfiguriert wurde, verfügt der Dienst sehr wahrscheinlich über einen eigenen Dienstanwendungspool.  
  
5.  Wählen Sie unter **Select an account for this service**(Ein Konto für diesen Dienst auswählen) ein vorhandenes verwaltetes Konto aus, oder erstellen Sie ein neues. Das Konto muss ein Domänenbenutzerkonto sein.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="create-or-change-the-application-pool-for-a-powerpivot-service-application"></a><a name="bkmk_appPool"></a>Erstellen oder Ändern des Anwendungs Pools für eine Power Pivot-Dienst Anwendung  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Wählen Sie die PowerPivot-Dienstanwendung aus, aber klicken Sie nicht darauf. Wenn Sie auf einen Anwendungsnamen klicken, wird das PowerPivot-Management-Dashboard geöffnet. Dort wird aber kein Link zur Eigenschaftenseite bereitgestellt, auf dem der Anwendungspool angegeben ist.  Sie können auf das Leerzeichen in der Zeile oder auf den Typnamen klicken, um die PowerPivot-Dienstanwendung auszuwählen.  
  
3.  Klicken Sie im Menüband auf **Eigenschaften** .  
  
4.  Wählen Sie **Einen neuen Anwendungspool erstellen**aus. Geben Sie einen Namen für den Anwendungspool und ein verwaltetes Konto für die Identität des Anwendungspools an.  
  
##  <a name="account-requirements-and-permissions"></a><a name="requirements"></a>Kontoanforderungen und-Berechtigungen  
 Wenn Sie eine PowerPivot für SharePoint-Bereitstellung planen, sollten Sie die folgenden Dienstkonten vorsehen.  
  
-   Analysis Services-Dienstkonto. Analysis Services verarbeitet PowerPivot-Abfragen und -Datenaktualisierungsaufträge in der Farm. Dieses Konto wird immer während des SQL Server-Setups angegeben, wenn Sie PowerPivot für SharePoint installieren.  
  
-   PowerPivot-Dienstanwendungspool. Eine PowerPivot-Dienstanwendung ist mit einem PowerPivot-Systemdienst verbunden, der SharePoint-Integration und -Infrastruktur für die PowerPivot-Abfrageverarbeitung in einer Farm bereitstellt. Der Anwendungspool, den Sie für eine PowerPivot-Dienstanwendung angeben, ist die Dienstidentität des PowerPivot-Systemdiensts. Eine Farm kann mehrere PowerPivot-Dienstanwendungen enthalten. Jede erstellte Anwendung sollte in einem eigenen Anwendungspool ausgeführt werden.  
  
#### <a name="analysis-services-service-account"></a>Analysis Services-Dienstkonto  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Bereitstellungsanforderung|Dieses Konto muss während SQL Server-Setups auf der **Seite Analysis Services-Konfiguration** des Installations-Assistenten (oder `ASSVCACCOUNT` im Installationsparameter in einem Befehlszeilen Setup) angegeben werden.<br /><br /> Sie können den Benutzernamen oder das Kennwort mit der Zentraladministration, PowerShell oder dem PowerPivot-Konfigurationstool ändern. Die Verwendung anderer Tools zum Ändern von Konten und Kennwörtern wird nicht unterstützt.|  
|Domänenbenutzerkonto-Anforderung|Bei diesem Konto muss es sich um ein Windows-Domänenbenutzerkonto handeln. Integrierte Computerkonten (z. B. Netzwerkdienst oder Lokaler Dienst) sind nicht zulässig. SQL Server-Setup erzwingt die Domänenbenutzerkonto-Anforderung, indem die Installation blockiert wird, sobald ein Computerkonto angegeben wird.|  
|Berechtigungsanforderungen|Dieses Konto muss ein Mitglied der Sicherheitsgruppe SQLServerMSASUser $ \<server> $PowerPivot und WSS_WPG Sicherheitsgruppen auf dem lokalen Computer sein. Diese Berechtigungen sollten automatisch gewährt werden. Weitere Informationen zum Überprüfen oder erteilen von Berechtigungen finden Sie unter [Manuelles gewähren von Administrator Berechtigungen für das Power Pivot-Dienst Konto](#updatemanually) in diesem Thema und [Erstkonfiguration &#40;PowerPivot für SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md).|  
|Anforderungen für horizontales Skalieren|Wenn Sie mehrere PowerPivot für SharePoint-Serverinstanzen in einer Farm installieren, müssen alle Analysis Services-Serverinstanzen unter dem gleichen Domänenbenutzerkonto ausgeführt werden. Wenn Sie z.B. die erste [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] -Instanz für die Ausführung als Contoso\ssas-srv01 konfigurieren, müssen alle zusätzlichen [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] -Instanzen, die Sie danach in der gleichen Farm bereitstellen, auch als Contoso\ssas-srv01 (bzw. unter dem entsprechenden aktuellen Konto) ausgeführt werden.<br /><br /> Indem alle Dienstinstanzen für die Ausführung unter dem gleichen Konto konfiguriert werden, hat der PowerPivot-Systemdienst die Möglichkeit, Abfrageverarbeitungs- oder Datenaktualisierungsaufträge jeder beliebigen Analysis Services-Dienstinstanz in der Farm zuzuordnen. Außerdem wird die Verwendung des Features Verwaltetes Konto in der Zentraladministration für Analysis Services-Serverinstanzen ermöglicht. Indem Sie das gleiche Konto für alle [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] -Instanzen verwenden, müssen Sie das Konto oder Kennwort nur einmal ändern, dann werden alle Dienstinstanzen, die die Anmeldeinformationen verwenden, automatisch aktualisiert.<br /><br /> In SQL Server-Setup wird die Verwendung eines identischen Kontos erzwungen. In einer Bereitstellung für horizontales Skalieren, in der bereits eine Instanz von PowerPivot für SharePoint in einer SharePoint-Farm installiert ist, wird die Neuinstallation von Setup blockiert, wenn sich das von Ihnen angegebene [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Konto von dem bereits in der Farm verwendeten Konto unterscheidet.|  
  
#### <a name="powerpivot-service-application-pool"></a>PowerPivot-Dienstanwendungspool  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Bereitstellungsanforderung|Beim PowerPivot-Systemdienst handelt es sich um eine in der Farm freigegebene Ressource, die verfügbar wird, wenn Sie eine Dienstanwendung erstellen. Der Dienstanwendungspool muss bei der Erstellung der Dienstanwendung angegeben werden. Er kann auf zwei Arten angegeben werden: mithilfe des PowerPivot-Konfigurationstools oder durch PowerShell-Befehle.<br /><br /> Sie haben die Anwendungspoolidentität möglicherweise so konfiguriert, dass sie unter einem eindeutigen Konto ausgeführt wird. Wenn dies nicht der Fall ist, sollten Sie es in Erwägung ziehen, es jetzt unter einem anderen Konto auszuführen.|  
|Domänenbenutzerkonto-Anforderung|Die Anwendungspoolidentität muss ein Windows-Domänenbenutzerkonto sein. Integrierte Computerkonten (z. B. Netzwerkdienst oder Lokaler Dienst) sind nicht zulässig.|  
|Berechtigungsanforderungen|Dieses Konto benötigt keine lokalen Systemadministratorberechtigungen auf dem Computer. Dieses Konto muss Analysis Services-Systemadministratorberechtigungen auf dem lokalen [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] -Computer aufweisen, der auf dem gleichen Computer installiert ist. Diese Berechtigungen werden automatisch von SQL Server-Setup oder beim Festlegen oder Ändern der Anwendungspoolidentität in der Zentraladministration gewährt.<br /><br /> Administratorberechtigungen sind erforderlich, damit das Weiterleiten von Abfragen an den [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Computer erfolgen kann. Sie sind auch zum Überwachen des Zustands, zum Schließen inaktiver Sitzungen und zum Lauschen auf Ablaufverfolgungsereignisse erforderlich.<br /><br /> Das Konto muss über Verbindungs-, Lese- und Schreibberechtigungen für die PowerPivot-Dienstanwendungsdatenbank verfügen. Diese Berechtigungen werden automatisch gewährt, wenn die Anwendung erstellt wird, und automatisch aktualisiert, wenn Sie Konten oder Kennwörter in der Zentraladministration ändern.<br /><br /> Die PowerPivot-Dienstanwendung überprüft, ob ein SharePoint-Benutzer berechtigt ist, Daten vor dem Abrufen der Datei anzuzeigen, aber sie nimmt die Identität des Benutzers nicht an. Es gibt keine Berechtigungsanforderungen für Identitätswechsel.|  
|Anforderungen für horizontales Skalieren|Keine.|  
  
##  <a name="troubleshooting-grant-administrative-permissions-manually"></a><a name="updatemanually"></a>Problembehandlung: Manuelles erteilen von Administrator Berechtigungen  
 Administratorberechtigungen werden nicht aktualisiert, wenn die Person, die die Anmeldeinformationen aktualisiert, kein lokaler Administrator auf dem Computer ist. Wenn dies auftritt, können Sie Administratorberechtigungen manuell gewähren. Die einfachste Möglichkeit hierzu besteht darin, den PowerPivot-Konfigurationszeitgeberauftrag in der Zentraladministration auszuführen. Mit diesem Ansatz können Sie Berechtigungen für alle PowerPivot-Server in der Farm zurücksetzen. Beachten Sie, dass dieser Ansatz nur funktioniert, wenn der SharePoint-Zeitgeberauftrag sowohl als Farmadministrator als auch als lokaler Administrator auf dem Computer ausgeführt wird.  
  
1.  Klicken Sie in Monitoring auf **Auftragsdefinitionen überprüfen**.  
  
2.  Wählen Sie Zeit Geber **Auftrag für Power Pivot-Konfiguration**aus.  
  
3.  Klicken Sie auf **jetzt ausführen**.  
  
 Als letztes Mittel können Sie die richtigen Berechtigungen sicherstellen, indem Sie Analysis Services System Administrator Berechtigungen für die Power Pivot-Dienst Anwendung gewähren und dann ausdrücklich die Dienst Anwendungs Identität der Windows-Sicherheitsgruppe SQLServerMSASUser $ $PowerPivot hinzufügen \<servername> . Sie müssen diese Schritte für jede Analysis Services-Instanz wiederholen, die mit der SharePoint-Farm integriert ist.  
  
 Sie müssen lokaler Administrator sein, um Windows-Sicherheitsgruppen zu aktualisieren.  
  
1.  Stellen Sie in SQL Server Management Studio eine Verbindung mit der Analysis Services Instanz als \<server name> \powerpivother.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Servernamen, und wählen Sie **Eigenschaften**aus.  
  
3.  Klicken Sie auf **Sicherheit**.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
5.  Geben Sie den Namen des Kontos ein, das für den Power Pivot-Dienst Anwendungs Pool verwendet wird, und klicken Sie dann auf **OK**.  
  
6.  Klicken Sie unter „Verwaltung“ auf **Computerverwaltung**.  
  
7.  Öffnen Sie **Lokale Benutzer und Gruppen**.  
  
8.  Öffnen Sie **Gruppen**.  
  
9. Doppelklicken Sie auf SQLServerMSASUser $ \<servername> $PowerPivot.  
  
10. Klicken Sie auf **Hinzufügen**.  
  
11. Geben Sie den Namen des Kontos ein, das für den Power Pivot-Dienst Anwendungs Pool verwendet wird, und klicken Sie dann auf **OK**.  
  
##  <a name="troubleshooting-resolve-http-503-errors-due-to-expired-passwords-for-central-administration-or-the-sharepoint-foundation-web-application-service"></a><a name="expired"></a>Problembehandlung: Beheben von HTTP 503-Fehlern aufgrund abgelaufener Kenn Wörter für die zentral Administration oder den SharePoint Foundation-Webanwendungs Dienst  
 Wenn der zentrale Verwaltungsdienst oder der SharePoint Foundation-Webanwendungsdienst aufgrund der Rücksetzung eines Kontos oder des Ablaufs eines Kennworts aufhört zu arbeiten, erhalten Sie die Fehlermeldung HTTP 503 "Dienst nicht verfügbar", wenn Sie versuchen, die zentrale SharePoint-Verwaltung oder eine SharePoint-Website zu öffnen. Führen Sie folgende Schritte aus, um den Server online zurückzubringen. Sobald die zentrale Verwaltung verfügbar ist, können Sie damit fortfahren, abgelaufene Kontoinformationen zu aktualisieren.  
  
1.  Klicken Sie in der Verwaltung auf **Internetinformationsdienste-Manager**.  
  
2.  Wenn die Identität der Website oder Zentraladministrationsanwendungspools ein Domänenbenutzerkonto ist, das ein abgelaufenes Kennwort hat, gehen Sie wie folgt vor:  
  
    1.  Klicken Sie mit der rechten Maustaste auf den Namen des Anwendungspools, und wählen Sie **Erweiterte Einstellungen**aus.  
  
    2.  Wählen Sie **Identität** aus, und klicken Sie auf... , um das Dialogfeld Anwendungs Pool Identität zu öffnen.  
  
    3.  Klicken Sie auf **Festlegen**.  
  
    4.  Geben Sie den Benutzernamen und das Kennwort ein.  
  
3.  Führen Sie IISRESET aus. Öffnen Sie hierzu eine Administratoreingabeaufforderung, und geben Sie `iisreset` beim Befehl ein.  
  
4.  Wählen Sie in der zentralen SharePoint-Verwaltung unter „Sicherheit“ die Option **Verwaltete Konten konfigurieren**aus.  
  
5.  Klicken Sie auf **Bearbeiten** , um die Informationen des verwalteten Kontos mit dem abgelaufenen Kennwort zu aktualisieren.  
  
6.  Wählen Sie **Kennwort jetzt ändern**aus.  
  
7.  Klicken Sie auf **Vorhandenes Kennwort verwenden**.  
  
8.  Geben Sie das Kennwort ein, und klicken Sie dann auf **OK**.  
  
 Wenn Reporting Services installiert ist, aktualisieren Sie Kennwörter für den Berichtsserver und die Verbindung zur Berichtsserver-Datenbank mithilfe des Reporting Services-Konfigurations-Managers. Weitere Informationen finden Sie unter [Konfiguration und Verwaltung eines Berichtsservers &#40;SharePoint-Modus von Reporting Services&#41;](../../reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten oder Abbrechen eines PowerPivot für SharePoint Servers](start-or-stop-a-power-pivot-for-sharepoint-server.md)   
 [Konfigurieren Sie das unbeaufsichtigte Daten Aktualisierungs Konto für Power Pivot &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
  
